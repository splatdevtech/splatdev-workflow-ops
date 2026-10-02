# SplatDev Workflow — Operations

Deliverables for the **SplatDev Workflow** project in Paperclip: the documents the
operational routines produce, and nothing else.

## Why this repo exists

The project had no home of its own. Its issues carried PR URLs split across two
places — 39 in Azure DevOps (37 of them in `SplatDev Home and Services/_git/SplatDev
eCommerce`, a *product* repo) and 9 in `splatdevtech/splatdev-workflow`, which held
three files. Paperclip's completion gate was bound to the near-empty one, so
verification compared the merged deliverable against a repository that did not
contain it.

The visible cost, on 2026-10-01/02:

- **SPL-4371** failed the same verification **seven times in 48 hours**, each a full
  agent run finding the identical problem. The work was done and merged; the check was
  looking elsewhere.
- **SPL-4362** stalled every week on a required `build` check that
  `splatdev-workflow` can never emit — its only CI is two workflows that `echo
  "documentation-only repo"`.
- A quarterly architecture review's file citations could not be reproduced, because
  they were searched for in the wrong repository.

Operational documents were landing in a product codebase, and the gate was pointed at
neither place.

## What belongs here

Architecture decision reviews · compliance and governance reports · delivery forecasts
and OKR roll-ups · capacity and backlog reviews · runbooks and process docs.

## What does not

Product or application code. That stays in its own repository — `SplatDev eCommerce`
for the commerce work, and the relevant product repo otherwise. A document deliverable
should never require a product repo's build to go green.

## Layout

```
docs/
  proposals/      architecture decision reviews, design proposals
  compliance/     PR compliance and governance checks
  reports/        forecasts, OKR roll-ups, capacity reviews
  runbooks/       operational procedures
```

## Verification

The Paperclip project binds to this repo with `integrationBranch: main`. Because the
deliverables are documents, the binding uses **merge-only** verification
(`requiredChecks: []`): a deliverable counts as verified when its PR is merged into
`main`, with no CI check required.

That is a deliberate choice, not an oversight. Inventing an always-green check named
`build` to satisfy a gate is the failure this repo exists to end — and
`splatdev-workflow` already contains two such workflows as evidence of where that
leads.
