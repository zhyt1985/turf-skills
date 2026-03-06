---
name: turf-skills
description: |
  Automatically invoke for ANY spatial analysis, geospatial operations, or GeoJSON tasks.

  Supports 60+ operations across 6 categories:
  - Measurement: distance, area, length, bearing, midpoint, center, centroid, along, bbox
  - Query: point-in-polygon, contains, intersects, overlaps, within, disjoint, nearest, crosses, parallel
  - Transformation: buffer, union, intersect, difference, simplify, convex/concave hull, dissolve, voronoi
  - Data Creation: points, lines, polygons, random features, feature collections
  - Grids: hex, square, triangle grids with custom cell sizes
  - Analysis: interpolation (IDW), isobands, isolines, clustering (K-means, DBSCAN)

  用于任何空间分析、地理操作或 GeoJSON 任务，自动触发。
  支持 60+ 操作：测量、空间查询、变换、数据创建、网格生成、聚类分析。

  Trigger Examples:
  - "Calculate distance between coordinates"
  - "Find area of polygon"
  - "Check if point is inside polygon"
  - "Create a 5km buffer around this location"
  - "Generate hex grid for this area"
  - "Compute convex hull of these points"
  - "Cluster these points into groups"
  - "Interpolate values from these sample points"
  - "Find nearest point to location"
  - "Simplify this geometry"
  - "Union/intersect/difference of polygons"
  - "Rotate/scale/translate geometry"

  触发示例：
  - "计算两个坐标之间的距离"
  - "计算多边形面积"
  - "检查点是否在多边形内"
  - "创建5公里缓冲区"
  - "生成六边形网格"
  - "计算点的凸包"
  - "对点进行聚类"
  - "从样本点插值"
  - "查找最近点"
  - "简化几何图形"
  - "合并/相交/差集多边形"
  - "旋转/缩放/平移几何"

  Common keywords: GeoJSON, coordinates, spatial, gis, geography, map, geometry, polygon, point, line
  常见关键词: GeoJSON、坐标、空间、地理、地图、几何、多边形、点、线
license: MIT
metadata:
  author: zhangyuting
  version: '1.0.0'
  project: https://github.com/zhyt1985/turf-skills
compatibility: Node.js >= 16
---

# turf-skills

Turf.js spatial analysis skill for Claude Code.

## Usage

```bash
turf-skills --action <name> [options]
```

## Actions

### Measurement 测量

| Action         | Description                          | Required      | Optional                   |
| -------------- | ------------------------------------ | ------------- | -------------------------- |
| `distance`     | Distance between two points 两点距离 | input, input2 | units                      |
| `area`         | Area of polygon 多边形面积(m²)       | input         |                            |
| `length`       | Length of line 线长度                | input         | units                      |
| `bearing`      | Bearing between points 方位角        | input, input2 |                            |
| `destination`  | Point at distance+bearing 目标点     | input         | distance, direction, units |
| `midpoint`     | Midpoint of two points 中点          | input, input2 |                            |
| `center`       | Center of features 中心点            | input         |                            |
| `centroid`     | Centroid 质心                        | input         |                            |
| `centerOfMass` | Center of mass 重心                  | input         |                            |
| `along`        | Point along line 沿线取点            | input         | distance, units            |
| `bbox`         | Bounding box 边界框                  | input         |                            |
| `bboxPolygon`  | Bbox as polygon 边界框多边形         | input or bbox |                            |
| `envelope`     | Envelope 包络矩形                    | input         |                            |

### Query 空间查询

| Action                  | Description                        | Required                      | Optional |
| ----------------------- | ---------------------------------- | ----------------------------- | -------- |
| `booleanPointInPolygon` | Point in polygon 点在多边形内      | input(point), input2(polygon) |          |
| `booleanContains`       | Feature contains another 包含      | input, input2                 |          |
| `booleanCrosses`        | Features cross 交叉                | input, input2                 |          |
| `booleanDisjoint`       | Features disjoint 不相交           | input, input2                 |          |
| `booleanEqual`          | Features equal 相等                | input, input2                 |          |
| `booleanIntersects`     | Features intersect 相交            | input, input2                 |          |
| `booleanOverlap`        | Features overlap 重叠              | input, input2                 |          |
| `booleanWithin`         | Feature within another 在内部      | input, input2                 |          |
| `booleanParallel`       | Lines parallel 平行                | input, input2                 |          |
| `booleanPointOnLine`    | Point on line 点在线上             | input(point), input2(line)    |          |
| `nearestPoint`          | Nearest point in collection 最近点 | input(point), input2(FC)      |          |

