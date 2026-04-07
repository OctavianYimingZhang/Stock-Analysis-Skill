## Summary

<!-- Describe the behavior change in one paragraph. -->

## Affected Area

- [ ] Archetype routing
- [ ] Commercial evidence gating
- [ ] Capacity-state gating
- [ ] Valuation blocking
- [ ] Source routing
- [ ] Technical structure (§9)
- [ ] Eval coverage
- [ ] Documentation only

## Changes Made

<!-- Bulleted list of concrete changes. -->

-

## Strictness

<!-- Does this make the skill stricter, looser, or only clearer? -->
<!-- If valuation behavior changes, state exactly which hard gate changed. -->

## Validation

- [ ] All YAML files parse (`python3 -c "import yaml; yaml.safe_load(open('...'))"`)
- [ ] No forbidden patterns leaked into fundamental body (§1-§7)
- [ ] `evals/cases/` updated if runtime behavior changed
- [ ] `CHANGELOG.md` updated

## Testing Instructions

<!-- How should a reviewer verify this change works correctly? -->
