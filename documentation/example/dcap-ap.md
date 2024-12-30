# DCAT-AP
For purpose of this example we use following prefixes:
```turtle
@base <http://example.org/> .
@prefix dsc: <https://skodapetr.github.io/data-schema/1.0.0/core#> .
@prefix dst: <https://skodapetr.github.io/data-schema/1.0.0/type#> .
@prefix dsf: <https://skodapetr.github.io/data-schema/1.0.0/format#> .
```

We start by introduction of basic entities using only the core module.
We express the information that we observed three entities, catalog, dataset and distribution.

```turtle

:catalog a dsc:Entity .

:dataset a dsc:Entity .

:distribution a dsc:Entity .

```

We also observe relation between those entities if form of associations.
Data schema made no distinction between attribute and association, it's just a property.
We start by declaring the properties.
```turtle

:hasDataset a dsc:Property .

:hasDistribution a dsc:Property .

```

With properties declared, we observe them to be part of respective entities.
```turtle

:catalogHasDataset a dsc:Observation ;
  dsc:subject :catalog ;
  dsc:predicate dsc:property ;
  dsc:object :hasDataset .

:datasetHasDistribution a dsc:Observation ;
  dsc:subject :dataset ;
  dsc:predicate dsc:property ;
  dsc:object :hasDistribution .

```

In order to declare ranges for the properties we first need to define the types.
```turtle

:datasetType a dsc:Type .

:distributionType a dsc:Type .

```

With types declared we define ranges for the properties.
```turtle

:hasDatasetType a dsc:Observation ;
  dsc:subject :hasDataset ;
  dsc:predicate dsc:range ;
  dsc:object :datasetType .

:hasDistributionType a dsc:Observation ;
  dsc:subject :hasDistribution ;
  dsc:predicate dsc:range ;
  dsc:object :distributionType .

```

At this point, this is all we can do with the core module.

## Using Type module
As you can see, there is no connection between types and entities.
We could use the same identifier or employ another module.

```turtle

:datasetEntityType a dsc:Observation ;
  dsc:subject :datasetType ;
  dsc:predicate dst:entityType ;
  dsc:object :dataset .

:distributionEntityType a dsc:Observation ;
  dsc:subject :distributionType ;
  dsc:predicate dst:entityType ;
  dsc:object :distribution .

```

## Using Format RDF module
Although we are using RDF resources with IRIs, those are not IRIs that should be used for RDF representation.

The next step is to define classes for entities: catalog, dataset and distribution.
```turtle

:catalogClass a dsc:Observation ;
  dsc:subject :catalog ;
  dsc:predicate dsf:rdfClass ;
  dsc:object <http://www.w3.org/ns/dcat#Catalog> .

:datasetClass a dsc:Observation ;
  dsc:subject :dataset ;
  dsc:predicate dsf:rdfClass ;
  dsc:object <http://www.w3.org/ns/dcat#Dataset> .

:distributionClass a dsc:Observation ;
  dsc:subject :distribution ;
  dsc:predicate dsf:rdfClass ;
  dsc:object <http://www.w3.org/ns/dcat#Distribution> .

```

With the classes defined now it's time to define predicates.
```turtle

:hasDatasetPredicate a dsc:Observation ;
  dsc:subject :hasDataset ;
  dsc:predicate dsf:rdfPredicate ;
  dsc:object <http://www.w3.org/ns/dcat#dataset> .

:hasDistributionPredicate a dsc:Observation ;
  dsc:subject :hasDistribution ;
  dsc:predicate dsf:rdfPredicate ;
  dsc:object <http://www.w3.org/ns/dcat#distribution> .

```