### Transformation 变换

| Action               | Description                | Required      | Optional                   |
| -------------------- | -------------------------- | ------------- | -------------------------- |
| `buffer`             | Buffer zone 缓冲区         | input         | radius, units              |
| `union`              | Union polygons 合并        | input, input2 |                            |
| `intersect`          | Intersect polygons 求交    | input, input2 |                            |
| `difference`         | Difference polygons 求差   | input, input2 |                            |
| `simplify`           | Simplify geometry 简化     | input         | tolerance                  |
| `convex`             | Convex hull 凸包           | input         |                            |
| `concave`            | Concave hull 凹包          | input         | maxEdge, units             |
| `dissolve`           | Dissolve polygons 融合     | input(FC)     | propertyName               |
| `voronoi`            | Voronoi diagram 泰森多边形 | input(points) | bbox                       |
| `tin`                | TIN 不规则三角网           | input(points) | propertyName               |
| `bezierSpline`       | Bezier spline 贝塞尔曲线   | input(line)   | resolution, sharpness      |
| `transformRotate`    | Rotate 旋转                | input         | angle                      |
| `transformScale`     | Scale 缩放                 | input         | factor                     |
| `transformTranslate` | Translate 平移             | input         | distance, direction, units |

### Helpers 创建

| Action             | Description            | Required    | Optional    |
| ------------------ | ---------------------- | ----------- | ----------- |
| `point`            | Create point 创建点    | coordinates | properties  |
| `lineString`       | Create line 创建线     | coordinates | properties  |
| `polygon`          | Create polygon 创建面  | coordinates | properties  |
| `multiPoint`       | Create MultiPoint      | coordinates | properties  |
| `multiLineString`  | Create MultiLineString | coordinates | properties  |
| `multiPolygon`     | Create MultiPolygon    | coordinates | properties  |
| `randomPoint`      | Random points 随机点   |             | count, bbox |
| `randomLineString` | Random lines 随机线    |             | count, bbox |
| `randomPolygon`    | Random polygons 随机面 |             | count, bbox |

### Interpolation 插值/网格

| Action         | Description                      | Required       | Optional                                |
| -------------- | -------------------------------- | -------------- | --------------------------------------- |
| `interpolate`  | IDW interpolation 反距离加权插值 | input(points)  | cellSide, gridType, propertyName, units |
| `isobands`     | Isobands 等值面                  | input(points)  | breaks, propertyName                    |
| `isolines`     | Isolines 等值线                  | input(points)  | breaks, propertyName                    |
| `hexGrid`      | Hex grid 六边形网格              | bbox, cellSide | units                                   |
| `pointGrid`    | Point grid 点网格                | bbox, cellSide | units                                   |
| `squareGrid`   | Square grid 方形网格             | bbox, cellSide | units                                   |
| `triangleGrid` | Triangle grid 三角网格           | bbox, cellSide | units                                   |

### Clustering 聚类

| Action           | Description                  | Required         | Optional                      |
| ---------------- | ---------------------------- | ---------------- | ----------------------------- |
| `clustersKmeans` | K-means clustering K均值聚类 | input(points FC) | numberOfClusters              |
| `clustersDbscan` | DBSCAN clustering 密度聚类   | input(points FC) | maxDistance, units, minPoints |

## Examples

### Calculate distance 计算距离

```bash
turf-skills --action distance \
  --input '{"type":"Point","coordinates":[120,30]}' \
  --input2 '{"type":"Point","coordinates":[121,31]}' \
  --units kilometers
```

### Point in polygon 点在多边形内

```bash
turf-skills --action booleanPointInPolygon \
  --input '{"type":"Point","coordinates":[120.5,30.5]}' \
  --input2 '{"type":"Polygon","coordinates":[[[120,30],[121,30],[121,31],[120,31],[120,30]]]}'
```

### Buffer 缓冲区

```bash
turf-skills --action buffer \
  --input '{"type":"Point","coordinates":[120,30]}' \
  --radius 5 --units kilometers
```

### Read from file 从文件读取

