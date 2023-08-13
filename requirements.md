# Requirements
This document capture requirements on a data model. 
Each requirement can contain explanation as well as suggest implementation.

## R01: There is an entity.
We can express existence of an entity.

## R02: There is a property.
We can express existence of a property.
No additional information such as a connection to an entity is required.

### Explanation
We can be able to detect existence of a property with no connection to an entity.

## R03: Entity can have properties.
Entity can have none, one or more properties.
No ordering or additional information is defined.

## R04: Technical resources can have a technical name.
Technical resources can have a technical name.
At most one technical name can be assigned.
A single technical resources can be used under different names.

### Explanation
For example in frontend, backend and database.
As a result, it may seems logical to allow for multiple technical names.
This can be handy when entities from different sources are merged together.
Yet by doing so we would loose ability to distinguish between the sources.
Instead we allow for only a one and introduce aggregation later.

## R05: There is a type.
We can express existence of a type with no additional information given.

### Explanation
Introducing type for each entity can be labour intensive.
Yet this allow for easier extension and easier to work with structure.

## R06: Property can have a type.
Property can have a type. 
Multiple types are not allowed.

### Explanation
In languages like TypeScript or JSON Schema property can have multiple types.
It can be an intersection, anyOf, etc..
We adres all above by introducing additional type.
Thus we are shifting the complexity to working with types.

## R07: There are primitive types.
User can define a primitive type for a language or a format.

### Explanation
User should be able to define custom primitive types.
We can provide list of some predefined ones.

## R08: There are predefined primitive types.
We should predefined primitive types for common languages and formats.

## R09: Optional / required / special handling.
We need to be able to express missing / null / undefined value of a property.
Inspired by TypeScript this should be handled using additional types.

## R10: There are composite types.
A type can be defined as a set of entities or types.
There is no ordering or additional information.

## Explanation
Original idea was to make it similar to TypeScript:
- infer available properties for reading using intersection,
- allow user to assign all entities.
But there can be different types of containers, list, set, ordered list, ...
A solution is just to allow for composite types and introduce other mechanic to handle details.

## R11: There are predefined composite types.
We need to predefine basic composite types like an array.
