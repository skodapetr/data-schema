# There is a source file.

## Requirement
We can express existence of a file at a particular location.
The file location is relative to a parent project.
The path must start with "./".

## Notes
Should absolute / public path be needed we shall introduce additional property.
Same holds for projects.

## Solution
```Turtle
<http://example.com/resources/source/person.ts> a dsfsc:SourceFile ;
  dsfsc:filePath "./src/person.ts" .
```

## RDF
```Turtle
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .

dsfsc:SourceFile a rdfs:Class ;
  rdfs:label "Source file"@en .

dsfsc:filePath a rdfs:Predicate ;
  rdfs:label "File path"@en ;
  rdfs:range dsfsc:SourceFile ;
  rdfs:domain rdfs:Literal .
```
