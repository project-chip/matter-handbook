> Some links on this page are only accessible to Alliance members.

Feature developers are not only tasked with developing the specification and implementation (SDK) for a new feature, but are also required to develop and support the certification program that is used to ensure that devices implementing the feature are compliant.

Although this process is occasionally depicted as a waterfall, test development is an important feedback to both the specification and the implementation of a new feature. Tests should be developed in conjunction with the implementation and feed back into the specification when areas are unclear or difficult to test.

Certification program development consists of several different components, each of which is handled by the feature tiger team:
- Test plan development
- Test automation
- Test harness support
- Test validation through test and validation events
- Interop lab support
- Ongoing support

## Test plan development
The test plans form the official record of the certification program requirements and are a part of the official ballot per the [CSA policies and procedures](https://csa-iot.org/wp-content/uploads/2022/10/13-0625-090-organizational-processes-and-procedures_2023-03-23.pdf)

Information on how to get started writing test plans is available in the test plans repo [Getting Started Guide](https://github.com/CHIP-Specifications/chip-test-plans/blob/master/docs/getting_started.md).

Further information about test plan development is available in the [Test Plans documentation](https://github.com/CHIP-Specifications/chip-test-plans/tree/master/docs).

Test plans are developed in the [test-plans GitHub](https://github.com/CHIP-Specifications/chip-test-plans).

Compiled versions of the test plans can be found on the [CSA-IOT document site - test plans](https://docs.csa-iot.org/chip-test-plans/).

## Test Automation
All server-side tests are required to be fully automated either in YAML or Python with the exception of testing actions triggered outside of Matter. (e.g., press a button to test switch event generation, trigger a sensor to confirm a state change in a cluster.)

Further information about the Automation requirements can be found in the [Test Plans Getting Started Guide](https://github.com/CHIP-Specifications/chip-test-plans/blob/master/docs/getting_started.md#automation-requirements).

During certification testing, tests are run in the test harness. Certification tests are also run in the SDK CI. Most tests can also be run locally for development purposes.

Information about the test harness including the test harness user guide can be found in the [Official Release Documentation](https://groups.csa-iot.org/wg/members-all/document/folder/2269) for each release.

Information about the SDK and certification testing can be found in the [SDK Testing Guide](https://project-chip.github.io/connectedhomeip-doc/testing/index.html).

Certification tests can be automated either in YAML or Python. Information on how to automate tests can be found in the [Integration Testing Guide](https://project-chip.github.io/connectedhomeip-doc/testing/integration_tests.html).

Members automating tests should join the [Test Harness Tiger Team](https://groups.csa-iot.org/wg/matter-csg-thd/dashboard)(under the Certification Sub-Group).

## Test harness support
The test harness is used by the test laboratories when doing official testing of devices for certification. The test harness runs on a raspberry pi and contains the official versions of all the tests approved for a particular specification revision.

Tiger teams are responsible for ensuring that their tests run properly not only in the CI and locally, but also in the test harness.

For many features, the standard TH is sufficient to run the tests required. Developers automating tests should use the [Test Harness Helper functions](https://project-chip.github.io/connectedhomeip-doc/testing/python.html#test-harness-helpers) to ensure the test steps and results are reported correctly.

Some features require special settings or hardware to properly test devices. For example, NFC chips, cameras, particular network settings. Teams that have these types of requirements should engage with the test harness tiger team early to ensure that the test harness can accommodate the requirements and any required hardware can be obtained by the test labs (ATLs). Tiger team members are responsible for implementing the required test harness changes, with the support of the test harness development team.

Members doing test harness development should join the [Test Harness Tiger Team](https://groups.csa-iot.org/wg/matter-csg-thd/dashboard)(under the Certification Sub-Group).

Code for the test harness itself is available in the [Matter certification-tool GitHub](https://github.com/project-chip/certification-tool).

## Test validation through test and validation events
The feature tiger team is responsible for supporting the validation of the tests through the test and validation events.

Specification features cannot be declared officially certifiable until three separate implementations are tested at an official validation event. One of those implementations may be the SDK, as tested by the quality assurance team.

Specification Validation Events (SVEs) are held in conjunction with each release. These are gated, in-person test events. Manufacturers who are bringing an implementation of the feature travel to the validation event location and work with members from an Authorized Test Lab (ATL) to validate the tests.

Participation in the Specification Validation Event is gated by participating in the Test Events (TEs) leading up to the SVE. The number and requirements of the test events can vary based on the contents of the release. Generally, there are multiple test events. The first event is normally lighter, and focused on getting manufacturers familiar with the test harness and running tests. The test event before the SVE is a trial run of the SVE. All tests need to be complete by the test event preceding the validation event

Test events are run virtually, where manufacturers run tests against their implementation themselves, and then upload the results to the CSA test event database - [Test Event Data Stockpile - TEDS](https://zigbeecertifiedproducts.knack.com/test-event-data-stockpile-teds#teds-for-matter/).

SVEs are run in-person and participating manufacturers and ATLs are required to travel to the event location. Most SVE events are now held in multiple global locations and manufacturers can select their preferred location. SVE events last one week, and manufacturers are expected to be present for the entire week to run and debug tests. The set of required tests is identified before the event by the CSA staff and CSG. All manufacturers at an SVE are required to run the full suite of applicable tests from the SVE test suite, in order to support both their own feature, as well as core improvements.

Event participants are supported by the CSA staff and supporting volunteer members. Participants can communicate on a private event slack and raise issues in the GitHub repo. Bugs found and fixed during the validation event should be re-run by participants in order to validate the fixes.

Participants in test and validation events are required to abide by the [Test Event Rules of Engagement](https://groups.csa-iot.org/wg/members-all/document/128), which include confidentiality rules. These are in place to allow manufacturers to participate in test events with unreleased products.

Team members that are validating their features at test and validation events, but who are not actively participating by testing against their own device, can and should request to be added as support staff for the event. Support staff are also required to abide by the [Test Event Rules of Engagement](https://groups.csa-iot.org/wg/members-all/document/128) and are permitted to participate and engage with testers on the slack channel. This type of timely support is key to ensuring that bugs can be fixed before the end of the event. Tiger team members should make this request to either the CSG lead or the CSA staff before the start of the event registration (prior to 4 weeks before the event).

Official information about the test and validation events is available in the [Certification Policy](https://groups.csa-iot.org/wg/members-all/document/previewpdf/125)

### Minimal Validation Events
The Matter working group is now also testing Minimal Validation Events. These events are smaller, virtual and are used to support smaller improvements and technical changes that would otherwise be difficult for manufacturers to travel to support. The certification policy for these events is currently under development, and the first event of this type is being tested as a part of the 1.4.2 release.

## Interoperability lab support
The interop lab runs tests on production devices in a simulation of a standard household set up and use case. Devices submitted to the interoperability lab are run through a series of tests by the lab technicians. Some of these tests are standard across all devices (ex. setup, commission to multiple fabrics etc.) There are also device-specific tests where the technicians exercise the functionality of the devices using various ecosystems.

The test plans for the interoperability lab are designed in conjunction with the tiger team, the ecosystem and the lab technicians through the interoperability tiger team. Properly designing the interoperability test plans ensures that the desired functionality can be tested.

Many ecosystems also accept results from the interoperability lab for certifying devices with their "Works With" (WW) programs and designing a proper test plan for the interop lab facilitates the use of the interoperability lab for these new features and device types.

Information about the interoperability testing facility can be found on the [CSA-IOT Interoperability Testing Facility](https://csa-iot.org/certification/interop-lab/) page.

Members are welcome to join the [Matter CSG Interoperability Tiger Team](https://groups.csa-iot.org/wg/matter-csg-interop/workgroup) (under the Certification Sub-Group).

Members may also join the [Matter MPSG PMTT Interop Lab Works With Tiger Team](https://groups.csa-iot.org/wg/matter-mpsg-pmtt-int/workgroup)(under the Marketing and Product Sub-Group -> Product Marketing Tiger Team).

Interop lab test plans can be found on the [matter-interoperability GitHub](https://github.com/CHIP-Specifications/matter-interoperability).

## Ongoing support
As manufactures begin certifying the feature in their products, device, test and implementation bugs often arise. Manufacturers facing challenges during development and certification may reach out over slack or by filing a [Change Control Board (CCB) request](https://zigbeecertifiedproducts.knack.com/zigbee-alliance-ccb-tool#home/) that should be addressed by the tiger team.
