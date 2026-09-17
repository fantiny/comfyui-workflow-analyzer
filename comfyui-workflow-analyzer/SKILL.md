---
name: comfyui-workflow-analyzer
description: "Create business-oriented learning documentation for ComfyUI workflows, explaining the user goal, functional subflows, node combinations, parameter effects, dependencies, and failure diagnosis. Use when documenting or teaching from ComfyUI workflow JSON files."
---

# ComfyUI Workflow Business Docs

Use this skill when the user needs to understand, teach, or document one or more ComfyUI workflow JSON files.

## Core rule

Explain the workflow from the user's business task backwards—not from the node list forwards. Every major section must answer:

> What result does the user want, and how does this group of nodes contribute to that result?

Avoid descriptions such as “passes data to the next node”, “forms a continuous process”, or merely restating node names and types.

## Required analysis

1. Read the workflow JSON, including node types, widget values, input/output ports, links, model names, prompts, masks, dimensions, and output nodes.
2. Identify the concrete task from the filename, prompts, inputs, model family, and graph. Examples: replace clothing, preserve identity, remove an object, generate a video from a reference frame, upscale detail.
3. Separate the workflow into business subfunctions, such as:
   - prepare source and reference material;
   - define the edit boundary or structure control;
   - convert references into model conditions;
   - apply style/identity/motion adapters;
   - generate or edit with the base model;
   - decode, repair, upscale, preview, and export.
4. For each subfunction, identify the smallest meaningful node combination and explain what would change if the combination were removed or misconfigured.
5. Use official model/custom-node documentation or source when a custom node's behavior cannot be established from ports and parameters. Mark unresolved claims as “requires runtime verification”; do not invent semantics.

## Required document structure

For each workflow, write a concise Markdown document with:

1. **Business goal** — one plain-language paragraph describing the intended result.
2. **Inputs and outputs** — source image/video, reference material, mask, prompt, model, and final result.
3. **Top-level flowchart** — a small Mermaid graph showing business subfunctions only.
4. **Subfunction explanations** — for every subfunction:
   - `Node combination`;
   - `Business purpose`;
   - node-to-business mapping;
   - why these nodes are combined;
   - important parameters and their effect on the requested result.
5. **Subfunction flowcharts** — one Mermaid graph per subfunction, showing only its nodes and internal links.
6. **Parameter tuning order** — prioritize parameters by business impact, normally mask/boundary, reference quality, prompt/conditioning, strength/guidance, seed, then performance settings.
7. **Failure symptoms and diagnosis** — connect visible symptoms to likely workflow causes.
8. **Dependencies and verification boundary** — model files, custom nodes, and what was inferred versus actually run.

## Writing standard

- Prefer “reference image + mask + ACEPlusFFTProcessor produce a clothing replacement in the selected region” over “LoadImage connects to ACEPlusFFTProcessor”.
- Explain each node only once in the node table; in subfunction sections explain the combination and business effect.
- Keep the total diagram readable: the top-level graph must not contain every node.
- Use tables for parameters and failure diagnosis.
- Distinguish evidence from inference and runtime validation. Never claim quality, speed, or compatibility without evidence.
