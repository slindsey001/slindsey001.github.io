---
layout: default
title: Driver Documentation Dependency Resolver
---

# Driver Documentation Dependency Resolver

## Overview

Built a static analysis tool that maps documentation dependencies across a large docs-as-code system, answering a question that previously required slow, manual investigation: "Which drivers use this shared documentation file?"

In a catalog of more than 300 database drivers, documentation is assembled from shared content maintained in a central ProviderBase library. Because shared files are referenced through multiple layers of includes, entities, bundles, and conditional rules, the impact of changing a single file was often difficult to determine. This project focused on making those dependencies instantly visible to improve change confidence, reduce manual investigation, and identify where shared content is used throughout the documentation ecosystem.

Developed during the CData Docs Team 2026 Hackathon.

---

## Responsibilities

- Defined the dependency resolution model across the driver catalog
- Identified and handled multiple documentation inclusion mechanisms, including shared bundles, chapter includes, inline entities, and conditional content
- Validated tool output against ground-truth searches to identify and correct accuracy gaps
- Designed both a command-line interface and searchable web interface
- Documented known limitations and edge cases to improve transparency and trust in results

---

## How It Works

The tool resolves the full chain of references used to build each driver's documentation, beginning with driver-specific content and following references transitively into shared files, bundles, chapters, and entities. The resulting dependency graph is then inverted to show which drivers consume a given shared file.

Key resolution patterns included:

- Transitive dependency resolution across shared bundles, chapter includes, and inline entities
- Authoritative file lookups using generated build indexes rather than naming conventions
- Conditional content evaluation for edition-specific and build-specific documentation
- Attribution tracking showing how each dependency was reached
- Explicit labeling of unresolved content and build-generated edge cases

---

## Example Usage

```text
python doc-deps.py AzureProps/AzureAccessKey.prp
```

---

## Example Output

```text
File:   ProviderBase/help/source/AzureProps/AzureAccessKey.prp
Entity: &AZUREPROPSpAzureAccessKey;
Via:    mixed

Direct body reference (3):
  ProviderDatabricks
  SyncADLS
  SyncAzureBlobDestination

Via shared .map, marked-section gated (10):
  ProviderAccess
  ProviderAvro
  ProviderCSV
  ProviderExcel
  ProviderJSON
  ProviderParquet
  ProviderREST
  ProviderSASDataSets
  ProviderSASXpt
  ProviderXML
```

The web interface presents the same information through a searchable UI with color-coded dependency paths and one-click copying of provider lists.

---

## Lessons Learned

One of the biggest challenges was accurately evaluating conditional content. Early versions of the resolver treated edition-specific conditions too broadly, which led to undercounted dependencies. Comparing results against real documentation searches helped uncover these gaps and improve the overall accuracy of the resolution model.

The project also reinforced the importance of clearly communicating limitations. Some documentation is assembled by the build process itself rather than through traceable references, so the tool explicitly identifies these cases instead of overstating accuracy.

---

## Outcome

The project resulted in a working command-line resolver and searchable web application capable of tracing documentation dependencies across 307 drivers. The tool resolves approximately 97% of referenced shared files, transforming a manual repository-wide investigation into an instant lookup while supporting documentation impact analysis, dependency discovery, and identification of orphaned content.
