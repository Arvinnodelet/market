# BOM Estimation Playbook

## Objective
Estimate hardware BOM and manufacturing cost when public BOM is unavailable.

## Workflow
1. Define configuration, production volume and geography.
2. Decompose product into assemblies.
3. Identify known components from teardown / manuals / certification.
4. Estimate unknown components using comparable parts and engineering constraints.
5. Collect reference prices by component class and volume assumption.
6. Add PCB assembly, mechanical parts, wiring, packaging, assembly and calibration assumptions.
7. Build Base / Low / High scenarios.
8. Perform sensitivity analysis on the largest cost drivers.

## Cost Structure
| Assembly | Component | Qty | Unit estimate | Basis | Confidence |
|---|---|---:|---:|---|---|

## Rules
- BOM cost is not retail price.
- Distinguish component price, assembled PCB cost, manufacturing cost and landed cost.
- Estimated values must never be presented as disclosed company data.
- State volume, supplier region and price basis.
