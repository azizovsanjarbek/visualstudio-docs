---
title: OOP Extensibility Model reference
description: A reference for OOP Extensibility Model
ms.topic: conceptual
ms.date: 3/31/2023
ms.author: maiak
monikerRange: ">=vs-2022"
author: maiak
manager: jmartens
ms.technology: vs-ide-sdk
---

# Introduction to VisualStudio.Extensibility for VS SDK users

While extensions have typically been loaded into the Visual Studio process, VisualStudio.Extensibility, brings most Visual Studio extensions out-of-process. This out-of-proc model gives you the opportunity to create more reliable, secure, and easier-to-write extensions. The following documentation describes:

* The general architecture of the new extensibility model
* How to take advantage of the new extensibility model's APIs
* How to compile and F5 debug an extension with the new model 
* Resources and code samples to get started writing an extension with the new model

## About the VisualStudio.Extensibility model

The new VisualStudio.Extensibility model aims to address many of the problems developers experience when using and writing extensions in Visual Studio using the old model. These issues include:

* Extension-caused crashes and hangs of Visual Studio and other installed extensions
* Inconsistent hard-to-find docs and APIs, requirements for specialized expertise, and overwhelming architecture
* Having to restart Visual Studio when installing extensions

Writing extensions using VisualStudio.Extensibility provides the following benefits:

* **Increased reliability** – Extensions written with the new model are out-of-proc and do not block the Visual Studio UI.  This means that if the extension crashes, VS will not crash as a result.
* **Reduced API complexity** – The new model’s wrapper API has been built from the ground-up to be more cohesive and simpler to implement while retaining the old model’s advanced functionality.
* **.NET Only** – In order to benefit from latest enhancements on .NET and C#, the new extensibility model will only support .NET for out of process hosting and is hosted in a .NET process.
* **Hot-loading functionality** – Excluding ones requiring VS component prerequisites that haven’t been installed yet, extensions written using the new model can be installed and loaded without needing to restart Visual Studio.
* **Cross-CPU Platform** – Since underlying implementation is based on RPC compatible brokered services and is .NET based, all extensions will run on all CPU platforms supported by .NET runtime.

## Technology

The VisualStudio.Extensibility model is primarily built on top remote RPC contracts that are provided as brokered services from Visual Studio. The extensions are hosted in an external ServiceHub process that communicates with Visual Studio via RPC. Extensions both utilize services provided by Visual Studio and may also provide services to Visual Studio process in certain cases.

Extensibility packages that are provided as part of the SDK consist of base classes, utility methods and wrapper objects around these RPC contracts, with the goal of making the extensibility surface area easier to use and easier to discover, and also make it easier for extension authors to quickly contribute to the Visual Studio ecosystem.

## Next steps

To get started writing an extension using the new model, here are some docs, walkthroughs, samples, and videos to get you started:

* [Documentation Index](../visualstudio-extensibility.md)
* [Create your first extension](create-your-first-extension.md)
