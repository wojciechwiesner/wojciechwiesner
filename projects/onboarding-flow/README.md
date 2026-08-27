# Onboarding Flow

> Schema-driven onboarding automation designed to minimize manual operator work without giving the LLM control of process state.

**Scale:** ~1,500 people processed with minimal manual intervention  
**Role:** process discovery, product design, architecture and implementation  
**Status:** production system; source code is private/proprietary

## Business problem

Operational onboarding involved repetitive communication, branching business rules, missing data, documents, reminders and handoffs between people and systems. The challenge was not to make an AI chatbot — it was to create a reliable process engine that could keep moving cases forward without an operator manually deciding every next step.

## Architecture

```text
candidate / worker data
        ↓
schema + process state
        ↓
deterministic decision engine
        ↓
next action / integration / communication
        ↓
LLM only where language flexibility is useful
```

A useful shorthand for the design is **~90% deterministic process logic / ~10% LLM**.

## What I owned

- decomposed the existing operational process into states, rules and transitions;
- designed the data schema and execution flow;
- built the automation and external-system integrations;
- used LLMs selectively for language generation and interpretation rather than workflow control;
- handled edge cases and production feedback until manual intervention became the exception.

## Design principles

- process state belongs to the system, not the model;
- repeatable decisions should be deterministic;
- ambiguous language tasks are good LLM boundaries;
- every automated step should be observable and recoverable;
- optimize for operator attention, not for maximum AI usage.

## Why this project matters

The result is an example of AI enablement that changes an actual operating process rather than adding a conversational layer on top of it.

---

Public case study only. Implementation details and source code remain private.