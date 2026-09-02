# Fact vs Inference

## Fact

A statement directly supported by a source.

Example:

> Manufacturer documentation states that the product uses an optical encoder.

## Verified Fact

A statement supported by multiple independent reliable sources.

## Reported

A credible third party reports the statement, but primary confirmation is unavailable.

## Inference

A conclusion derived from observed evidence such as photos, teardown, PCB markings, mechanical structure, interfaces, or performance behavior.

Use language such as:
- likely
- appears to
- suggests
- consistent with

## Estimate

A numerical or commercial conclusion derived from assumptions, calculations, industry benchmarks, or comparable products.

Always expose the basis.

## Unknown

There is not enough evidence to make a responsible claim.

Prefer:

> Unknown / not publicly disclosed

rather than inventing a value.

## Writing Rule

Never silently upgrade:

```text
Inference → Fact
Estimate → Public Data
Reported → Confirmed
```

The report should preserve uncertainty when it materially affects the conclusion.
