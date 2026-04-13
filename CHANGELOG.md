# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [1.0.3] - 2026-04-13

### Changed

- Optimized `SKILL.md` frontmatter: shortened `description` to ~160 characters to comply with Agent Skill specification
- Replaced all direct `turf-skills` CLI examples with `npx turf-skills` for better `npx skills` ecosystem compatibility
- Updated `README.md`, `README.zh-CN.md`, and `INSTALL.md` with `npx skills` installation instructions
- Bumped package version to 1.0.3

## [1.0.0] - 2025-03-20

### Added

- Initial release of turf-skills
- Support for 60+ Turf.js operations across 6 categories:
  - Measurement: distance, area, length, bearing, destination, midpoint, center, centroid, centerOfMass, along, bbox, bboxPolygon, envelope
  - Query: booleanPointInPolygon, booleanContains, booleanCrosses, booleanDisjoint, booleanEqual, booleanIntersects, booleanOverlap, booleanWithin, booleanParallel, booleanPointOnLine, nearestPoint
  - Transformation: buffer, union, intersect, difference, simplify, convex, concave, dissolve, voronoi, tin, bezierSpline, transformRotate, transformScale, transformTranslate
  - Helpers: point, lineString, polygon, multiPoint, multiLineString, multiPolygon, featureCollection, randomPoint, randomLineString, randomPolygon
  - Interpolation: interpolate, isobands, isolines, hexGrid, pointGrid, squareGrid, triangleGrid
  - Clustering: clustersKmeans, clustersDbscan
- CLI interface with comprehensive options
- Bilingual documentation (English and Chinese)
- 32 test cases with 100% pass rate
- File input/output support
- Unit conversion (kilometers, miles, meters)

[Unreleased]: https://github.com/zhyt1985/turf-skills/compare/v1.0.3...HEAD
[1.0.3]: https://github.com/zhyt1985/turf-skills/releases/tag/v1.0.3
[1.0.0]: https://github.com/zhyt1985/turf-skills/releases/tag/v1.0.0
