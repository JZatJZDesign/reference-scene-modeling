---
name: reference-scene-modeling
description: "Build, revise, or compare reference-image-driven 3D scenes, especially interiors and furniture assemblies in Blender. Use for reference reconstruction, model-to-image comparison, spatial layout, and complex furniture corrections. Resolve uncertain structure, constrain dimensions and relationships, and validate isolated assets before scene assembly. Not for image-only retouching or unrelated animation work."
---

# Reference-Driven Scene Modeling

Understand structure and spatial relationships before building a credible, editable, verifiable reconstruction. Object count, subdivision levels, and attractive wide shots are not evidence of structural correctness.

## Establish the current scope

- For analysis, comparison, inspection, or status requests, perform relevant read-only checks and explain findings with evidence. Do not automatically modify the model.
- For modeling, revision, repair, or "analyze and directly fix" requests, implement the authorized changes, validate, and save. Do not substitute analysis for requested modifications.
- Respect the user's chosen software and connection method. Before using Blender MCP, read [Blender implementation and verification](references/blender-mcp.md). Do not silently substitute a generated look-alike image.
- Preserve the existing project, confirmed relationships, and unrelated content. Inspect the current file, scene, and collections first; save major rebuilds as separate revisions.

## 1. Analyze the whole image and consolidate key questions

Decompose the reference into the room or site envelope, fixed equipment, complex furniture, repeated assets, and small props. Distinguish:

- **Visible facts:** clear silhouettes, seams, occlusions, connections, and counts.
- **User-confirmed constraints:** shared axes, ground contact, equal heights, gaps, and structural types explicitly identified by the user.
- **Inferences:** hidden backs, absolute dimensions, internal connections, and material thicknesses. Record their basis and confidence.

When ambiguity materially affects structure or layout, ask one concise round of clarification, prioritizing the one to three questions most likely to prevent rework. Identify the specific region, plausible interpretations, and consequences rather than asking vaguely for more requirements. Ask whether standalone product photos, side or rear views, dimension drawings, or product links are available for complex objects.

If an essential choice is missing, pause finalizing that component while continuing independent, well-understood parts. When the user authorizes inference or direct revision, use reasonable, labeled assumptions without repeatedly requesting information they have declined to provide. Simple, unambiguous corrections do not require another confirmation round.

## 2. Analyze complex assets separately

For chairs, unusual fixtures, equipment, or curved products, first read [Complex asset analysis](references/complex-objects.md). Crop the object from the original image, remove the background, and retain the corresponding original region. Reanalyze silhouette, occlusion, support, and connections.

A clearer standalone reference supplied later should update the interpretation of that object, not automatically override unrelated, confirmed scene constraints.

Do not conceal uncertain structure with additional detail. Validate one prototype before duplication or instancing. When needed, ask the user to confirm a prototype close-up rather than discovering the wrong structural type only after the full scene has rendered.

## 3. Express dimensions and relationships as constraints

Use consistent coordinates and units, with a short project record. For new scenes or major revisions, copy the [Scene workbook template](assets/scene-workbook.md) into the project directory. For small corrections, record only affected items.

- Prefer user-provided dimensions and credible product specifications. Treat typical ergonomic dimensions as labeled initial estimates, not measurements recovered from the photograph.
- Define testable conditions and project-appropriate tolerances for axes, aligned edges, heights, clearances, layers, supports, counts, and symmetry.
- A shared centerline does not imply aligned edges: compare width or depth and both boundaries as well as centers.
- Measure clearance from the most protruding components, such as sills, handles, eaves, or upholstery edges, not merely walls or object origins.
- Do not turn one kitchen's dimensions, cabinet styles, or chair structure into defaults for every scene.

## 4. Build and review in stages

Apply these checkpoints proportionally to the task; user approval is not required at every stage.

1. **Space and primary forms:** establish silhouettes, masses, floor levels, wall openings, and basic layout before adding clutter.
2. **Camera and proportions:** match the reference using long straight edges, verticals, known dimensions, and occlusions. Use orthographic checks to distinguish perspective differences from actual geometry errors.
3. **Asset structure:** build the supporting frame, connections, and thicknesses before curved surfaces and upholstery. Establish coherent volumes and connections before subdivision.
4. **Assembly:** verify instance orientation, ground contact, component joints, opening space, and clearances. Move dependent objects with their assemblies without breaking confirmed constraints.
5. **Details and appearance:** add tableware, seams, fasteners, textures, glass, and lighting once structure is stable.
6. **Evidence review:** use the reference camera for resemblance, top or orthographic views for layout, and close-ups for joints and edges. Correct obvious problems before increasing render quality.

For black patches, white spikes, or abnormal glass, first inspect overlapping faces, normals, thickness, occlusion, missing supports, and material assignment. Isolate variables in inexpensive tests instead of repeatedly adjusting shaders without a diagnosis. If the same correction keeps failing, revisit structural assumptions and reference evidence rather than adding detail to an incorrect framework.

## 5. Regress, save, and deliver

- Check the current correction first, then recheck affected earlier constraints. Later edits must not silently break confirmed lamp heights or table-island alignment, for example.
- Combine geometric measurements with visual inspection. Bounding-box overlap identifies candidates, not proven intersections; absence of a visible problem in a photograph does not prove collision-free geometry.
- Save again after the final geometry or material change and rerender affected views when needed. Do not deliver an old image alongside a newer model as though they match.
- Deliver the native project, current render, and necessary verification close-ups. Identify inferred details and unresolved limitations; do not claim measurement-grade accuracy or engineering safety certification.
- Tie status wording to evidence: **analyzed / modified / validated / saved / rendered**. If only analysis was performed, explicitly state that the model has not been changed.
