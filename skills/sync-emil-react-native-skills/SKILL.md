---
name: sync-emil-react-native-skills
description: Use when checking emilkowalski/skills for upstream changes, assessing their impact on the installed React Native adaptations, preparing a port report, applying approved semantic updates, or advancing the recorded upstream checkpoint.
---

# Sync Emil React Native Skills

## Core Principle

Detect automatically; port semantically; mutate only with explicit authorization. Treat Emil's repository as Web-first source material, not files to copy over the React Native adaptations.

## Modes

Choose the first matching mode:

1. **Check/report** — default. Compare upstream with the recorded checkpoint, classify changes, produce an impact report, and stop without modifying files or state.
2. **Plan port** — produce exact proposed changes and tests, but do not modify files or state.
3. **Apply approved port** — edit only changes the user explicitly approved, validate them, save them, and then advance state.
4. **Record no-op checkpoint** — advance state only when the user explicitly approves recording an inspected range that requires no local content changes.

Words such as "check," "inspect," "report," or "what changed" select check/report mode. Do not infer mutation permission from them.

## Required Context

1. Read [upstream-state.yaml](references/upstream-state.yaml) for the repository, branch, and exact checkpoint SHA.
2. Read [upstream-map.md](references/upstream-map.md) for source-to-target ownership and classification rules.
3. Locate installed target skills by matching the `name:` frontmatter in `/root/.codex/skills/remote-skills/*/SKILL.md`. Never depend on a stored `skill-<id>` directory name because installation may rewrite it.

## Check Workflow

1. Fetch the exact upstream branch head and commits after `checkpoint_commit`. Prefer the connected GitHub app; use official GitHub sources if the connector is unavailable.
2. Verify that the checkpoint is an ancestor of the head. If it is missing, inaccessible, or upstream history was rewritten, stop and report the condition. Do not guess a comparison range.
3. List changed files across the complete range before reading individual patches.
4. Inspect relevant upstream `skills/*/SKILL.md` patches and any new skill directories. Treat README, image, typo, and installation-only changes as evidence for a no-op unless they alter the skill inventory or meaning.
5. Classify every relevant change using the categories in the mapping reference.
6. Produce the required impact report and stop unless the active mode explicitly authorizes mutation.

If head equals the checkpoint, report "No upstream changes" and make no state edit.

## Impact Report Contract

Start with:

```markdown
Upstream: emilkowalski/skills
Checkpoint: <full SHA>
Head: <full SHA>
Range: <checkpoint>..<head>
```

Then use:

| Upstream file/change | Classification | React Native target | Proposed action | Evidence | Approval |
| --- | --- | --- | --- | --- | --- |

End with exactly these sections:

- **Verdict:** no-op / port recommended / new-skill evaluation / blocked.
- **State action:** unchanged / eligible to advance after approval / advance after successful port.
- **Unverified:** inaccessible commits, missing patches, unknown target versions, or runtime claims.

Do not describe an upstream behavior as ported until the installed target file contains it and validation has passed.

## Semantic Port Rules

- **Universal principle:** preserve the intent, terminology, and decision boundary; express it in native React Native terms.
- **Web implementation:** extract the behavior being taught, then map it to installed React Native, Reanimated, Gesture Handler, Expo, or platform APIs. Never copy CSS, DOM, WAAPI, Framer Motion, browser media queries, or Pointer Events into native guidance.
- **New capability or skill:** evaluate whether it belongs in an existing target or warrants a new React Native skill. Present the decision before creating anything.
- **Irrelevant change:** do not edit target skills. It may still justify a no-op checkpoint after approval.

Preserve local improvements, routing, scope hard stops, platform verification, Reduced Motion, haptic restraint, Safe Area, keyboard, scroll ownership, and unverified-claim labeling. Apply a minimal patch; never replace a complete target `SKILL.md` with its upstream source.

## Apply Workflow

Only enter this workflow when the user explicitly authorizes the proposed port.

1. Re-fetch upstream head. If it differs from the reported head, stop and regenerate the report.
2. Re-read each current target skill and its references before editing.
3. Apply one source-to-target change at a time using the mapping reference.
4. Validate each changed skill with `quick_validate.py`.
5. Forward-test the affected behavior with a fresh context. Include at least:
   - the new or changed upstream principle;
   - rejection or translation of any Web-only implementation;
   - the target skill's scope boundary;
   - unchanged routing and output contracts.
6. Fix Critical or Important review findings and repeat affected tests.
7. Save each changed personal skill separately using the `skill-creator` save process.
8. Advance the checkpoint only after every authorized target save succeeds and the saved versions are revalidated.

If any target fails validation or saving, leave the checkpoint unchanged and report the partial state. Never mark a partially applied range as synchronized.

## State Update Rules

Edit [upstream-state.yaml](references/upstream-state.yaml) only in apply-approved or record-no-op mode.

- Set `checkpoint_commit` to the exact inspected head SHA.
- Set `checked_at` to the current ISO date.
- Set `checkpoint_kind` to `ported` or `no-op`.
- Record a concise `checkpoint_note` naming affected upstream skills or explaining why no local change was needed.
- Save this sync skill only after target skills have been saved successfully.

For a no-op range, require explicit approval before advancing state. For a port, the user's approval to apply the reported changes also authorizes advancing state after successful validation and save.

## Failure Handling

- **GitHub unavailable:** report that the current upstream state cannot be verified; do not advance state.
- **Checkpoint not found or not an ancestor:** report blocked history and request a new trusted baseline.
- **Target skill missing:** report the exact `name:` that could not be located; do not silently create a replacement.
- **Upstream adds or removes a skill:** classify as new-skill evaluation; do not auto-create or delete local skills.
- **Concurrent local changes:** preserve them and stop if the semantic merge is ambiguous.
- **Validation or save failure:** keep the previous checkpoint and list which local edits exist.

## Common Mistakes

- Copying upstream Web files over native adaptations.
- Treating README-only commits as skill-content updates.
- Updating state during a report-only request.
- Advancing the SHA before all target saves succeed.
- Using short SHAs in persistent state.
- Storing rewritten installation directory IDs in the mapping.
- Claiming platform behavior from static skill text.
