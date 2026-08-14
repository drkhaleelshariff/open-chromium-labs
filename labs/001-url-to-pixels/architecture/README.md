**Lab 001 — Architecture**



**URL to Pixels: The Complete Chromium Journey**



This directory contains the architecture reference material for Lab 001.

The architecture diagram provides a conceptual view of how a web navigation

moves through major Chromium subsystems, from a user's URL entry through

network activity, web-content processing, compositing, graphics and final

presentation.



**Architecture Diagram**



**URL to Pixels — The Complete Chromium Journey**



!\[Lab 001 Architecture](Lab001-URL-to-Pixels-Architecture-v1.0.png)



**Purpose**



The diagram is intended to provide a high-level mental model before the

learner begins the hands-on experiments.



It should not be interpreted as a literal sequence of function calls or as

a complete representation of every Chromium process, thread, service or

platform-specific implementation.



Chromium is a highly concurrent and multi-process system. Several activities

can occur in parallel, and the exact implementation can vary according to

platform, configuration and browser state.



**Major Areas**



The architecture diagram groups the journey into several major areas:



**1. User / Input**



The journey begins with a user entering or otherwise initiating a navigation.

The browser's user interface provides the entry point for navigation.



**2. Browser Process**



The Browser Process coordinates browser-level activities and manages

important browser state and relationships with other Chromium components.



It participates in navigation, process management, browser UI and other

browser-level responsibilities.



**3. Network Service**



Chromium provides networking through its Network Service architecture.



Depending on platform and configuration, the Network Service can run

out-of-process or in-process. The out-of-process configuration is preferred

for isolation and stability on most platforms.



The Network Service handles lower-level networking responsibilities such as

HTTP, sockets and WebSockets.



**4. External World**



The browser communicates with systems outside Chromium, including resources

such as:

\- DNS infrastructure

\- Web servers

\- CDNs and edge services

\- Other network endpoints



The external systems are not Chromium components, but they form an important

part of the URL-to-content journey.



**5. Renderer Process**



Renderer processes handle web content.



The renderer incorporates Blink and related web-platform functionality and

is responsible for processing web content and producing visual updates.



The renderer is intentionally isolated from many privileged browser

operations.



**6. Blink**



Blink is Chromium's rendering engine and web-platform implementation.

For the purposes of this introductory laboratory, the diagram presents a

simplified conceptual path involving activities such as:



&#x20;   HTML

&#x20;     ↓

&#x20;   DOM

&#x20;     ↓

&#x20;   CSS

&#x20;     ↓

&#x20;   Style

&#x20;     ↓

&#x20;   Layout

&#x20;     ↓

&#x20;   Paint



The later experiments will investigate these stages individually.



**7. V8**



V8 is the JavaScript engine used by Chromium.



JavaScript execution interacts with the web platform through Blink and

related bindings.



The diagram therefore places V8 alongside Blink inside the renderer

conceptual area.



**8. Compositing and Viz**



Chromium's compositing architecture involves components including the

Compositor / cc and Viz.

Viz provides infrastructure for compositing and GPU presentation.

The Display Compositor combines submitted frames into a resource that can

ultimately be presented to the user.

This is represented as a separate conceptual part of the journey because

compositing and presentation are important stages between web-content

processing and the final display.



**9. GPU / Graphics**



Graphics operations can involve GPU acceleration or software paths depending

on the platform, configuration and capabilities available to Chromium.



The diagram therefore represents the graphics stage conceptually rather than

assuming that every operation always executes on physical GPU hardware.



**10. Operating System / Platform**



Chromium ultimately depends on the operating system and platform for

resources such as:

\- Window-system integration

\- Graphics drivers

\- Filesystem access

\- Memory management

\- Networking facilities

\- Audio

\- Power-management facilities



The exact responsibilities and implementation details vary by operating

system and platform.



**IPC and Mojo**



The diagram uses dashed communication arrows to represent important

inter-component communication.

Chromium uses Mojo for a substantial part of its inter-process and

inter-component communication architecture.

The arrows in this diagram are intentionally conceptual.

They should not be interpreted as a complete list of every Mojo interface,

message or process boundary involved in a navigation.

A later laboratory will investigate Mojo IPC directly.



**How to Read the Diagram**



Use the diagram in three different ways.



**First pass — Architectural view**



Follow the broad journey:



&#x20;   User

&#x20;     ↓

&#x20;   Browser

&#x20;     ↓

&#x20;   Network

&#x20;     ↓

&#x20;   Web Content

&#x20;     ↓

&#x20;   Compositing

&#x20;     ↓

&#x20;   Graphics

&#x20;     ↓

&#x20;   Display



**Second pass — Responsibility**



**Ask:**



**> Which Chromium component is responsible for this activity?**



**Third pass — Evidence**



**During the experiments, ask:**



**> What evidence can I actually observe that supports this part of the architecture?**



This distinction is fundamental to the Open Chromium Labs methodology.



**Important: Conceptual Model vs Implementation**



This diagram is a teaching model.



It intentionally simplifies Chromium's implementation.



For example, the diagram should not be interpreted as saying:



&#x20;   Browser → Network → Renderer → Viz → GPU



is always a single synchronous sequence.



Chromium contains multiple processes, services, threads, task runners,

IPC mechanisms and asynchronous operations.



The purpose of the diagram is to establish a useful mental model that we

will progressively refine through experiments.



**Evidence-Based Learning**



The laboratories in this repository follow this principle:



&#x20;   Architectural Claim

&#x20;           ↓

&#x20;       Experiment

&#x20;           ↓

&#x20;       Observation

&#x20;           ↓

&#x20;         Evidence

&#x20;           ↓

&#x20;        Analysis

&#x20;           ↓

&#x20;       Conclusion



The architecture diagram represents the starting hypothesis.



The experiments provide observable evidence.



The learner then compares the evidence with the architectural model.



**Related Experiments**



The architecture will be investigated progressively through the experiments

contained in this laboratory.



**Planned areas include:**

**- Web navigation**

**- Network activity**

**- HTML and DOM processing**

**- Rendering**

**- Layout and paint**

**- Browser processes**

**- Performance**

**- Chromium tracing**

**- Compositing**

**- Viz**

**- Graphics and presentation**



**Technical References**



The architecture described here is a simplified educational model based on

Chromium's publicly documented architecture and source-code documentation.



**Important reference areas include:**

**- Chromium Multi-Process Architecture**

**- Chromium Process Model and Site Isolation**

**- Chromium Network Service**

**- Chromium cc compositor**

**- Chromium Viz**



The Open Chromium Labs explanations and diagrams are independently authored

for educational use.



**Version**



**Architecture Diagram:**



**Lab001-URL-to-Pixels-Architecture-v1.0**



**Status:**



**Initial educational architecture**



This architecture will be refined as the laboratory progresses and deeper

Chromium implementation details are investigated.

