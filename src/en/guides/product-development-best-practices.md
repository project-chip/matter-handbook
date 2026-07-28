---
label: Product Development Best Practices
order: 97
---
# Matter Product Development Best Practices

This document outlines best practices for developing Matter-enabled smart home products, drawing from industry best practices.

## Overview of Product Development Process Stages

The Product Development Process is a phased approach used for hardware development, from concept to end-of-life. Each phase has specific goals, activities, and exit criteria to ensure readiness for the next stage.

1. **Investigation:** Exploring opportunities, technologies, and business justification.
2. **Define:** Establish product concept, features, schedule, and cost goals.
3. **Develop:** Iteratively designing and defining the product, validating early assumptions.
4. **Prototyping:** Building first form-factor units to test core design and functionality.
5. **Engineering Verification Testing (EVT):** Validating engineering design with production-intent parts.
6. **Development Verification Testing (DVT):** Validating the manufacturing process and readiness for mass production.
7. **Production Verification Testing (PVT):** Validating mass production processes and producing marketable units.
8. **Mass Production (MP):** Ramping to full production capacity.
9. **Product Maintenance:** Ongoing product support, improvements, and end-of-life management.

## Detailed Stages for Matter Product Development

### Investigation Stage

**Goal:** To explore potential market opportunities for new Matter devices, assess the technical feasibility of potential solutions, and ensure any pursued concepts align with the company's broader strategic objectives and core competencies. This stage is about idea generation, opportunity sizing, and initial risk assessment before significant resources are committed.

**General Product Development Activities:**

* **Market & User Research:** Analyze market trends in the smart home space and identify unmet user needs or pain points. Conduct foundational user research (e.g., interviews, surveys) to understand user behaviors. Estimate market size and growth potential.
* **Initial Estimates:** Develop cost estimates for development and conduct a high-level assessment of technical risks. Generate a range of product concepts and ideas to address the identified opportunities.

**Matter Specific Activities:**

* **Technology Scouting:** Research available System on Chip (SoC) solutions with robust support for Matter, Thread/Wi-Fi, and Bluetooth Low Energy (BLE). Evaluate Matter stacks from silicon vendors, considering power consumption, cost, and software maturity.

**Exit Criteria:**

* A clear business opportunity for a Matter device is identified and documented.
* Sufficient evidence suggests technical feasibility at a high level.
* The opportunity aligns with the company's strategic direction.
* Internal stakeholders agree to invest resources in further defining a specific product concept.

### Define Stage

**Goal:** To solidify a selected product concept into a well-defined product proposal. This involves detailing key features, defining the target user experience, making critical technology choices, and establishing a preliminary business case, schedule, and resource plan.

**General Product Development Activities:**

* **Product & UX Definition:** Clearly articulate the product vision, goals, and target users. Develop initial user flows for the device setup and control experience. Create early industrial designs to explore physical form.
* **Planning:** Define the Financial Plan, Business Case, and High-Level Schedule. Finalize choices for sensors, connectivity modules, and power sources.

**Matter Specific Activities:**

* **Matter Requirements Definition:**
  * **Functional (Feature Mapping):** Detail the exact Matter device types and specific standard/custom clusters the product will support to achieve its core use cases.
  * **Non-Functional (Ecosystem Strategy):** Acknowledge the architectural shift from a closed, single-app ecosystem to a multi-ecosystem, network-dependent environment. Define stringent non-functional requirements (e.g., latency expectations, multi-admin considerations, network architecture Key Performance Indicators (KPIs)) specifically for this complex, highly variable environment.
