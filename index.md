---
title: Introduction
layout: home
nav_order: 1
permalink: /
---
{: .fs-9 }
# OpenDrive Framework

{: .fs-6 .fw-350 }
OpenDrive Framework is an open-source project designed to accelerate the development of autonomous driving systems.It provides a modular structure and the necessary tools to create a complete development environment for autonomous vehicles.

OpenDrive Framework allows developers to work on detection, perception, and decision-making components, facilitating the creation of custom autonomous systems.


[View it on GitHub][Just the Docs repo]{: .btn .fs-5 .mb-4 .mb-md-0 }

---

{: .Warning }

> This software is for educational purposes only . USE THE SOFTWARE AT YOUR OWN RISK. THE AUTHORS AND ALL AFFILIATES ASSUME NO RESPONSIBILITY FOR YOUR TRADING RESULTS.
> We strongly recommend you to have basic coding skills and Python knowledge.

---


## Objective

The goal of **OpenDrive Framework** is to simplify the development of autonomous driving systems by providing well-defined, ready-to-use components while maintaining the flexibility to customize or replace modules as needed. This project is designed to be accessible to developers who wish to experiment and contribute new features, bug fixes, and improvements.

## Project Structure

The framework is divided into three main modules, each designed to fulfill specific functions within an autonomous system:

- **Sensor Module**: Captures and processes real-time data from cameras and other sensors. Currently, it supports data acquisition through cameras.
- **Perception Module**: Uses pre-trained AI models to analyze data captured by the sensors, performing tasks such as object detection, lane recognition, and traffic sign detection.
- **Decision-Making Module**: Based on the results provided by the perception module, this module defines the actions or warnings that the vehicle should take.

## Principles

**OpenDrive Framework** is guided by the following principles, aimed at maintaining a modular, flexible, and developer-friendly system:

- **Modularity**: Each module has well-defined functions and APIs, allowing them to work together seamlessly. Developers can contribute to or modify modules without affecting the rest of the system.
- **Interchangeable Architecture**: Although OpenDrive Framework provides the necessary components to build a complete autonomous system, its modular architecture allows developers to replace components with their own implementations.
- **Security without compromising usability**: The framework offers secure default settings, ensuring system integrity without making it difficult to use.
- **Developer-focused**: The APIs are designed to be functional and useful for building powerful tools. The documentation and user experience are aimed at developers, making integration and extension easier.

## Contributions

OpenDrive Framework is an open project, welcoming contributions from the community. Whether you want to add new features, improve performance, or fix bugs, all contributions are welcome. To get started, check out the [Contribution Guide](CONTRIBUTING.md) and follow the established development standards.


[Just the Docs repo]: https://github.com/OpenDriveDevelopment/OpenDrive
