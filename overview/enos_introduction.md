# EnOS Overview

Envision EnOS is an IoT operating system that builds on top of open standards and best design to ensure it operates in an open eco-system. EnOS provides comprehensive features and services to cater for different use-case scenarios.


## Key benefits

- **Extensive connectivity**: Simplified ubiquitous connectivity based on rich protocol library.
- **Deployment flexibility**: Enterprise-grade software stack with flexible deployment options (public, private, and hybrid cloud).
- **Domain expertise**: Domain driven data architecture promised by rich experience with smart energy devices and scenarios.
- **Eco-system**: Seamless integration with native and third-party applications, end-to-end tooling that empowers you to build your own platform.


## Major components

EnOS consists of cloud side and edge side as shown in the following figure.

![EnOS architecture](architecture.gif)

## EnOS Cloud

EnOS Cloud provides fundamental capabilities of model-based device asset
management, data acquisition, stream data processing, batch data processing,
custom event triggering and time-sequence data query service.

All features of the EnOS Cloud are exposed as service APIs. Some of those are
provided in EnOS Portal for user to access through a user-friendly graphical
interface.

EnOS Cloud supports native EnOS Edge. If a 3rd party edge is required, EnOS
Cloud also supports 3rd party edges that are compatible with the EnOS device
connection framework.

## EnOS Edge

EnOS Edge provides capabilities of device data acquisition, device controlling,
data normalization, and model-based real-time computing. The data communication
channels between EnOS Edge and EnOS Cloud are secured by TLS/SSL protocol with
dedicated X.509 certificate for each edge device and EnOS Cloud access point.

## EnOS APIs

EnOS provides APIs for developers to add, delete, modify, and retrieve resources
such as users, assets, and applications, to facilitate development of
applications. EnOS adopts a variety of authentication and authorization
techniques to ensure secure access to the APIs.

## EnOS Portal

EnOS Portal is the web-based graphic interfaces for user to interact with
resources in the EnOS.

All functionalities on the web-based graphic interfaces are available from the
EnOS APIs. User will be able to develop dashboards and remotecontrol
functionalities through EnOS APIs according to business operation needs.
