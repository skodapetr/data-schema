# Data Schema
Data schema is a re-usable data description model.
Unlike specifications, data schema does not aim capture data requirements.
Instead, data schema is designed to describe existing data and data models.

The specification is build in a modular way, where each module address particular interest area.
For example, the human readability module defines how to represent information needed to present data schema in a human readable way.
Each module consist of notes.

A note represent a design decision made to address given need.
Each node contains a brief description, meta-model definition, and optionally examples in different data format.
The meta-model is expressed using TypeScript and annotations.

## Module: Core
The core module define basic concepts do data schema.
The guiding design principle is that design schema is build to observe.
As a result the basic unit an observation.
In addition, the module introduces entity, as a container, and a relationship.

## Module: Type
The type system in data schema is inspired by Typescript.
This module define the fundamental types other type system may build upon.
By doing so the type systems should remain compatible.

At the same type data schema is designed to be extensible, so feel free to define custom types.

## Module: Format RDF
Provides ability to capture information about data structure representation using RDF.
It allows to map entities to RDF classes and relationships to RDF predicate.
