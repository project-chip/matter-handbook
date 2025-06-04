+++
title = "Development"
chapter = true
weight = 5
pre = "<b>5. </b>"
+++

# Matter Development

Developers have multiple options for creating Matter-certified devices, bridges, or controllers. The official Matter SDK is the recommended choice for most projects, but alternative implementations, such as JavaScript, also offer compelling features for certain use cases.

The following table provides a general overview of various use cases for the available SDKs:

| Use Case                                                                  | Official SDK | JavaScript SDK |
|---------------------------------------------------------------------------|--------------|----------------|
| Compliant with Matter version                                             | 1.4.1        | 1.4.1          |
| Participate in development of new Matter features                         | X            | –              |
| Use for embedded platforms with strict memory and performance constraints | X            | –              |
| Chipset-specific implementations (e.g. Wi-Fi/Thread)                      | X            | –              |
| Use on OS-based platforms: Linux, macOS                                   | X            | X              |
| Use on Windows                                                            | –            | X              |
| Ideal for rapid prototyping and testing                                   | –            | X              | 

## The official Matter SDK

The official Matter SDK, written in C++, is fully aligned with the latest Matter specifications and optimized for embedded devices with strict memory and performance constraints. It serves as the foundation for most chipset-specific SDKs.

The SDK is compatible with Linux and Darwin platforms and supports integration as a binary dependency for Python, Objective-C, and Java bindings. It includes several example applications for different platforms and supports configuration for various endpoints and clusters using the ZAP tool.

To learn more, go to the [Matter SDK Documentation](https://project-chip.github.io/connectedhomeip-doc/index.html).

## matter.js - The Matter JavaScript SDK

The JavaScript SDK implements Matter in pure JavaScript, utilizing TypeScript’s typing system for automatic data and system model compliant development. It can be used to build devices, bridges, and controllers running an operating system where a JavaScript runtime, like Node.js, is available.

This SDK includes ready-to-use example projects and is particularly suited for rapid prototyping and testing, thanks to its compliance-by-default approach and the simple but powerful API design.

To learn more, go to the [Matter JavaScript SDK documentation](https://matter-js.github.io/docs/index.html).

Note: Some features of the Matter protocol are not yet implemented in the JavaScript SDK. For details about this check the [matter.js Compatibility Information](https://github.com/project-chip/matter.js/blob/main/docs/MATTER_COMPATIBILITY.md).



