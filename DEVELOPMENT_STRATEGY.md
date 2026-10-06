# LIMN Education — Development Strategy

## Plan the Landscape. Build a Slice.

LIMN Education is intended to grow into a broader educational system for the art, craft, science, and technology of stop-motion animation.

We should therefore keep the larger educational landscape in view while resisting the temptation to design the entire system before we have built and taught real material.

Our development approach is:

**Plan the landscape broadly. Build the architecture narrowly. Generalize from evidence.**

## The First Vertical Slice

The first complete vertical slice of LIMN Education is **Fundamentals of Stop-Motion Camera**.

This is not merely sample content for a predesigned platform.

The course is the first real-world proving ground for the educational system itself.

By developing the course from source material through teaching and delivery, we can discover what LIMN Education actually requires.

This includes requirements that may emerge around curriculum, lessons, terminology, reference knowledge, exercises, demonstrations, production workflows, media, physical equipment, software tools, student resources, assessment, publishing, and other parts of the educational process.

We should not assume in advance that each of these requires its own permanent system or abstraction.

## Keep the Larger Landscape in View

Although development begins with a camera course, LIMN Education is not intended to become a camera-only educational system.

Future subject areas may include animation, lighting, fabrication, motion control, visual effects, post-production, production practice, and other areas of stop-motion filmmaking.

When the camera course produces a new requirement, ask:

**Is this requirement specific to this course, or does it reveal something about the larger educational system?**

That question should inform architecture without automatically creating architecture.

## Build From Real Requirements

Implement what the working course actually needs.

Avoid building generalized systems solely because future courses might need them.

When a requirement appears:

1. solve the concrete educational problem;
2. identify whether the solution contains a potentially reusable pattern;
3. keep the larger landscape in view;
4. avoid generalizing prematurely;
5. observe whether the pattern appears again;
6. generalize when there is enough evidence to understand what is actually shared.

The first implementation does not need to become the permanent abstraction.

## Complete the Slice

Whenever practical, prefer completing an end-to-end educational workflow over building many disconnected pieces of future infrastructure.

For the camera course, this means eventually following real material through the full path from authored educational source to a usable teaching and learning experience.

Doing so allows problems at the boundaries between curriculum, tools, media, publishing, instruction, and student use to become visible.

Those boundaries are where many of the important architectural requirements will be discovered.

## Distinguish the Layers

As development proceeds, distinguish among:

### Course-specific needs

Requirements belonging specifically to Fundamentals of Stop-Motion Camera.

### Reusable educational patterns

Structures demonstrated by the camera course that appear likely to serve other LIMN Education material.

### Project-wide infrastructure

Capabilities that have demonstrated a genuine need to operate across the educational project.

### Implementation choices

Current technologies used to provide those capabilities.

Do not promote something from one layer to another merely because doing so seems architecturally tidy.

## Frappe Is Part of the Slice, Not the Definition

The current vertical slice will use Frappe and related technologies to explore course delivery and educational workflows.

This makes Frappe an important part of the present implementation.

It does not make Frappe the definition of LIMN Education.

The educational knowledge and the lessons learned from building the system should remain useful if the delivery technology changes.

## Learn From the Course

The first course should produce more than a finished course.

It should also produce evidence.

We should learn:

* what structures recur;
* what terminology needs shared definition;
* what belongs in durable source material;
* what belongs in the publishing system;
* what educators need;
* what learners need;
* what should remain course-specific;
* what benefits from shared tooling;
* where software genuinely improves teaching;
* where software adds unnecessary complexity;
* what should become a project convention;
* and what should remain flexible.

These findings should guide the next course and the next stage of LIMN Education.

## Generalize Deliberately

A successful solution in the camera course is evidence, not automatically a standard.

Project-wide conventions should emerge deliberately from demonstrated patterns and should remain consistent with `PROJECT_PRINCIPLES.md`.

When evidence supports generalization, document the reasoning for the new convention so future contributors and automated systems can understand why it exists.

## The Goal

The immediate goal is to build an excellent, working Fundamentals of Stop-Motion Camera course.

The larger goal is to learn, through doing that work, how to build a durable educational system capable of supporting the wider practice of stop-motion animation.

We build the slice with the landscape in view.
