# Changelog

All notable changes to this project will be documented in this file.
The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [Unreleased]
### Added

### Changed


## [3.3.0-beta] - 2026-06-30
### Added
- New documentation page listing unsupported UML constructs, describing the
  behaviour each unsupported construct produces and why it is not transformed.
- Documentation of the optional OWL-full consolidated artefact and the
  `generateOWLFull` and `fullArtefactURI` configuration parameters (M2O3-234).
- Documentation of `{disjoint}` generalization-set support in the OWL-restrictions
  artefact (M2O3-235).
- CAUTION admonition documenting the bidirectional-connector directionality
  pitfall in the generalisation-connector conventions.
- Documentation of the `Character` UML primitive datatype mapping to `xsd:string`.
- Documentation of datatype-union range generation for data properties with mixed
  reused datatypes.
- Documentation of the unified `METADATA_JSON_PATH` Make parameter.
- Guidance for using `includedPrefixesList=('')` with unprefixed ontology models.
- Documentation of the `annotateDefinedConceptsWithOntology` (OWL) and
  `annotateShaclConceptsWithOntology` (SHACL) parameters that control whether
  `rdfs:isDefinedBy` annotations are generated; suppression NOTEs added to the
  corresponding transformation rules T.08/T.09.

### Changed
- Association class and qualified association handling described as best-effort,
  with an explicit statement of what is omitted from generated artefacts.
- Generalization-set default-semantics note rendered as a NOTE admonition.
- Covering and completeness generalization-set constraints documented as
  unsupported.
- Connector-generalisation convention updated to reflect the directionality
  pitfall guidance.
- Checker documentation for general-connector-type-1 and general-element-type-2
  updated to match the softened code wording.
- Generalisation-connector checker documentation aligned with the actual checker
  IDs (-9/-10).
- Checker messages for unsupported constructs updated to match the new
  convention-report wording.
- `{disjoint}` modifier removed from the unsupported-constructs list.

### Removed
- Documentation of the removed checker `connectors-with-same-name-multiplicity-1`.
- Documentation of the removed checker `class-attributes-reuse-data-types-3`
  (differing datatypes on a reused attribute are now supported).


## [3.2.0-rc.2] - 2026-02-03
### Added
Introduce a description of generating RDF diff reports for multiple modules in the user guide (TEDM2O-12).

### Changed
- Update the user guide for the RDF diffing feature (TEDM2O-12).
- Update the configuration and usage instructions for the RDF diffing feature (TEDM2O-12).
- Update references to the RDF Differ repository (TEDM2O-12).


## [3.2.0-rc.1] - 2025-12-09
### Added
- Introduce RDF Diffing feature (TEDM2O-12).
- Add description of the new `generate-asciidoc-glossary` CLI command (TEDM2O-13).

### Changed
- Update the configuration description for generating reused concepts (TEDM2O-13).


## [3.1.0-rc.2] - 2025-11-20
### Changed
- Update documentation of the `issuedDate` parameter (TEDM2O-11).


## [3.1.0-rc.1] - 2025-10-15
### Added
- New category of transformation rules for JSON-LD context generation
  (TEDM2O-7).
- New _ReSpec documentation_ page for the ReSpec generation feature (TEDM2O-11).
- New section describing existing and new metadata stored in the `metadata.json`
  (TEDM2O-11).
- Description of a new `imports.xml` configuration file enabling fine-grained
  control of URIs included in `owl:imports` statements for each
  generated RDF artefact (TEDM2O-21).
- Description of a new `annotateShaclConceptsWithOntology` parameter, which
  enables the generation of rdfs:isDefinedBy statements in SHACL shapes
  (TEDM2O-18).
- Description of a new `nodeShapeURIsuffix` parameter, which specifies how URIs
  for SHACL node shapes are constructed (TEDM2O-19).

### Changed
- Updates on the _Configuration parameters_ page reflecting move of metadata
  from from `config-parameters.xml` to `metadata.json` file (TEDM2O-11).
- Transformation rules for cardinality constraints (TEDM2O-33).
- Description of the model2owl CLI for the import statements file (TEDM2O-21).

### Removed
- Documentation of the abandoned `R.18` transformation rule for disjointness
  among sibling classes in generalizations (TEDM2O-15).


## [3.0.0] — 2025-03-21
### Added
- Documentation of new transformation rules and conventions for controlled
  vocabularies ([Task 2: Export of controlled vocabulary
  restrictions](https://github.com/OP-TED/model2owl/issues/228)) by @gkostkowski
  in https://github.com/OP-TED/ted-model2owl-docs/pull/6
- Documentation of new transformation rules and conventions for tags and
  comments ([Task 3: Export of metadata about
  concepts](https://github.com/OP-TED/model2owl/issues/229)) by @gkostkowski in
  https://github.com/OP-TED/ted-model2owl-docs/pull/7
- User guide providing general instructions and documenting new features ([Task
  1: Status-based filtering](https://github.com/OP-TED/model2owl/issues/226),
  [Task 2: Export of controlled vocabulary
  restrictions](https://github.com/OP-TED/model2owl/issues/228), [Task 3: Export
  of metadata about concepts](https://github.com/OP-TED/model2owl/issues/229))
  by @Dragos0000 in https://github.com/OP-TED/ted-model2owl-docs/pull/9
- Documentation of conventions and checkers for property inheritance
  (https://github.com/OP-TED/model2owl/issues/205) by @gkostkowski in
  https://github.com/OP-TED/ted-model2owl-docs/pull/10


## [2.3.0-rc.1] — 2024-12-06
### Changed
- Cleaned-up the documentation structure
- Fixed documentation version
- Changed version number to correspond to the relevant [model2owl
  version](https://github.com/OP-TED/model2owl/releases/tag/2.3.0-rc.2)
