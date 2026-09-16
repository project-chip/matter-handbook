#

![|700](/static/logos/matter-spec-logo.svg)

The Matter specification is the technical foundation of the Matter protocol. There are normally two minor releases per year, in Spring and Fall, with optional follow-up patch releases between the minor releases.

## Latest Release

!!!base :icon-tag: Version 1.6.0 (June 2026)
All specification documents are available for download from the Alliance website.

[!button variant="base" icon="download" text="Download Specification"](https://csa-iot.org/developer-resource/specifications-download-request/)
!!!

### What's New in 1.6

Matter 1.6 focuses on device setup, device sharing across ecosystems, context-aware thermostat control, and clearer device status information:

- :icon-device-mobile: **NFC-based commissioning** - The full commissioning exchange can take place over bidirectional Near Field Communication (NFC), even before a device is fully powered. This provides an alternative to Bluetooth Low Energy (BLE) commissioning for devices such as light bulbs and in-wall switches.
- :icon-people: **Joint Fabric** - Multiple user-authorized controllers can co-administer one shared Matter fabric through a central datastore. Devices on the Joint Fabric are available to participating controllers without separate setup in each ecosystem.
- :icon-home: **Thermostat Suggestions** - Ecosystems can send time-limited suggestions tied to thermostat presets. The thermostat can evaluate each suggestion against user preferences, recent manual changes, and current conditions, then explain when it does not follow a suggestion.
- :icon-info: **Device status and safety information** - Devices can report capabilities and operating limits more consistently. Security sensors gain event history, and smoke and carbon monoxide alarms can report when they are unmounted.
- :icon-shield: **Partitioned certificate revocation lists** - Certificate revocation information can be split into smaller, independently updated partitions as the number of certified devices grows.

[!ref target="blank" text="Read the full announcement"](https://csa-iot.org/newsroom/matter-1-6-enables-more-intuitive-setup-multi-ecosystem-experiences-and-context-driven-control/)


---

## Specification Documents

The specification is made up of four documents:

{.compact}
Document | Description
--- | ---
:icon-book: **Core** | Defines the foundational components of Matter, how they interact, and the common procedures that underpin the protocol.
:icon-apps: **Application Cluster** | Details the data models for each cluster that makes up an endpoint, describing their attributes, commands, and events.
:icon-device-mobile: **Device Library** | Sets out the types of end-user devices in Matter and specifies which application clusters each device type requires.
:icon-table: **Namespace** | Defines common data formats and structures shared across multiple clusters. Introduced in version 1.2.

---

## Release History

The Alliance aims to publish two releases per year. The specification follows a **major.minor.patch** versioning scheme:

- **Minor releases** (e.g. 1.4, 1.5, 1.6) introduce new device types, clusters, and protocol features.
- **Patch releases** (e.g. 1.4.1, 1.5.1) primarily contain corrections and clarifications, but may also include smaller new features.

{.clean .striped .compact}
Version | Published | Highlights
--- | --- | ---
[!badge text="1.6.0" variant="success"] [!badge text="Latest" variant="success"] | June 2026 | NFC-based commissioning, Joint Fabric, Thermostat Suggestions, device status and security updates
[!badge text="1.5.1" variant="primary"] | March 2026 | Multi-stream video, HEIC/CMAF media
[!badge text="1.5" variant="primary"] | November 2025 | Cameras, closures, soil sensors, energy tariffs, TCP transport
[!badge text="1.4.2" variant="primary"] | August 2025 | Wi-Fi-only commissioning, security enhancements, certifiable scenes
[!badge text="1.4.1" variant="primary"] | May 2025 | Enhanced Setup Flow, NFC onboarding, multi-device QR code
[!badge text="1.4" variant="primary"] | November 2024 | Enhanced Multi-Admin, network infrastructure, solar, batteries, heat pumps
[!badge text="1.3" variant="primary"] | May 2024 | Energy reporting, EV charging, water management, kitchen appliances, scenes
[!badge text="1.2" variant="primary"] | October 2023 | Vacuums, appliances, smoke/CO alarms, air quality, fans, Namespace Spec
[!badge text="1.1" variant="primary"] | May 2023 | Intermittently Connected Devices (ICD)
[!badge text="1.0" variant="light"] [!badge text="Initial Release" variant="light"] | November 2022 | Lighting, plugs, locks, thermostats, blinds, sensors, media
