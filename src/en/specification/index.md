#
![|700](/static/logos/matter-spec-logo.svg)

The Matter specification is the technical foundation of the Matter protocol. It is updated twice a year, with releases in Spring and Fall.

## Latest Release

!!!base :icon-tag: Version 1.5.1 (March 2026)
All specification documents are available for download from the Alliance website.

[!button variant="base" icon="download" text="Download Specification"](https://csa-iot.org/developer-resource/specifications-download-request/)
!!!

### What's New in 1.5.1

Building on the camera and video doorbell support introduced in 1.5, this maintenance release focuses on streaming efficiency, media capabilities, and device refinements:

- :icon-device-camera-video: **Multi-stream video** - Cameras can now deliver multiple optimized streams simultaneously (e.g. high-res for recording, low-res for mobile, and a separate stream for AI processing), reducing bandwidth overhead.
- :icon-image: **HEIC snapshots & CMAF streaming** - Snapshot images can use the HEIC codec for better quality at smaller file sizes. Recorded video gains HLS/DASH upload support via the CMAF Interface-2 profile.
- :icon-arrow-both: **Pan-tilt-zoom improvements** - Greater flexibility for camera positioning, including better support for installations where the home position is at the edge of the rotation range.
- :icon-bell: **Chime & intercom updates** - Controllers can now request a specific chime sound rather than only the default, enabling per-doorbell or contextual chimes. Intercom devices gain clearer signaling requirements and integrated chime support.
- :icon-bug: **Bug fixes & clarifications** - Recording configuration validation, doorbell stability improvements, and editorial refinements across the camera-related specifications.

[!ref target="blank" text="Read the full announcement"](https://csa-iot.org/newsroom/matter-1-5-1-enhancing-camera-performance-and-expanding-device-flexibility/)

!!!base :icon-lock: Alliance Members
In-progress drafts of the specification are available through the [Secure Document Access Portal](https://docs.csa-iot.org/) (requires Alliance member login).

Members actively contributing to specification development may submit and review content in the [Specification GitHub Repository](https://github.com/CHIP-Specifications/connectedhomeip-spec). If you are a Participant or Promoter member and need contributor access, please email [help@csa-iot.org](mailto:help@csa-iot.org).
!!!

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

- **Minor releases** (e.g. 1.3, 1.4, 1.5) introduce new device types, clusters, and protocol features.
- **Patch releases** (e.g. 1.4.1, 1.5.1) primarily contain corrections and clarifications, but may also include smaller new features.

{.clean .striped .compact}
Version | Published | Highlights
--- | --- | ---
[!badge text="1.5.1" variant="success"] [!badge text="Latest" variant="success"] | March 2026 | Multi-stream video, HEIC/CMAF media
[!badge text="1.5" variant="primary"] | November 2025 | Cameras, closures, soil sensors, energy tariffs, TCP transport
[!badge text="1.4.2" variant="primary"] | August 2025 | Wi-Fi-only commissioning, security enhancements, certifiable scenes
[!badge text="1.4.1" variant="primary"] | May 2025 | Enhanced Setup Flow, NFC onboarding, multi-device QR code
[!badge text="1.4" variant="primary"] | November 2024 | Enhanced Multi-Admin, network infrastructure, solar, batteries, heat pumps
[!badge text="1.3" variant="primary"] | May 2024 | Energy reporting, EV charging, water management, kitchen appliances, scenes
[!badge text="1.2" variant="primary"] | October 2023 | Vacuums, appliances, smoke/CO alarms, air quality, fans, Namespace Spec
[!badge text="1.1" variant="primary"] | May 2023 | Intermittently Connected Devices (ICD)
[!badge text="1.0" variant="light"] [!badge text="Initial Release" variant="light"]| November 2022 | Lighting, plugs, locks, thermostats, blinds, sensors, media
