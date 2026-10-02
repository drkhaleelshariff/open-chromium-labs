# Chromium Internals Lab 002

## Inside the Chromium Process Model

**Difficulty:** L2 — Observer

**Category:** Browser Architecture

**Estimated Time:** 90–120 minutes

**Lab Type:** Observation, process exploration and evidence-based architecture analysis

## 1. The Question

When Chromium loads a web page, which process is responsible for what?

And perhaps more importantly:

> How do the different Chromium processes work together?

In Lab 001, we followed the broad journey from:

**URL → Network → Web Content → Rendering → Compositing → Graphics → Pixels**

In this laboratory, we will open up that model and examine the **process architecture** underneath it.

Instead of treating Chromium as one large application, we will investigate the major processes that participate in the browser's operation.

## 2. What You Will Learn

By the end of this laboratory, you should be able to:

- Identify major Chromium processes associated with a running browser.
- Explain the conceptual role of the Browser Process.
- Identify Renderer Processes associated with web content.
- Identify the GPU Process.
- Recognize relevant Utility Processes and the Network Service.
- Explain why Chromium uses multiple processes.
- Understand the basic idea of process isolation.
- Recognize evidence of communication between Chromium processes.
- Understand where Mojo fits into Chromium's IPC architecture.
- Distinguish direct observation from architectural inference.

## 3. The Big Picture

Chromium is not a single-process application.

A running Chromium instance may contain multiple processes, each with different responsibilities and privileges.

A simplified conceptual model is:

```text
                         Chromium
                            |
             +--------------+--------------+
             |              |              |
             v              v              v
       Browser Process  Renderer       GPU Process
                            |
                            v
                          Blink
                            |
                            v
                      Web Content

```

Other processes and services participate in areas such as networking, media, storage, graphics and other browser functionality.

The purpose of this laboratory is not to memorize a process diagram.

The purpose is to learn how to **observe the process model and reason from evidence**.

## 4. A Critical Distinction

Throughout this laboratory we will distinguish between three levels of knowledge.

### Directly Observable

What can we actually see using Chromium, DevTools, operating-system process information or tracing tools?

### Reasonably Inferred

What architectural conclusion can we draw from the evidence?

### Requires Deeper Investigation

What requires tracing, Chromium source code, or a dedicated experiment before we can make a strong claim?

This distinction is fundamental to the Open Chromium Labs methodology.

## 5. Investigation Method

Each investigation follows:

```text
Architectural Claim
        ↓
     Experiment
        ↓
    Observation
        ↓
      Evidence
        ↓
     Analysis
        ↓
    Conclusion
```

We will avoid treating a conceptual architecture diagram as proof of a specific implementation detail.

## 6. Experiments

This laboratory will progressively investigate:

### Experiment 002-A — Observe Chromium's Process Model

Identify the major processes associated with a running Chromium instance and a loaded web page.

The experiment will distinguish between what can be directly observed, what can reasonably be inferred, and what requires deeper investigation.

### Experiment 002-B — Observe Renderer Processes

Investigate renderer-process behaviour when loading web content and opening additional pages or sites.

### Experiment 002-C — Observe the GPU Process

Identify the GPU Process and investigate observable evidence of its role.

### Experiment 002-D — Observe Utility and Network Processes

Identify relevant Utility Processes and the Network Service and determine what can actually be observed about their responsibilities.

### Experiment 002-E — Investigate Process Isolation

Perform controlled observations that help explain why Chromium separates work across processes.

### Experiment 002-F — Introduction to Mojo / IPC

Establish an evidence-based introductory understanding of communication between Chromium processes and services.

## 7. What This Lab Does Not Attempt to Prove

This laboratory does not attempt to provide a complete description of every Chromium process, thread, service, task runner or Mojo interface.

Chromium is highly concurrent and its implementation varies by operating system, configuration, browser state and Chromium version.

The process model presented here is therefore a **conceptual model supported progressively by evidence**.

Deeper laboratories will investigate individual subsystems in greater detail.

## 8. Coming Next

The experiments in this laboratory will move from identifying processes to understanding why Chromium is designed around process separation and how those processes communicate.

The next stage will take us deeper into:

- Process isolation
- Renderer architecture
- Mojo IPC
- Blink
- Viz
- GPU architecture
- Chromium tracing