* **Comprehensive Matter Lifecycle Planning:** Because Matter operates in a highly dynamic, multi-ecosystem environment, you must draft a lifecycle plan now that accounts for extended software, certification, and post-launch realities. Your plan must define:
  * **Vendor Engagement Timelines:** Do not wait until development. Engage critical external dependencies during this phase.
    * *PKI Providers:* Select and engage a Public Key Infrastructure (PKI) provider for Device Attestation Certificates (DACs) to ensure your factory provisioning infrastructure is ready by EVT.
    * *Authorized Test Labs (ATLs):* Lab queues can back up. Scope your testing windows and establish relationships with ATLs now.
  * **The Certification Critical Path:** Understand that Matter certification is a hard blocker for Mass Production. You must obtain a Certification Declaration (CD) *before* you can legally flash units on the factory line. Plan to begin pre-certification testing during EVT, with final formal certification targeted for early DVT.
  * **FSI vs. Day-0 OTA Strategy:** Acknowledge that the Factory Shipped Image (FSI) locked during PVT may be out of date by the time the product reaches consumers. Because smart home ecosystems update constantly, interoperability bugs may be discovered between factory lock and retail launch. You must architect your launch schedule to consider the high likelihood of a Day-0 Over-the-Air (OTA) update, reserving development resources specifically to patch multi-ecosystem edge cases right before the product hits the shelves.
  * **Rapid/FastTrack Recertification Training:** Matter FastTrack Recertification is a program for recertification of previously certified Matter products that reduces the cost and friction involved in releasing software updates for these products. If you discover bugs between factory image lock (PVT) and retail launch, the FastTrack program will be your primary mechanism to deploy a Day-0 patch without restarting a multi-week ATL queue.
    * Secure budget and schedule time for your engineering team to attend the [mandatory Connectivity Standards Alliance (Alliance) Rapid/FastTrack Recertification Training](https://handbook.buildwithmatter.com/certification/fast-track-recertification-faq/).
  * **Ecosystem "Works With" (WW) Badging Strategy:** Matter certification ensures baseline interoperability, but if your marketing and packaging require specific ecosystem badges (e.g., *Works with Google Home*, *Works with Apple Home*, *Works with Alexa*), you must account for this now. Each ecosystem has its own distinct certification programs, legal agreements, and testing queues that run parallel to (and often require) Matter certification.
  * **Post-Launch Requirements & Resource Allocation:** Matter is not a "ship and forget" protocol. Define the operational budget and engineering resources required for the post-launch phase. This includes monitoring ecosystem changes, addressing security vulnerabilities, fixing bugs and committing to an ongoing OTA cadence to maintain compatibility as the Matter specification inevitably evolves.
* **End-to-End Testing Strategy:** Outline the high-level technical approach for validating Matter, Wi-Fi/Thread and interoperability across all phases of development. Additionally, define how Matter-specific checks (such as verifying secure DAC injection, validating physical QR codes against digital payloads, confirming basic network joining capability, etc) will be integrated into factory test stations and Outgoing Quality Control (OQC) procedures to prevent defective units from shipping.

**Exit Criteria:**

* An approved Product Proposal with cross-functional buy-in.
* A clear path to achieving the desired features, schedule, and cost goals.
* Key technology choices are made, and a viable business case is established.

### Develop Stage

**Goal:** Mature the product design through iteration and early prototyping (e.g., development boards, non-form factor hardware).

**General Product Development Activities:**

* **Architectural Design:** Define the overall system layout including hardware components, Operating System (OS), middleware, and mechanical material selection. Evaluate trade-offs in performance, power consumption, size, cost, and manufacturing feasibility.
* **Reference Hardware Bring-up:** Utilize vendor development kits or non-form factor boards to bring up the SoC. Develop low-level drivers and port the target OS.
* **Risk & Appearance:** Create non-functional physical models for aesthetics and ergonomics. Identify potential schedule, cost, and manufacturing issues and create mitigation plans.

**Matter Specific Activities:**

* **Stack Integration:** Define how the Matter stack will be integrated into the software architecture. If relevant, define how the Thread stack will be integrated into the software architecture.
* **Core Feature Prototyping:** Implement initial integration of Matter stack, conduct basic network connectivity tests, and test device-type-specific cluster logic on reference hardware.

**Exit Criteria:**

* A clear and feasible path forward for the product's hardware, software, and mechanical design.
* Key technical and design assumptions have been tested and validated through Non-Form Factor (NFF) prototyping.
* Major risks have been identified, with credible mitigation plans in place.
* Sufficient confidence to proceed with designing first form-factor prototypes.

### Prototyping Stage

**Goal:** To build the first form-factor devices to validate core design, hardware/software integration, key technology assumptions, and to identify fundamental risks early.

**General Product Development Activities:**

* **Hardware Bring Up:** Fabricate and assemble form-factor Printed Circuit Board Assemblies (PCBAs). Perform basic power-on tests, interface validation, and initial Radio Frequency (RF) circuit testing for Wi-Fi/Thread, and BLE.
* **Base Firmware:** Integrate initial firmware and conduct software unit/integration tests on the hardware.
* **Internal Field Testing:** Ensure internal team members interact with the working prototype for early feedback.
* **Updated Risk Assessment:** Leveraging testing data & user feedback, identify and document new key risks in hardware, software, mechanics, and network performance. Develop mitigation plans.

**Matter Specific Activities:**

* **Core Connectivity Testing:** Verify successful Matter commissioning onto a test fabric. Confirm the device appears correctly with its defined Matter device type and clusters. Verify basic on/off or primary function control via Matter.
* **Network Joining:** Verify successful joining to a test Ethernet/Wi-Fi/Thread network and test basic network reachability.
* **Test Infrastructure Setup:** Set up testbeds and automation frameworks specifically geared for Matter, the chosen network architecture, and multi-ecosystem testing.

**Exit Criteria:**

* Core product features demonstrated on form-factor hardware, with basic software/firmware stability.
* Successful Matter commissioning and basic control established.
* Achieve basic network connectivity (Ethernet/Wi-Fi/Thread).
* Major risks identified with viable mitigation strategies.
* Alignment on final product specifications, features, schedule, and cost.

### Engineering Verification Testing (EVT)

**Goal:** To verify the engineering design against all functional, performance, reliability, and manufacturing feasibility specifications using production-intent design, materials, and processes.

**General Product Development Activities:**

* **Comprehensive Hardware Validation:** Build units with hard-tooled parts. Conduct detailed electrical testing, mechanical testing (fit, drop, vibration), thermal testing, and RF tuning.
* **Software Maturation:** Achieve feature-complete beta quality. Execute full functional test plans, stability tests, and performance profiling.
* **Manufacturing Test Prep:** Develop and validate factory test stations and software.
* **Field Testing (General):** Launch an internal field testing program to gather qualitative and quantitative feedback on usability and feature performance.

**Matter Specific Activities:**

* **Matter Self-Testing & Pre-Certification:** [Matter self-testing](https://handbook.buildwithmatter.com/certification/certifying-a-product/self-pre-test/) is critical at this stage. Validate spec compliance using the [YAML](https://github.com/project-chip/connectedhomeip/tree/master/src/app/tests/suites/certification) or [Python](https://github.com/project-chip/connectedhomeip/tree/master/src/python_testing) SDK folders. Run manual verification steps from the [official release documentation](https://groups.csa-iot.org/wg/members-all/document/folder/2269). Test with the [Matter Test Harness](https://github.com/project-chip/certification-tool/blob/main/docs/Matter_TH_User_Guide/Matter_TH_User_Guide.adoc), as this mimics ATL evaluation.
* **In-Depth Protocol Testing:** Conduct commissioning stress tests, multi-admin commissioning scenarios, subscription testing, and group control testing.
  * For Thread devices, test network joining, multi-hop mesh performance, recovery, and power consumption for sleepy end devices.
* **Network & Ecosystem Interoperability Testing:** Adopt the mindset that in a multi-ecosystem world *"network problems are user problems"*. Test interoperability with major smart home ecosystems, not just one version of your app. Validate device connectivity with distinct networking infrastructure (Wi-Fi Routers, Thread Border Routers).
* **Device Quality Testing:** Protocol conformance testing is not the same as quality testing. The best way to evaluate device quality for Matter devices is by gathering real-world qualitative and quantitative feedback on setup, usability, feature performance, device connectivity, and user-experience in real-world environments.
  * **Product Development Team Testing:** Ensure the majority of members on the product development team have directly used the product over multiple sessions, testing for reliability, performance, and user experience.
  * **Testing with internal users outside the Product Development Team:** Secure field testing program participation from other internal company employees, from a diverse set of functions, both technical and non-technical, to ensure unbiased feedback. Secure a statistically significant number of users to participate in this program; the more participation the better.
  * **Standardized Feedback:** Ensure a standardized feedback collection mechanism, bug submission process, and thorough quantitative data collection for users participating in this program. Direct user feedback, bugs, device logs, and metrics, must be thoroughly analyzed to identify performance/reliability issues, bugs, and user experience quality.
* **Factory Provisioning Preparation:** Finalize the strategy for factory-provisioned items that must be individually allocated per unit (e.g., discriminators, Password-Authenticated Key Exchange (PAKE) verifiers). Determine the manufacturing logic to correctly match QR and manual setup codes to those specific devices.
* **Plugfests:** Participate in Alliance Plugfests if possible.

**Exit Criteria:**

* Production-intent design validated against key specifications.
* Hardware design locked (no major changes anticipated).
* Key Performance Indicators (KPIs) for function, connectivity, and reliability on track.
* Positive results from protocol conformance and interoperability tests.
* Positive initial feedback from user testing.
* Clear resolution paths for all critical or launch-blocking bugs.

### Development Verification Testing (DVT)

**Intent:** To validate the manufacturing process, ensure the product can be built at scale meeting quality and reliability standards, and to finalize the product for certification and mass production.

**General Product Development Activities:**

* **Manufacturing & Reliability:** Build units on the mass production line. Monitor and optimize factory yield. Conduct extensive Highly Accelerated Life Testing (HALT) and environmental stress tests.
* **Regressions:** Execute full regression test suites on hardware and software to catch issues introduced by process changes.
* **Field Testing Expansion:** Expand the field testing program participation with DVT units by at least 2x to focus on long-term stability and edge cases.

**Matter Specific Activities:**

* **Formal Certification:** Submit DVT units to Authorized Test Laboratories (ATLs) for formal certifications (Regulatory, Safety, Wi-Fi, Bluetooth, Thread, and Matter). Apply for Interoperability testing simultaneously with Matter certification to discover and address issues with popular smart home ecosystems.
* **Large-Scale Interoperability:** Expand interoperability testing with a wider range of Matter controllers and networking infrastructure (Wi-Fi Routers, Thread Border Routers). Participate in Alliance Test Events.
* **Conduct “Works With” activities for Ecosystems:** Works With programs for ecosystems require distinct activities (such as field testing, automated testing, etc) in order to satisfy requirements for Works With badges. At this stage you should engage with each ecosystem platform, and kick off completing these activities.
* **Real-World Network Stress Testing:** Passing certification is not a substitute for diligent real-world testing. Extensive field testing in diverse, real-world 3rd-party networking environments and complex multi-admin scenarios with real users is critical prior to launch.

**Exit Criteria:**

* Manufacturing process is stable and capable.
* Pass all formal certification tests (or have high confidence in imminent approval).
* Demonstrate product reliability through rigorous stress testing.
* Successful and extensive Matter & networking interoperability proven.
* No critical, high-severity, or launch-blocking bugs in software or hardware.

### Production Verification Testing (PVT) Stage

**Intent:** To conduct a final validation of the entire mass production process, including assembly lines, test stations, training, and logistics.

**General Product Development Activities:**

* **Production Line Validation:** Run a significant build on the finalized assembly lines to verify repeatable and scalable processes.
* **Test & Packaging:** Verify all factory test stations are operating correctly. Verify final packaging, labeling, and accessories.
* **Factory Shipped Image (FSI) Lock:** Finalize and lock the software image to be flashed on devices during production.

**Matter Specific Activities:**

* **Provisioning Validation:** Ensure the FSI correctly includes all necessary firmware, Matter configurations, and pre-loaded credentials. Validate that the factory lines are successfully and securely injecting individual DACs, discriminators, and PAKE verifiers, and that physical QR codes match the digital records perfectly.

**Exit Criteria:**

* Demonstrated stable and capable manufacturing process.
* Repeatable and reliable test results from all factory test stations.
* FSI software locked and validated.
* All necessary regulatory and compliance certifications are fully approved and received.

### Mass Production Stage

**Intent:** To ramp up manufacturing to full capacity to meet launch inventory needs, ongoing sales forecasts, and quality expectations.

**General Product Development Activities:**

* **Ramp-Up:** Incrementally increase production volume to target levels.
* **Quality Monitoring:** Continuously monitor key production metrics and implement corrective actions. Ensure systems are in place to receive and analyze early field quality data post-launch.

**Matter Specific Activities:**

* **0-Day OTA Update Preparation:** If an update is required immediately at launch (to address multi-admin bugs or interoperability edge cases found after FSI lock), ensure the OTA infrastructure and software image are ready and thoroughly tested across major ecosystems.
  * Leverage Matter FastTrack Recertification program to quickly certify updated image if relevant.
  * Consider OTA update delivery strategy for major ecosystems as some ecosystems will require leveraging their portal to upload and stage OTA updates.

### Product Maintenance

**Intent:** To manage the product throughout its post-launch lifecycle by maintaining long-term security, multi-ecosystem interoperability, and field performance, while executing a structured End-of-Life (EOL) strategy that preserves user trust and meets regulatory compliance.

**General Product Development Activities:**

* **Field Performance & Sustaining Engineering:** Track device performance and hardware reliability through field analytics, crash logs, and product returns. Maintain dedicated engineering resources for root-cause analysis on connectivity drops or field bugs.
* **Ongoing Security & Vulnerability Management:** Continuously monitor Common Vulnerabilities and Exposures (CVE) databases for OS, network stack (Wi-Fi/Thread), and cryptographic library vulnerabilities.
* **Feedback & Support Loops:** Gather and analyze customer reviews and support tickets. Translate user feedback regarding setup or connectivity into actionable software patches.
* **General OTA Updates:** Deploy software updates to fix bugs, address security vulnerabilities, and improve overall performance. Leverage ecosystem developer portals to manage OTAs and ensure smooth and consistent deployments.

**Matter Specific Activities:**

* **Ecosystem & Network Monitoring:** Track commissioning success rates, network stability, interoperability issues across different major ecosystems, and OTA update uptake rates.
* **Standard Evolution & Upstream SDK Upgrades:**
  * Actively track updates to the open-source Matter SDK and establish a cadence for merging upstream bug fixes and security patches into your production firmware branch.
  * Evaluate new Matter specification releases to determine whether backporting new features to existing hardware is valuable and viable (given memory constraints).
* **Ecosystem Interoperability Maintenance:**
  * Maintain active testbeds with updated ecosystem hubs and mobile OS releases to catch regression bugs introduced by 3rd-party updates.
  * Utilize the Rapid/FastTrack Recertification program to cost-effectively re-certify products when releasing firmware updates or stack upgrades.
  * Ensure ongoing compliance with ecosystem-specific "Works With" badge requirements as program rules evolve over time.
