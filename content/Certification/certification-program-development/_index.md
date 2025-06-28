+++
title = "Developing a Certification Program for a New Feature"
chapter = false
weight = 4
+++

> Some links on this page are only accessible to CSA members.

Feature developers are not only tasked with developing the specification and implementation (SDK) for a new feature, but are also required to develop and support the certification program that is used to ensure that devices implementing the feature are compliant.

Although this process is often discussed as a waterfall, test development is an important feedback to both the specification and the implementation of a new feature. Tests should be developed in conjunction with the implementation and feed back into the specification when areas are unclear or difficult to test.

Certification program development consists of several different components, each of which is handled by the feature tiger team:
- Test plan development
- Test automation
- Test validation through test and validation events
- Ongoing support

## Test plan development
The test plans form the official record of the certification program requirements and form a part of the official ballot.

Information on how to get started writing test plans is available in the test plans repo [Getting Started Guide](https://github.com/CHIP-Specifications/chip-test-plans/blob/master/docs/getting_started.md).

Further information about test plan development is available in the [Test Plans documentation](https://github.com/CHIP-Specifications/chip-test-plans/tree/master/docs).

## Test Automation
All new server-side tests are required to be fully automated either in YAML or Python with the exception of testing actions triggered outside of Matter. (e.g., press a button to test switch event generation, trigger a sensor to confirm a state change in a cluster.)

Further information about the Automation requirements can be found in the [Test Plans Getting Started Guide](https://github.com/CHIP-Specifications/chip-test-plans/blob/master/docs/getting_started.md#automation-requirements).

During certification testing, tests are run in the test harness. Certification tests are also run in the SDK CI. Most tests can also be run locally for development purposes.

Information about the test harness including the test harness user guide can be found in the [Official Release Documentation](https://groups.csa-iot.org/wg/members-all/document/folder/2269) for each release.

Information about the SDK and certification testing can be found in the [SDK Testing Guide](https://project-chip.github.io/connectedhomeip-doc/testing/index.html).

Certification tests can be written either in YAML or Python. Information on how to write tests can be found in the [Integration Testing Guide](https://project-chip.github.io/connectedhomeip-doc/testing/integration_tests.html).

## Test validation through test and validation events
The feature tiger team is responsible for supporting the validation of the tests through the test and validation events.

Specification features cannot be declared officially certifiable until three separate implementations are tested at an official validation event. One of those implementations may be the SDK, as tested by the quality assurance team.

Specification Validation Events (SVEs) are held in conjunction with each release. These are gated, in-person test events. Manufacturers who are bringing an implementation of the feature travel to the validation event location and work with members from an Authorized Test Lab (ATL) to validate the tests.

Participation in the Specification Validation Event is gated by participating in the Test Events (TEs) leading up to the SVE. The number and requirements of the test events can vary based on the contents of the release. Generally, there are multiple test events. The first event is normally lighter, and focused on getting manufacturers familiar with the test harness and running tests. The test event before the SVE is a trial run of the SVE. All tests need to be complete by this test event.

Test events are run virtually, where manufacturers run tests against their implementation themselves, and then upload the results to the CSA test event database - [Test Event Data Stockpile - TEDS](https://zigbeecertifiedproducts.knack.com/test-event-data-stockpile-teds#teds-for-matter/).

SVEs are run in-person and participating manufacturers and ATLs are required to travel to the event location. Most SVE events are now held in multiple global locations and manufacturers can select their preferred location. SVE events last one week, and manufacturers are expected to be present for the entire week to run and debug tests. The set of required tests is identified before the event by the CSA staff and CSG. All manufacturers at an SVE are required to run the full suite of applicable tests from the SVE test suite, in order to support both their own feature, as well as core improvements.

Event participants are supported by the CSA staff and supporting volunteer members. Participants can communicate on a private event slack and raise issues in the GitHub repo. Bugs found and fixed during the validation event should be re-run by participants in order to validate the fixes.

Participants in test and validation events are required to abide by the [Test Event Rules of Engagement](https://groups.csa-iot.org/wg/members-all/document/128), which include confidentiality rules. These are in place to allow manufacturers to participate in test events with unreleased products.

Official information about the test and validation events is available in the [Certification Policy](https://groups.csa-iot.org/wg/members-all/document/previewpdf/125)

### Minimal Validation Events
The Matter working group is now also testing Minimal Validation Events. These events are smaller, virtual and are used to support smaller improvements and technical changes that would otherwise be difficult for manufacturers to travel to support. The certification policy for these events is currently under development, and the first event of this type is being tested as a part of the 1.4.2 release.