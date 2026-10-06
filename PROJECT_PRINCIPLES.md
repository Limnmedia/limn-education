# LIMN Education — Project Principles

## Purpose

LIMN Education exists to make the art, craft, science, and technology of stop-motion animation more understandable, teachable, accessible, and durable.

The project encompasses education, curriculum, reference material, tools, software, and production knowledge. Individual courses, applications, platforms, and technologies serve that larger purpose; they do not define it.

These principles guide decisions when the correct implementation is not otherwise specified.

## 1. Uplift Stop-Motion

LIMN Education exists in service of the larger art and practice of stop-motion animation.

The project should strengthen the knowledge, capabilities, accessibility, and continuity of the field rather than exist primarily to promote a particular LIMN product, technique, course, institution, or technology.

The measure of success is not adoption of LIMN itself, but whether people are better able to understand, practice, teach, and advance stop-motion.

## 2. Education Is Infrastructure

Education is not documentation added after a tool has been built.

Knowledge, terminology, curriculum, teaching methods, references, and pathways into professional practice are foundational infrastructure.

Tools should support learning, and learning should inform the tools.

## 3. Teach the Professional Method Without Hiding It

Accessibility does not require replacing professional practice with a simplified imitation of it.

Whenever practical, teach authentic methods, terminology, reasoning, and production practices in forms that beginners can understand and progressively master.

Complex ideas should be made understandable rather than unnecessarily concealed.

A learner should be able to begin simply without being taught something they must later unlearn.

## 4. Make Tacit Knowledge Explicit

Much of stop-motion knowledge has historically traveled through apprenticeship, studio culture, individual experience, and undocumented production practice.

LIMN Education should identify, describe, test, organize, and preserve that knowledge wherever possible.

Document not only what experienced practitioners do, but also the terminology, measurements, relationships, assumptions, and reasoning that make the knowledge transferable.

## 5. Ground Learning in Physical Reality

Stop-motion is fundamentally connected to physical objects, cameras, light, space, time, materials, and movement.

Whenever practical, begin with relationships that can be observed, measured, constructed, tested, compared, and repeated.

Software should extend understanding rather than substitute for it.

A learner who understands the underlying relationship should remain capable even when the particular tool changes.

## 6. Connect Disciplines

Stop-motion does not exist in isolation.

Its practice intersects with animation, fabrication, cinematography, photography, optics, lighting, engineering, motion control, surveying, VFX, compositing, software, production, and many other disciplines.

LIMN Education should build useful bridges between these fields without requiring learners to become specialists in all of them.

Where different disciplines describe the same underlying problem differently, help make those relationships visible.

## 7. Knowledge Should Travel

Important educational knowledge should not exist only inside an LMS, database, proprietary application, hosted service, or other single system.

Preserve durable source material in portable, documented, widely supported formats whenever practical.

Publishing systems may transform that material into lessons, websites, PDFs, presentations, applications, or other experiences, but the underlying knowledge should remain recoverable.

A change in publishing technology should not require rebuilding the intellectual foundation of the project.

## 8. Prefer Adapters Over Dependencies

People should be able to benefit from one part of LIMN Education without being required to adopt the entire LIMN ecosystem.

Courses should not unnecessarily require LIMN hardware. Educational resources should not unnecessarily require LIMN software. Useful methods should remain useful outside the system that introduced them.

When systems must interact, prefer documented interfaces, portable representations, and adapters over unnecessary hard dependencies.

Progressive adoption is preferable to lock-in.

## 9. Open Knowledge Expands Access

Methods and educational knowledge become more valuable when people can study, teach, test, adapt, preserve, and build upon them.

LIMN Education should favor broad access to knowledge while allowing sustainable value to be created through teaching, manufacturing, integration, support, publishing, services, and deeper engagement.

Openness and sustainability should reinforce one another rather than be treated as opposites.

## 10. Preserve Provenance and History

Educational material should make its origins understandable.

Where practical, distinguish among:

* original LIMN work;
* established professional practice;
* measured or experimentally derived information;
* referenced or adapted material;
* third-party contributions;
* interpretation or synthesis;
* generated or machine-assisted material;
* hypotheses, proposals, and unresolved questions.

Sources, authorship, measurements, assumptions, and significant changes should be preserved when they materially affect understanding.

Uncertainty should be documented rather than silently converted into certainty.

## 11. Build From Demonstrated Needs

Do not create abstractions, schemas, services, directory structures, automation, or dependencies merely because they might someday be useful.

Allow real educational material, learner needs, teaching experience, production requirements, and demonstrated technical problems to reveal the structure the project needs.

Start with the simplest structure that preserves the important information and relationships.

Generalize after patterns emerge.

## 12. Humans Remain Responsible

Automation and artificial intelligence may assist with research, organization, transformation, analysis, software development, publishing, and other project work.

They do not remove human responsibility for the result.

Consequential technical, architectural, educational, factual, editorial, and licensing decisions should remain subject to human review.

Automated systems should not silently establish project-wide conventions as side effects of unrelated work.

## 13. Infrastructure Will Change; Knowledge Should Survive It

Programming languages, frameworks, LMS platforms, hosting providers, repositories, AI systems, file formats, and production technologies will change.

The architecture of LIMN Education should assume this.

Frappe, GitHub, and the present development stack are current implementations, not permanent definitions of the project.

Whenever practical, separate durable knowledge and project intent from replaceable infrastructure.

The project should remain understandable and reconstructable even after today’s tools are obsolete.

## 14. Leave the Path Smoother for the Next Filmmaker

LIMN Education should preserve and share hard-won knowledge so that the next person does not have to rediscover everything from the beginning.

Documentation, teaching, open tools, careful terminology, reproducible methods, and thoughtful design are forms of mentorship.

The goal is not to remove the difficulty, experimentation, or craft from stop-motion.

The goal is to remove unnecessary barriers to learning it.

Leave behind better maps, better tools, clearer language, and a smoother path for whoever comes next.

## Applying These Principles

These principles sit above implementation decisions.

The intended decision hierarchy is:

```text
Mission → Project Principles → Architecture → Implementation → Tools
```

When making a project-wide decision, prefer the choice that best preserves the principles above rather than the choice that is merely most convenient for the current toolchain.

Changes that establish significant new conventions should be deliberate. Examples include:

* top-level repository structure;
* canonical content formats;
* schemas and data models;
* licensing;
* sources of truth;
* major dependencies;
* publishing architecture;
* storage strategy;
* deployment architecture;
* project-wide naming conventions.

Do not silently establish these conventions while performing an unrelated task.

If a requested implementation appears to conflict with these principles, identify the conflict rather than quietly working around it.

## Current Implementation Context

The current LIMN Education development environment uses technologies including Git, GitHub, Frappe, and related infrastructure.

Those technologies are implementation choices beneath these principles.

Detailed environment information belongs in `DEVELOPMENT_ENVIRONMENT.md` and other technical documentation rather than in this document.

Course-specific requirements belong with their respective course material.

This document should change infrequently. Amend it when the underlying philosophy of LIMN Education changes, not merely because the implementation changes.
