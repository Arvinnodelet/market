# Teardown Analysis Playbook

## Objective
Infer product architecture and component choices from teardown evidence without turning inference into fact.

## Workflow
1. Define product and questions.
2. Collect official manuals, service documents, FCC/CE/certification material and teardown media.
3. Build subsystem map: mechanical, electrical, sensing, actuation, compute, software, materials.
4. Record each observed component with location, function and evidence.
5. Separate observed facts from inferred function and estimated specification.
6. Cross-check with product specifications, patents and supplier information.
7. Identify design trade-offs and likely cost drivers.
8. Produce architecture diagram and evidence table.

## Evidence Table
| Item | Observation | Inference | Confidence | Source |
|---|---|---|---|---|

## Rules
- Photo evidence proves visible structure, not hidden specifications.
- A component identification from marking should be verified where possible.
- Do not infer a sensor/control algorithm solely from a connector or PCB footprint.
- Preserve conflicting evidence.
