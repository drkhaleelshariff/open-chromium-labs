# Lab 002 - Inside the Chromium Process Model

## Central Investigation Question

When Chromium loads a web page, which process is responsible for what, and how do the processes communicate?

## Investigation Goals

1. Observe the Chromium Browser Process.

2. Observe renderer processes associated with web content.

3. Identify the GPU Process.

4. Identify relevant Utility Processes.

5. Observe the Network Service.

6. Understand the relationship between browser processes and renderer processes.

7. Investigate process isolation.

8. Observe evidence of inter-process communication.

9. Introduce Mojo as Chromium's IPC framework.

10. Distinguish architectural concepts from what can actually be observed in DevTools.

## Evidence Strategy

The lab should prefer observable evidence over assumptions.

For each architectural claim, identify:

- What should be observable?

- Which Chromium or DevTools tool can expose it?

- What evidence should be captured?

- What can the evidence establish?

- What can the evidence NOT establish?

## Initial Experiments

### Experiment 002-A — Observe Chromium's Process Model

Observe a running Chromium instance and identify the major processes associated with the browser and a loaded web page.

The experiment will use observable browser/process information to identify the Browser Process, Renderer Processes, GPU Process and other visible Chromium processes.

The experiment will explicitly distinguish between:

- What can be directly observed

- What can be reasonably inferred

- What requires deeper tracing or source-code investigation

### Experiment 002-B — Observe Renderer Processes

Investigate renderer process behaviour when loading web content and opening additional pages or sites.

### Experiment 002-C — Observe the GPU Process

Identify the GPU Process and investigate what evidence can be obtained about its role.

### Experiment 002-D — Observe Utility and Network Processes

Identify relevant Utility Processes and the Network Service and determine what can actually be observed about their responsibilities.

### Experiment 002-E — Investigate Process Isolation

Perform controlled observations that help explain why Chromium separates work across processes.

### Experiment 002-F — Introduction to Mojo / IPC

Establish an evidence-based introductory understanding of communication between Chromium processes and services.

## Book 1 Alignment

**Book:** URL → Pixels

This laboratory deepens the process-model portion of the URL → Pixels journey.

The lab should explain the architectural roles that were introduced conceptually in Lab 001 and prepare the reader for deeper investigations of Blink, Mojo, Viz, rendering and performance.

## Book 2 Alignment

**Book:** Inside Chromium

This laboratory provides the first experimental foundation for:

- Chromium's multi-process architecture

- Browser Process

- Renderer Process

- GPU Process

- Utility Processes

- Network Service

- Process isolation

- Mojo / IPC

## Methodology

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

