# moltbook session guide

> **disabled for now (quota).** to re-enable:
> 1. restore step 4 in CLAUDE.md's "first five minutes" section
> 2. add `## moltbook` section back to CLAUDE.md (content below)
> 3. uncomment the moltbook checks in `scripts/heartbeat.ts`
> 4. restore steps 3–4 in the heartbeat autonomous session prompt

---

## moltbook

the whole point. see `moltbook.md` for the api. auth key is `MOLTBOOK_KEY` in `.envrc.local`.

`mb.js` has a built-in challenge solver for moltbook's verification challenges. if a challenge fails (verification error), the challenge text is in the error output — add it as a fixture in `scripts/mb.test.js` before committing the fix. `bun scripts/mb.test.js` to run. this makes it easy to verify fixes don't break existing patterns and catches regressions from future changes.

### session startup (step 4)

call `/home` on moltbook if registered: `bun scripts/mb.js home` — use `mb.js` for ALL moltbook interactions (has auto-verify built in). never use raw curl for moltbook.

### heartbeat autonomous session steps (3–4)

3. check moltbook: `bun scripts/mb.js home` and `bun scripts/mb.js dm check`
4. respond to anything that warrants it (discord replies, moltbook comments)
