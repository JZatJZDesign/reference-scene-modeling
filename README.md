# Reference Scene Modeling

A reusable agent skill for reconstructing 3D scenes from reference images, with a focus on Blender, interiors, furniture, and the small details that make a scene convincing.

**Understand the structure. Build in stages. Compare, correct, and verify.**

This is a set of instructions and supporting resources for an AI agent. It is not a Blender add-on, an MCP server, or a one-click image-to-3D generator. It guides how the agent analyzes a reference, asks questions, models the scene, and checks its own work.

## Why this skill exists

This workflow grew out of a kitchen modeling experiment using a reference image with many small objects, detailed furniture, and different materials.

The GPT-6 reconstruction captured many aspects of the scene, but it was still far from perfect.

Iteration helped. Asking the agent to compare its render against the input image, identify mismatches, and fix them improved the scene. However, some mistakes were not discovered by the AI itself and had to be pointed out by the user.

The chair was a particularly useful lesson. Its three-dimensional structure was difficult to understand from the full kitchen image. Providing a separate chair image on a white background made the frame, connections, and upholstery much easier to interpret.

The result still had limitations, but it improved through this feedback loop. This skill packages those lessons into a reusable process, so that clarification, isolated-object analysis, and verification become part of the workflow instead of repeated manual reminders.

The results reflect additional references, iterations, and human feedback. The skill is not tied to a specific GPT version and cannot guarantee a particular level of improvement.

## What it helps with

- Reconstructing rooms and assembled scenes from photographs or renders.
- Estimating plausible dimensions while clearly labeling assumptions.
- Understanding complex furniture before duplicating it throughout a scene.
- Checking alignment, clearances, support, proportions, and object relationships.
- Comparing a Blender render with the reference and making targeted corrections.
- Preserving earlier fixes when later revisions affect related objects.

It is not intended for image-only retouching or unrelated animation work.

## The workflow

1. **Analyze the whole reference.** Separate visible facts, user-confirmed constraints, and inferred dimensions or hidden geometry.
2. **Clarify the important uncertainties.** Ask one focused round of questions when an ambiguity could change the structure. Request separate product images or additional views when useful.
3. **Isolate complex objects.** Crop the original reference, remove the background when suitable tools are available, and retain the original crop for comparison. Check that thin parts and openings were not erased. A generated view is not evidence of the actual structure.
4. **Define dimensions and relationships.** Record units, axes, heights, clearances, aligned edges, and supporting connections. Typical real-world dimensions are starting estimates, not measurements recovered from a single image.
5. **Build from large forms to details.** Establish layout and camera, validate frames and connections, then add curved surfaces, materials, tableware, seams, and small props. Validate one complex asset before making copies.
6. **Compare from multiple views.** Use the reference camera for resemblance, top or orthographic views for layout, and close-ups for joints and edges. Fix structural errors before increasing render quality.
7. **Recheck, save, and deliver.** Verify that new fixes preserve earlier constraints. Save the latest model and produce matching renders. State what remains uncertain.

## Requirements

- An image-capable AI agent that supports skills and can read the supplied references.
- Blender and a separately installed, working Blender MCP integration for MCP-driven modeling.
- Reference images; optional product photos, drawings, or known dimensions improve the evidence available.

This repository does not install Blender, configure an MCP connection, or include model weights. Its instructions tell the agent to check the available tools and connection rather than assume a server or port. If an operation is unavailable, the agent should explain the limitation instead of claiming it has completed the work.

## Install in Codex

Ask Codex:

```text
$skill-installer Install the skill from:
https://github.com/JZatJZDesign/reference-scene-modeling
The SKILL.md file is at the repository root.
```

Alternatively, download this repository and place its contents in a folder named `reference-scene-modeling` under either:

- Your project's `.agents/skills/` directory, for project-specific use.
- Your home directory's `.agents/skills/` directory, for personal use across projects.

Keep `SKILL.md`, `agents/`, `assets/`, and `references/` together. If the skill does not appear, restart Codex. See the [official skill documentation](https://learn.chatgpt.com/docs/build-skills) for discovery and installation details.

## Example prompts

### Build a scene

```text
Use $reference-scene-modeling to reconstruct this kitchen in Blender via MCP.
Include the furniture, appliances, tableware, and visible small props.
Infer plausible dimensions, but label assumptions. Ask one focused round of
questions about important structural ambiguities. Analyze and validate the
chair separately before duplicating it. Preserve the existing project and
save this reconstruction as a new revision.
```

### Review without changing the model

```text
Use $reference-scene-modeling to compare the current render with the reference.
Check structure, proportions, layout, materials, and missing details.
Distinguish camera differences from geometry errors and prioritize the findings.
Analysis only: do not modify the Blender scene.
```

### Make targeted corrections

```text
Use $reference-scene-modeling to fix the confirmed mismatches:
the window needs a recessed reveal, all three pendant shades should share
the same bottom height, and the table and island must remain aligned.
Check the affected clearances and earlier fixes, save a new revision,
and render an updated reference-matched view.
```

## Repository contents

| File | Purpose |
| --- | --- |
| [SKILL.md](SKILL.md) | Main workflow and decision rules. |
| [agents/openai.yaml](agents/openai.yaml) | Codex display metadata and invocation settings. |
| [references/blender-mcp.md](references/blender-mcp.md) | Blender implementation, safe execution, and verification guidance. |
| [references/complex-objects.md](references/complex-objects.md) | Isolated reference analysis and structural checks for complex assets. |
| [assets/scene-workbook.md](assets/scene-workbook.md) | Template for evidence, dimensions, constraints, revisions, and delivery checks. |

## Limitations and practical advice

A single image cannot reliably reveal exact dimensions, hidden surfaces, or every connection. Camera perspective, lighting, and materials can also make correct geometry look different. Attractive renders are not proof of structural correctness.

For better results, provide the highest-quality reference you have, add known dimensions, and supply standalone images for difficult products. Point out mistakes the agent misses. Review a complex prototype before approving many copies, and use inexpensive test renders before committing to a long final render.

This remains a human-guided workflow, not guaranteed automatic reconstruction or engineering validation. The skill is available to download at no charge; the AI models and external tools used with it may have their own costs.
