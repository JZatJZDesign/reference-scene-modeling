# Complex Assets: Cropping, Background Removal, and Structural Reasoning

Read this when the three-dimensional structure of furniture, equipment, or a curved product is difficult to infer from a scene image.

## Prepare the evidence

1. Prefer a standalone product reference; use available side views, rear views, dimension drawings, or model identifiers. Do not ask again for information already supplied.
2. Crop the target from the original scene image, keeping a small contextual margin to interpret occlusions. Preserve the original image.
3. Remove the background with tools permitted in the current environment, following their tool and skill instructions. Isolate the existing object rather than regenerating, inventing, or beautifying its structure. If suitable tools are unavailable, disclose the limitation and continue with the original crop.
4. Compare the cutout against the original region. Check for deleted thin legs, glass, openings, and shadow boundaries, or incorrectly reconstructed edges. Generative output, enhanced details, and generated alternative views are not independent structural evidence.
5. A standalone image may show another model in the same range or merely a style reference. Check consequential differences and clarify if they change the modeling target. If the user explicitly requests revision to match the new image, follow it while preserving unrelated scene constraints.

## Analyze in this order

- **Silhouette and negative space:** examine gaps between legs, hollow supports, openings, and thickness changes, not just the outer contour.
- **Connection topology:** map component connections, such as "front leg → top bridge → rear leg" or "cushion → support panel → crossbeam → side frame." Derive these relationships from the reference rather than assuming a furniture construction.
- **Continuous members:** distinguish continuous legs and bridging members from component seams, stitching, and occlusion boundaries.
- **Surfaces and coverings:** distinguish timber frames, hard shells, upholstery, housings, and glass. Upholstery needs volume, thickness, edge treatment, and support; it is not simply a bent flat sheet.
- **Scale and visibility:** select a few dimensional anchors. Record directly visible evidence, user confirmation, and inferred hidden structure separately.

Photographs alone cannot establish real load-bearing safety. Structural reasoning here supports plausible model connections, not furniture manufacturing or engineering certification.

## Prototype checkpoint

Inspect the isolated prototype for:

- Consistent front, rear, and side silhouettes; inferred rear geometry must not contradict visible features.
- Actual connections between beams, legs, top bridges, and support panels. Distinguish intended assembly contact from accidental penetration.
- Upholstery or shells protruding through frames, floating, or blocking openings that should remain visible.
- Feet resting on the actual finished floor; structural side frames must not become merely attached decoration.
- Surface artifacts caused by coplanar overlaps, incorrect normals, or missing underside geometry rather than materials.

After validation, instance one master assembly. Change only placement, orientation, and explicitly required variants. Revise the master and recheck all instances rather than independently rebuilding four approximately matching chairs.

Present the prototype with simple materials and lighting that expose its connections. Matching viewpoints and framing make comparisons more useful. If the reference is perspective, do not attribute every apparent proportion difference in an orthographic render to faulty geometry.