```bash
turf-skills --action area --file polygon.geojson
turf-skills --action booleanContains --file polygon.geojson --file2 point.geojson
```

### Output to file 输出到文件

```bash
turf-skills --action buffer --file point.geojson --radius 10 --output result.geojson
```

### Create geometry 创建几何

```bash
turf-skills --action point --coordinates '[120,30]' --properties '{"name":"test"}'
turf-skills --action randomPoint --count 100 --bbox '[120,30,121,31]'
```

### Grid generation 网格生成

```bash
turf-skills --action hexGrid --bbox '[120,30,121,31]' --cellSide 5 --units kilometers
```

### Clustering 聚类分析

```bash
turf-skills --action clustersKmeans --file points.geojson --numberOfClusters 5
turf-skills --action clustersDbscan --file points.geojson --maxDistance 1 --minPoints 3
```

## Natural Language Patterns

### Common Queries 常见查询

| Query Pattern                          | Action                                            | Example                                            |
| -------------------------------------- | ------------------------------------------------- | -------------------------------------------------- |
| "distance between [coordinates]"       | distance                                          | "Calculate distance between [120,30] and [121,31]" |
| "area of [polygon]"                    | area                                              | "Find area of this polygon"                        |
| "length of [line]"                     | length                                            | "Calculate length of this line in km"              |
| "is [point] inside [polygon]"          | booleanPointInPolygon                             | "Is this point inside the polygon?"                |
| "buffer [radius] km/mi around [point]" | buffer                                            | "Create a 5km buffer around this point"            |
| "convex hull of [points]"              | convex                                            | "Compute convex hull of these points"              |
| "cluster points into [n] groups"       | clustersKmeans                                    | "Cluster these points into 5 groups"               |
| "nearest point to [location]"          | nearestPoint                                      | "Find nearest point to [120,30]"                   |
| "simplify geometry"                    | simplify                                          | "Simplify this geometry"                           |
| "union/intersect/difference"           | union/intersect/difference                        | "Union these two polygons"                         |
| "generate hex/square/triangle grid"    | hexGrid/squareGrid/triangleGrid                   | "Generate hex grid for this area"                  |
| "rotate/scale/translate"               | transformRotate/transformScale/transformTranslate | "Rotate this polygon by 45 degrees"                |

### Chinese Query Patterns 中文查询模式

| 查询模式           | 操作                                              | 示例                       |
| ------------------ | ------------------------------------------------- | -------------------------- |
| "计算...的距离"    | distance                                          | "计算北京和上海的距离"     |
| "计算...的面积"    | area                                              | "计算这个多边形的面积"     |
| "点是否在多边形内" | booleanPointInPolygon                             | "天安门是否在五环内？"     |
| "创建...缓冲区"    | buffer                                            | "创建5公里缓冲区"          |
| "计算凸包"         | convex                                            | "计算这些点的凸包"         |
| "聚类分析"         | clustersKmeans/clustersDbscan                     | "对这些点进行聚类"         |
| "查找最近点"       | nearestPoint                                      | "查找距离[120,30]最近的点" |
| "生成网格"         | hexGrid/squareGrid                                | "生成六边形网格"           |
| "旋转/缩放/平移"   | transformRotate/transformScale/transformTranslate | "旋转多边形45度"           |

### Real-World Scenarios 实际场景

```bash
# Beijing to Shanghai distance
turf-skills --action distance \
  --input '{"type":"Point","coordinates":[116.397428,39.90923]}' \
  --input2 '{"type":"Point","coordinates":[121.473701,31.230416]}' \
  --units kilometers

# 5km buffer around a location
turf-skills --action buffer \
  --input '{"type":"Point","coordinates":[116.397428,39.90923]}' \
  --radius 5 --units kilometers

# Point in polygon check
turf-skills --action booleanPointInPolygon \
  --input '{"type":"Point","coordinates":[116.397428,39.90923]}' \
  --input2 '{"type":"Polygon","coordinates":[[[116.1,39.7],[116.8,39.7],[116.8,40.1],[116.1,40.1],[116.1,39.7]]]}'

# Generate hex grid for a region
turf-skills --action hexGrid --bbox '[116,39,117,40]' --cellSide 10 --units kilometers

# K-means clustering
turf-skills --action clustersKmeans --file points.geojson --numberOfClusters 3
```
