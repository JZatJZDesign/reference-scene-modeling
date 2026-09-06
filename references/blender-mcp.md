# Blender MCP: Implementation and Verifiable Checks

Read only when working in Blender or through Blender MCP. Discover the actual available tools and parameters; do not assume fixed server names, ports, or installation paths.

## Before modifying the scene

- Inspect the connection, current `.blend` path, active scene, units, collections, camera, and unsaved user work. If no connection is available, report that honestly instead of claiming a successful modification.
- If a tool requires the user's verbatim prompt, pass the current request unchanged rather than substituting a self-written subtask.
- When the user explicitly requests MCP, use the available MCP connection. Disclose missing capabilities and obtain any necessary authorization for an alternative workflow.
- Preserve important earlier revisions under separate filenames. Save again after modifying the model; a pre-edit save does not mean the new result has been saved.

## Implement in bounded parts

- Read objects and relationships first, then work in small batches by space, assembly, asset, or lighting group. Target verified names or collections rather than broadly deleting every object.
- Create independent master assemblies and have scene instances reference shared data. Preserve materials, modifiers, dependent transforms, and existing constraints. Do not move only a tabletop while leaving its tableware, supports, or associated chairs behind.
- Distinguish local geometry, world geometry, parents, and collection instances. An object's origin alone does not establish its spatial extent or membership.
- Respect MCP safety mode. Rewrite rejected code within permitted capabilities; do not bypass the sandbox or ask the user to disable safeguards for routine work.
- Prefer the data API for data-only changes. Operators require a suitable active object, mode, and view layer. Objects present only in an instanced collection may need a temporary valid scene link for an operator; remove that temporary link afterward.

## Dimension and transform pitfalls

Update the dependency graph after changing objects or parents before reading final world-space geometry. Repeated per-component assignments to `dimensions` may recalculate scale from stale evaluated dimensions and undo earlier adjustments. Prefer setting the complete dimensions tuple, then updating and verifying it. For rotated objects or modifiers, also inspect evaluated geometry.

Read-only bounding-box example; replace the placeholder with a verified object name before use:

```python
import bpy
from mathutils import Vector

bpy.context.view_layer.update()
depsgraph = bpy.context.evaluated_depsgraph_get()
obj = bpy.data.objects['VERIFIED_OBJECT_NAME']
evaluated = obj.evaluated_get(depsgraph)
corners = [evaluated.matrix_world @ Vector(p) for p in evaluated.bound_box]
bounds = [(min(p[i] for p in corners), max(p[i] for p in corners)) for i in range(3)]
print(obj.name, bounds)
```

This example is for ordinary objects with valid bounding boxes, not collection-instance Empties. For collection instances, apply the appropriate instance world transforms to component geometry, or aggregate bounds from evaluated dependency-graph instances.

## Choose meaningful checks

| Relationship | Suitable verification |
|---|---|
| Shared axis and aligned front/rear edges | Compare world-space centers and both boundaries along a common axis; check matching depth |
| Equal-height lamps | Compare the same defined datum, such as the shade bottom, not pixel heights in a perspective image |
| Wall clearance | Compare the countertop boundary with actual wall, sill, and trim protrusions along the agreed direction |
| Floor-length frames and chair feet | Compare against the finished floor surface rather than assuming world Z = 0 |
| Suspected object intersections | Use bounding boxes for candidate screening, then inspect close-ups, sections, or actual meshes |
| Consistent instances | Check shared master references and intended position, orientation, and scale |

An axis-aligned bounding box does not measure true shortest clearance for rotated objects. For precise spacing, use relevant faces, a defined direction, or mesh distances. Intended contact or embedding at structural joints is not automatically an error; exposed coplanar overlaps and unintended penetrations should be removed.

## Render troubleshooting and completion

Low-resolution, low-sample renders, isolated assets, and orthographic checks are often more informative than repeated full-scene renders. Change one diagnostically useful variable at a time and inspect the result.

- **Black patches or flicker:** inspect coplanar overlaps, normals, duplicate objects, and material slots.
- **White spikes or open gaps:** inspect underside caps, subdivided n-gons, missing supports, and visible background before assuming a shading problem.
- **Metallic-looking or disappearing glass:** inspect thickness, normals, internal occlusion, refraction, and environment. Do not keep adding transparency to conceal geometry defects.
- **Boolean or subdivision results:** check modifier order and final surfaces. Operator success does not mean geometric validation passed.

After the last edit: update the dependency graph → verify affected constraints → save the native project → render affected views → inspect the actual output. Distinguish scene configuration, rendering in progress, and a completed output file. Saving a revision or using a separate inspection scene must not leave the user's intended main scene disrupted.
