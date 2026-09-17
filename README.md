# ComfyUI Workflow Analyzer

This repository contains two Codex skills for analyzing and documenting ComfyUI workflow JSON files from a business and learning perspective.

## Skills

| Directory | Language | Purpose |
|---|---|---|
| `comfyui-workflow-analyzer/` | English | Analyze a workflow's business goal, functional subflows, node combinations, parameters, dependencies, and failure diagnosis. |
| `comfyui-workflow-analyzer-zh/` | Chinese | The same methodology in Chinese for Chinese-language learning and documentation. |

## What the skills produce

The skills guide Codex to explain:

- what the workflow is intended to achieve;
- what inputs, references, masks, prompts, and models it uses;
- how nodes combine into meaningful business subfunctions;
- why each subfunction is needed;
- how important parameters affect the requested result;
- how to diagnose visible failures;
- which conclusions are inferred and which have been verified at runtime.

The methodology uses a concise top-level flowchart plus separate subfunction flowcharts, while avoiding descriptions that merely repeat node connections.

## Usage

Copy the relevant skill directory into your Codex skills directory, or use the corresponding `SKILL.md` as the instruction source when asking Codex to analyze a ComfyUI workflow.

The skills are designed for workflow JSON files and do not claim that image quality, speed, compatibility, or model availability has been verified unless the workflow has actually been run.
