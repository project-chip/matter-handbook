---
label: API Reference
order: 100
---

This document provides a high-level mapping of the REST API endpoints and corresponding Web UI locations for the key schemas defined in the Matter Distributed Compliance Ledger (DCL) specification.

All REST API queries are based on the root URL: `https://on.dcl.csa-iot.org`

Refer to the [Official REST API Documentation](https://zigbee-alliance.github.io/distributed-compliance-ledger/) for detailed response structures.

---

## Vendor Schema
**Description:** Contains details about the companies registered on the ledger, including their Vendor ID (VID), legal name, and landing page URLs.

### REST API
*   **Query All Vendors:** `/dcl/vendorinfo/vendors`
    *   **Returns:** A list of vendor records.
    *   **Pagination:** **Required**.

*   **Query by VID:** `/dcl/vendorinfo/vendors/{vid}`
    *   **Returns:** Details for a specific vendor.

### Web Interface
*   **Location:** https://webui.dcl.csa-iot.org/vendors

---

## Product Attestation Authority and Intermediate Certificate Schema
**Description:** The root of trust for Matter device attestation. Contains the approved root certificates (PAA).

### REST API
*   **Query All Root Certificates:** `/dcl/pki/root-certificates`
    *   **Returns:** The list of all approved PAA certificates + Alliance CD signing certificates. Returns Subject and SubjectKeyID only, certificates need to be queried individually.
    *   **Pagination:** Not explicitly paginated in current responses (returns full list), but client should be robust to future pagination.

*   **Query by Subject & SubjectKeyID:** `/dcl/pki/certificates/{subject}/{subjectKeyId}`
    *   **Returns:** A specific certificate.
    *   **Pagination:** Not applicable.
    * NOTE - subject needs to be percent formatted, which is a transformation of the data returned from the base root-certificates request.

### Web Interface
*   **Location:** https://webui.dcl.csa-iot.org/pki/root-certificates


---

## Operational Trust Anchors Schema
**Description:** Provides the list of Operational Root CA Certificates (RCAC) and Operational Intermediate CA Certificates (ICAC).


### Web Interface
*   **Location:** https://webui.dcl.csa-iot.org/pki (Select **NOC Certificates** tab)

---

## DeviceModel Schema
**Description:** Defines the base product models associated with a vendor. This includes immutable hardware details and shared product metadata.

### REST API
*   **Query All Models:** `/dcl/model/models`
    *   **Returns:** A global list of all device models.
    *   **Pagination:** **Required**.

*   **Query by VID:** `/dcl/model/models/{vid}`
    *   **Returns:** All products associated with a specific Vendor ID. Product response contains info about PID, name and part number.
    *   **Pagination:** **Required**.
    * NOTE - `vid` (Vendor ID) is a decimal value

*   **Query by VID & PID:** `/dcl/model/models/{vid}/{pid}`
    *   **Returns:** Details for a specific product.
    *   **Pagination:** Not applicable.
    * NOTE - `vid` (Vendor ID) and `pid` (Product ID) are decimal values


### Web Interface
*   **Location:** https://webui.dcl.csa-iot.org/models

---

## DeviceSoftwareVersionModel Schema
**Description:** Detailed information about specific software versions for a device model (release notes, OTA URLs).

### REST API
*   **Query by VID & PID:** `/dcl/model/versions/{vid}/{pid}`
    *   **Returns:** A list of all software versions for a specific device model.
    *   **Pagination:** Not applicable (returns complete list in one object).
    * NOTE: Querying by VID alone (`/dcl/model/versions/{vid}`) is NOT supported (Returns 501).

*   **Query by VID, PID & Software Version:** `/dcl/model/versions/{vid}/{pid}/{softwareVersion}`
    *   **Returns:** The full details for a specific software version.
    *   **Pagination:** Not applicable.
    * NOTE - `vid` (Vendor ID), `pid` (Product ID) and `softwareVersion` are decimal values

### Web Interface
*   **Location:** Accessed via the **Models** view details page.

---

## DeviceSoftwareCompliance Schema
**Description:** Tracks the certification status of a specific software version ("Certified", "Provisional", "Revoked").

### REST API
*   **Query All Compliance Records:** `/dcl/compliance/compliance-info`
    *   **Returns:** A list of all compliance records.
    *   **Pagination:** **Required**.

*   **Query by Specific Version:** `/dcl/compliance/compliance-info/{vid}/{pid}/{softwareVersion}/{certificationType}`
    *   **Returns:** The compliance status for a specific software version.
    *   **Pagination:** Not applicable.
    * NOTE - Intermediate queries by VID or VID/PID are NOT supported (Returns 501).
    * NOTE - `vid` (Vendor ID), `pid` (Product ID) and `softwareVersion` are decimal values
    * NOTE - certification type is "matter" (`/dcl/compliance/compliance-info/{vid}/{pid}/{softwareVersion}/matter`)

### Web Interface
*   **Location:** Accessed via the **Models** view details page.

---

## Device Attestation PKI Revocation Distribution Points Schema
**Description:** Provides the URLs where Certificate Revocation Lists (CRLs) can be downloaded for PAAs and PAIs.

### REST API
Refer to the [Official REST API Documentation](https://zigbee-alliance.github.io/distributed-compliance-ledger/) for detailed response structures.

*   **Query All Revocation Points:** `/dcl/pki/revocation-points`
    *   **Returns:** A list of all registered CRL distribution points.
    *   **Pagination:** **Required**.

*   **Query by Issuer Subject Key ID:** `/dcl/pki/revocation-points/{issuerSubjectKeyID}`
    *   **Returns:** The distribution point details for a specific Issuer (PAA/PAI).

### Web Interface
*   **Location:** https://webui.dcl.csa-iot.org/pki/revocation-points

---

## Additional Schemas & Indices

This section describes other schemas and indices available in the DCL. Refer to the [Official REST API Documentation](https://zigbee-alliance.github.io/distributed-compliance-ledger/) for full details on endpoints and structures.

### CertifiedModel Index
**Description:** A simplified index or "view" that allows for quick verification of certification status without retrieving the full compliance record.

#### REST API
*   **Query All Certified Models:** `/dcl/compliance/certified-models`
    *   **Returns:** A list of all models that currently hold a valid certification.
    *   **Pagination:** **Required**.

*   **Query by VID, PID & Software Version:** `/dcl/compliance/certified-models/{vid}/{pid}/{softwareVersion}/{certificationType}`
    *   **Returns:** A boolean-like record indicating if the specific version is certified. Also contains info about associated softwareVersion, certificationType, vid and pid

#### Web Interface
*   **Location:** https://webui.dcl.csa-iot.org/compliance

### Auth Endpoint
**Description:** Manages DCL accounts, roles (Vendor, Trustee, NodeAdmin), and permissions.
*   **Key Endpoint:** `/dcl/auth/accounts`
*   **Web Interface:**https://webui.dcl.csa-iot.org/accounts

### DclUpgrade Schema
**Description:** Manages the proposal and approval process for software upgrades to the DCL network itself.
*   **Key Endpoint:** `/dcl/dclupgrade/proposed-upgrades`
*   **Web Interface:**https://webui.dcl.csa-iot.org/upgrades

### Validator Schema
**Description:** Contains information about the Validator Nodes that maintain the DCL network consensus.
*   **Key Endpoint:** `/dcl/validator/nodes`
*   **Web Interface:**https://webui.dcl.csa-iot.org/validators
