---
label: API Reference
order: 100
---

This document provides a high-level overview of the REST API endpoints and corresponding Web UI locations for the key schemas defined in the Matter Distributed Compliance Ledger (DCL) specification.

All REST API queries are based on the root URL: `https://on.dcl.csa-iot.org`

---

## 1. Vendor Schema
**Description:** Contains details about the companies registered on the ledger, including their Vendor ID (VID), legal name, and landing page URLs.

### REST API
*   **Query All Vendors:** `/dcl/vendorinfo/vendors`
    *   **Returns:** A list of vendor records.
    *   **JSON Response Structure:**
        ```json
        {
          "vendorInfo": [ { "vendorID": 1, ... } ],
          "pagination": { "next_key": "...", "total": "..." }
        }
        ```
    *   **Pagination:** **Required**.

*   **Query by VID:** `/dcl/vendorinfo/vendors/{vid}`
    *   **Returns:** Details for a specific vendor.
    *   **JSON Response Structure:**
        ```json
        {
          "vendorInfo": { "vendorID": 1, ... }
        }
        ```

### Web Interface
*   **Location:** https://webui.dcl.csa-iot.org/vendors

---

## 2. DeviceModel Schema
**Description:** Defines the base product models associated with a vendor. This includes immutable hardware details and shared product metadata.

### REST API
*   **Query All Models:** `/dcl/model/models`
    *   **Returns:** A global list of all device models.
    *   **JSON Response Structure:**
        ```json
        {
          "model": [ { "vid": 1, "pid": 1, ... } ],
          "pagination": { "next_key": "...", "total": "..." }
        }
        ```
    *   **Pagination:** **Required**.

*   **Query by VID:** `/dcl/model/models/{vid}`
    *   **Returns:** All models associated with a specific Vendor ID.
    *   **JSON Response Structure:**
        ```json
        {
          "vendorProducts": { "vendorID": 1, "products": [ ... ] }
        }
        ```
        *(Note: The key here is `vendorProducts`, distinct from the global query)*

*   **Query by VID & PID:** `/dcl/model/models/{vid}/{pid}`
    *   **Returns:** Details for a specific product.
    *   **JSON Response Structure:**
        ```json
        {
          "model": { "vid": 1, "pid": 1, ... }
        }
        ```

### Web Interface
*   **Location:** https://webui.dcl.csa-iot.org/models

---

## 3. DeviceSoftwareVersionModel Schema
**Description:** Detailed information about specific software versions for a device model (release notes, OTA URLs).

### REST API
*   **Query by VID & PID:** `/dcl/model/versions/{vid}/{pid}`
    *   **Returns:** A list of all software versions for a specific device model.
    *   **JSON Response Structure:**
        ```json
        {
          "modelVersions": {
            "vid": 1,
            "pid": 1,
            "softwareVersions": [ 1, 2, 3 ]
          }
        }
        ```
    *   *Note: Querying by VID alone (`/dcl/model/versions/{vid}`) is NOT supported (Returns 501).*

*   **Query by VID, PID & Software Version:** `/dcl/model/versions/{vid}/{pid}/{softwareVersion}`
    *   **Returns:** The full details for a specific software version.
    *   **JSON Response Structure:**
        ```json
        {
          "modelVersion": { "vid": 1, "pid": 1, "softwareVersion": 1, ... }
        }
        ```

### Web Interface
*   **Location:** Accessed via the **Models** view details page.

---

## 4. DeviceSoftwareCompliance Schema
**Description:** Tracks the certification status of a specific software version ("Certified", "Provisional", "Revoked").

### REST API
*   **Query All Compliance Records:** `/dcl/compliance/compliance-info`
    *   **Returns:** A list of all compliance records.
    *   **JSON Response Structure:**
        ```json
        {
          "complianceInfo": [ { "vid": 1, ... } ],
          "pagination": { "next_key": "...", "total": "..." }
        }
        ```
    *   **Pagination:** **Required**.

*   **Query by Specific Version:** `/dcl/compliance/compliance-info/{vid}/{pid}/{softwareVersion}/{certificationType}`
    *   **Returns:** The compliance status for a specific software version.
    *   **JSON Response Structure:**
        ```json
        {
          "complianceInfo": { "softwareVersionCertificationStatus": 2, ... }
        }
        ```
    *   *Note: Intermediate queries by VID or VID/PID are NOT supported (Returns 501).*

### Web Interface
*   **Location:** Accessed via the **Models** view details page.

---

## 5. CertifiedModel Schema
**Description:** A simplified index or "view" for quick verification of certification status.

### REST API
*   **Query All Certified Models:** `/dcl/compliance/certified-models`
    *   **Returns:** A list of all models that currently hold a valid certification.
    *   **JSON Response Structure:**
        ```json
        {
          "certifiedModel": [ { "value": true, ... } ],
          "pagination": { "next_key": "...", "total": "..." }
        }
        ```
    *   **Pagination:** **Required**.

*   **Query by Specific Version:** `/dcl/compliance/certified-models/{vid}/{pid}/{softwareVersion}/{certificationType}`
    *   **Returns:** A boolean-like record indicating certification.
    *   **JSON Response Structure:**
        ```json
        {
          "certifiedModel": { "value": true, ... }
        }
        ```
    *   *Note: Intermediate queries by VID or VID/PID are NOT supported (Returns 501).*

### Web Interface
*   **Location:** https://webui.dcl.csa-iot.org/compliance

---

## 6. Product Attestation Authority and Intermediate Certificate Schema
**Description:** The root of trust for Matter device attestation (PAA Certificates).

### REST API
*   **Query All Root Certificates:** `/dcl/pki/root-certificates`
    *   **Returns:** The list of all approved PAA certificates.
    *   **JSON Response Structure:**
        ```json
        {
          "approvedRootCertificates": {
            "certs": [ { "subject": "...", ... } ]
          }
        }
        ```

*   **Query by Subject & SubjectKeyID:** `/dcl/pki/certificates/{subject}/{subjectKeyId}`
    *   **Returns:** A specific certificate.

### Web Interface
*   **Location:** https://webui.dcl.csa-iot.org/pki/root-certificates

---

## 7. Device Attestation PKI Revocation Distribution Points Schema
**Description:** Provides the URLs where Certificate Revocation Lists (CRLs) can be downloaded.

### REST API
*   **Query All Revocation Points:** `/dcl/pki/revocation-points`
    *   **Returns:** A list of all registered CRL distribution points.
    *   **JSON Response Structure:**
        ```json
        {
          "pkiRevocationDistributionPoint": [ { "dataUrl": "...", ... } ],
          "pagination": { "next_key": "...", "total": "..." }
        }
        ```
    *   **Pagination:** **Required**.

*   **Query by Issuer Subject Key ID:** `/dcl/pki/revocation-points/{issuerSubjectKeyID}`
    *   **Returns:** The distribution point details for a specific Issuer (PAA/PAI).

### Web Interface
*   **Location:** https://webui.dcl.csa-iot.org/pki/revocation-points
