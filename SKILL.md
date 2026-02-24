---
name: turf-skills
description: |
  Use when performing spatial analysis, geometric calculations, or GeoJSON operations.
  Supports measurement (distance, area, length), spatial queries (point-in-polygon, contains, intersects),
  transformations (buffer, union, intersect, simplify), data creation, interpolation/grids, and clustering.

  当用户需要进行空间分析、几何计算或 GeoJSON 操作时使用。支持测量（距离、面积、长度）、
  空间查询（点在多边形内、包含、相交）、变换（缓冲区、合并、求交、简化）、数据创建、插值/网格和聚类。

  Triggers: "calculate distance", "point in polygon", "buffer", "spatial analysis", "GeoJSON", "convex hull", "voronoi", "clustering"
  触发词: "计算距离", "面积计算", "点在多边形内", "缓冲区", "空间分析", "凸包", "泰森多边形", "聚类分析"
license: MIT
metadata:
  author: zhangyuting
  version: "1.0.0"
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

| Action | Description | Required | Optional |
|--------|-------------|----------|----------|
| `distance` | Distance between two points 两点距离 | input, input2 | units |
| `area` | Area of polygon 多边形面积(m²) | input | |
| `length` | Length of line 线长度 | input | units |
| `bearing` | Bearing between points 方位角 | input, input2 | |
| `destination` | Point at distance+bearing 目标点 | input | distance, direction, units |
| `midpoint` | Midpoint of two points 中点 | input, input2 | |
| `center` | Center of features 中心点 | input | |
| `centroid` | Centroid 质心 | input | |
| `centerOfMass` | Center of mass 重心 | input | |
| `along` | Point along line 沿线取点 | input | distance, units |
| `bbox` | Bounding box 边界框 | input | |
| `bboxPolygon` | Bbox as polygon 边界框多边形 | input or bbox | |
| `envelope` | Envelope 包络矩形 | input | |

### Query 空间查询

| Action | Description | Required | Optional |
|--------|-------------|----------|----------|
| `booleanPointInPolygon` | Point in polygon 点在多边形内 | input(point), input2(polygon) | |
| `booleanContains` | Feature contains another 包含 | input, input2 | |
| `booleanCrosses` | Features cross 交叉 | input, input2 | |
| `booleanDisjoint` | Features disjoint 不相交 | input, input2 | |
| `booleanEqual` | Features equal 相等 | input, input2 | |
| `booleanIntersects` | Features intersect 相交 | input, input2 | |
| `booleanOverlap` | Features overlap 重叠 | input, input2 | |
| `booleanWithin` | Feature within another 在内部 | input, input2 | |
| `booleanParallel` | Lines parallel 平行 | input, input2 | |
| `booleanPointOnLine` | Point on line 点在线上 | input(point), input2(line) | |
| `nearestPoint` | Nearest point in collection 最近点 | input(point), input2(FC) | |

### Transformation 变换

| Action | Description | Required | Optional |
|--------|-------------|----------|----------|
| `buffer` | Buffer zone 缓冲区 | input | radius, units |
| `union` | Union polygons 合并 | input, input2 | |
| `intersect` | Intersect polygons 求交 | input, input2 | |
| `difference` | Difference polygons 求差 | input, input2 | |
| `simplify` | Simplify geometry 简化 | input | tolerance |
| `convex` | Convex hull 凸包 | input | |
| `concave` | Concave hull 凹包 | input | maxEdge, units |
| `dissolve` | Dissolve polygons 融合 | input(FC) | propertyName |
| `voronoi` | Voronoi diagram 泰森多边形 | input(points) | bbox |
| `tin` | TIN 不规则三角网 | input(points) | propertyName |
| `bezierSpline` | Bezier spline 贝塞尔曲线 | input(line) | resolution, sharpness |
| `transformRotate` | Rotate 旋转 | input | angle |
| `transformScale` | Scale 缩放 | input | factor |
| `transformTranslate` | Translate 平移 | input | distance, direction, units |

### Helpers 创建

| Action | Description | Required | Optional |
|--------|-------------|----------|----------|
| `point` | Create point 创建点 | coordinates | properties |
| `lineString` | Create line 创建线 | coordinates | properties |
| `polygon` | Create polygon 创建面 | coordinates | properties |
| `multiPoint` | Create MultiPoint | coordinates | properties |
| `multiLineString` | Create MultiLineString | coordinates | properties |
| `multiPolygon` | Create MultiPolygon | coordinates | properties |
| `randomPoint` | Random points 随机点 | | count, bbox |
| `randomLineString` | Random lines 随机线 | | count, bbox |
| `randomPolygon` | Random polygons 随机面 | | count, bbox |

### Interpolation 插值/网格

| Action | Description | Required | Optional |
|--------|-------------|----------|----------|
| `interpolate` | IDW interpolation 反距离加权插值 | input(points) | cellSide, gridType, propertyName, units |
| `isobands` | Isobands 等值面 | input(points) | breaks, propertyName |
| `isolines` | Isolines 等值线 | input(points) | breaks, propertyName |
| `hexGrid` | Hex grid 六边形网格 | bbox, cellSide | units |
| `pointGrid` | Point grid 点网格 | bbox, cellSide | units |
| `squareGrid` | Square grid 方形网格 | bbox, cellSide | units |
| `triangleGrid` | Triangle grid 三角网格 | bbox, cellSide | units |

### Clustering 聚类

| Action | Description | Required | Optional |
|--------|-------------|----------|----------|
| `clustersKmeans` | K-means clustering K均值聚类 | input(points FC) | numberOfClusters |
| `clustersDbscan` | DBSCAN clustering 密度聚类 | input(points FC) | maxDistance, units, minPoints |

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
