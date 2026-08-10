# Contribution 1: Help wanted: Support new frontend system (@backstage-community/plugin-xcmetrics)

**Contribution Number:** 1  
**Student:** Tish (Latisha) Griffiths  
**Issue:** [Github Issue](https://github.com/backstage/community-plugins/issues/7539)  
**Status:** Phase IV In Progress. 

---

## Why I Chose This Issue

This issue interests me because it is a revived opportunity to contribute to a real production plugin used by engineering teams. This work aligns well with my frontend development experience with JavaScript and frontend libraries. This feels like a natural challenge as I will be working with an unfamiliar product, platform, and codebase but familiar enough that I can make meaningful progress. I hope to learn more about the product and anything else as I work my way through this issue.

---

## Understanding the Issue

### Problem Description

The xcmetrics plugin needs to be updated to the new frontend system

### Expected Behavior

The platform should look and function the same as before.

### Current Behavior

The platform works but is using an outdated system.

### Affected Components

xcmetrics - backstage/community-plugins/tree/main/workspaces/xcmetrics/plugins/xcmetrics

---

## Reproduction Process

### Environment Setup

One challenge I ran into was getting the app to look similar to the real production app locally. I used claude to generate mock data and a new development script.

---

## Solution Approach

### Proposed Solution

Add new alpha endpoint with new frontend system. Keep the old system

### Implementation Plan

Using UMPIRE framework (adapted):

**Understand:** Add the new frontend system to the xcmetrics plugin

**Match:** There is a [recent pull request](https://github.com/backstage/community-plugins/pull/8948/changes/652958bbe252d1f99cdd197d01dbdc18e98ad852#diff-8300cb4af177566db515846e963441ef0d6c3590ebbbe25a5a5184f487939adf) that adds the new frontend system to another plugin, [Dynatrace](https://github.com/backstage/community-plugins/blob/main/workspaces/dynatrace/plugins/dynatrace/README.md)

**Plan:** 
1. Follow [migration guide](https://backstage.io/docs/frontend-system/building-plugins/migrating/)
2. Compare changes to the successful frontend system update of Dynatrace
3. Ensure all tests pass

**Implement:** [https://github.com/backstage/community-plugins/compare/main...TishG:community-plugins:xcmetrics-new-frontend-support](https://github.com/backstage/community-plugins/compare/main...TishG:community-plugins:xcmetrics-new-frontend-support)

**Review:** 
- [x] A changeset describing the change and affected packages. ([more info](https://github.com/backstage/community-plugins/blob/master/CONTRIBUTING.md#creating-changesets))
- [x] Added or updated documentation
- [x] All your commits have a `Signed-off-by` line in the message. ([more info](https://github.com/backstage/community-plugins/blob/master/CONTRIBUTING.md#developer-certificate-of-origin))

**Evaluate:** All tests pass, App runs locally

---

## Testing Strategy

### Unit Tests
Ensured all existing unit tests passed. 

### Manual Testing

Ensured app was functional locally

---

## Implementation Notes

### Week 1 Progress

Built a fully in-memory DevXcmetricsApi with mock data so the plugin can be developed and demoed locally without a real XCMetrics backend.
- Used Claude Code to generate the mock data and generate a new dev script for running the application locally

### Week 2 Progress

Migrated the @backstage-community/plugin-xcmetrics plugin to support Backstage's new frontend system by adding an /alpha entrypoint. This involved creating src/alpha.tsx with PageBlueprint and ApiBlueprint extensions, wiring them into a createFrontendPlugin, and exposing the new entry point via package.json exports.

### Week 9 Progress
Maintainer left 1 new comment, to go through this [skills doc](https://github.com/backstage/backstage/blob/master/docs/.well-known/skills/plugin-new-frontend-system-support/SKILL.md) and ensure I did not miss any steps. See link to [comment](https://github.com/backstage/community-plugins/pull/9454#pullrequestreview-4774456428).

### Week 10 Progress
Maintainer approved PR and merged into main.

### Code Changes

- **Files modified:** Main changes were done in workspaces/xcmetrics/plugins/xcmetrics/dev/DevXcmetricsApi.ts and workspaces/xcmetrics/plugins/xcmetrics/src/alpha.tsx. Here is the full list of [modified files](https://github.com/backstage/community-plugins/pull/9454/changes).

- **Key commits:** 
  - [https://github.com/backstage/community-plugins/pull/9454/changes/c90a97d284d054d8f4bbc3e24072665bac61fcec](https://github.com/backstage/community-plugins/pull/9454/changes/c90a97d284d054d8f4bbc3e24072665bac61fcec)
  - [https://github.com/backstage/community-plugins/pull/9454/changes/de7331d52037aad4af7eda7bab87e920fd22db35](https://github.com/backstage/community-plugins/pull/9454/changes/de7331d52037aad4af7eda7bab87e920fd22db35) 
- **Approach decisions:** 
  - Kept legacy exports intact — added new frontend system support as a separate /alpha entrypoint to avoid breaking existing users.
  - Used ADR plugin as a reference — the migration guide covers standalone pages only; the ADR plugin migration was a closer real-world match in the same codebase.
  - Used convertLegacyRouteRefs as a compat bridge — kept route ref migration out of scope to stay focused on the core change.
  - Built an in-memory DevXcmetricsApi — enabled local development and demos without needing a real backend.
  - Used a GitHub no-reply email for DCO sign-off — met the sign-off requirement without exposing my personal email in public commit history.

---

## Pull Request

**PR Link:** [https://github.com/backstage/community-plugins/pull/9454](https://github.com/backstage/community-plugins/pull/9454)

**PR Description:** Adds the frontend system to the xcmetrics plugin by adding a new alpha route

**Maintainer Feedback:**
- Jun 11, 2026: Copilot AI (automated) completed multiple review passes, flagging: a typo in the exported API extension name (`xCRMetricsApiExtension`, later `xcrmetricsApiExtension` in the generated API report — should be `xcmetricsApiExtension`), timestamp fields in the mock data using seconds instead of microseconds, mock target/error/warning generation referencing target IDs that might not exist, a non-isolated PRNG causing unstable mock data across calls, `package.json` `main`/`types`/`exports` pointing at TS/TSX source instead of built output, and legacy route refs/components not being wrapped for the new frontend system (missing `compatWrapper` / `convertLegacyRouteRef(s)`).
- [~1 week ago]: Maintainer @04kash requested changes:
  - Questioned why `workspaces/xcmetrics/backstage.json` was downgraded from 1.52.0 to 1.51.2 — flagged as unintended since the workspace should stay on its current version, not downgrade.
  - Asked for a `dev/alpha/index.ts` file (referencing a prior PR's pattern) so the alpha entrypoint is easy to test locally when developing/reviewing.
  - Asked for a `start:alpha` script (`backstage-cli package start --entrypoint dev/alpha`) to make running the alpha dev app easier.
  - Asked for a title and icon on the `xcmetricsPage` nav item.
  - Asked me to rebase the branch.
- Jun 11, 2026: backstage-goalie bot flagged that commits weren't DCO-signed and needed to be before review could proceed.
- Addressed all of the above: reverted `backstage.json` back to 1.52.0 and aligned `.yarnrc.yml`'s yarn-plugin spec to match; added `dev/alpha/index.tsx` (using Claude Code) modeled on the referenced PR; added the `start:alpha` script; added a `title` ('XCMetrics') and `icon` (`AssessmentIcon`) to `xcmetricsPage`; wrapped the legacy layout with `compatWrapper` and converted route refs via `convertLegacyRouteRef`/`convertLegacyRouteRefs`; renamed `xCRMetricsApiExtension` → `xcmetricsApiExtension` throughout (including the API report); added a `@alpha` annotation to the default export; added `@backstage/ui` styles to the dev instance; updated the README's new-frontend-system example to import `createApp` from `@backstage/frontend-defaults` instead of `@backstage/app-defaults`; added a test for the new `/alpha` entrypoint; rebased onto main; retrofitted DCO sign-off via `git rebase --signoff`.
- Wed, Jul 8, 2026: Rebased main again, addressed remaining comments, committed and pushed, then resolved CI failures from the merge.
- Wed, Jul 9, 2026 (~5 hrs): Addressed remaining Copilot comments and requested re-review from @04kash. Ran into additional CI failures that took a while to resolve due to unclear error output.
- Fri, Jul 24, 2026: Run changes against migration skills doc.

**Status:** Changes requested — addressed, re-review requested (as of Jul 9, 2026). Changes re-requested on Jul 27, 2026. See [comment](https://github.com/backstage/community-plugins/pull/9454#pullrequestreview-4774456428).

---

## Learnings & Reflections

### Technical Skills Gained

- Migrating a Backstage plugin to the new frontend system: building an /alpha entrypoint with PageBlueprint and ApiBlueprint extensions, and wiring them into a createFrontendPlugin
- Reading and adapting an existing migration (Dynatrace, ADR) as a reference when official docs didn't cover my exact case
- Debugging CI pipelines: fixing yarn.lock mismatches, generating missing API reports (report-alpha.api.md), adding missing @alpha JSDoc release tags, and resolving prettier/package-sync errors
- Retrofitting DCO sign-off onto existing commits with `git rebase --signoff`, and configuring a GitHub no-reply email for privacy
- Using Claude Code to scaffold mock data and dev scripts (DevXcmetricsApi, dev/alpha/index.tsx) for local development without a real backend
- Wrapping legacy components/route refs for compatibility with the new frontend system using `compatWrapper` and `convertLegacyRouteRef(s)`

### Challenges Overcome

- Navigating the Backstage migration guide, which describes migrating a standalone page but the plugin needed adapting for a different context
- Resolving several CI failures including a mismatched yarn.lock, a missing report-alpha.api.md API report, a missing @alpha JSDoc release tag, prettier formatting issues in .yarnrc.yml, and package sync errors — each requiring a separate fix and push
- Understanding the DCO sign-off requirement and retrofitting it onto existing commits using git rebase --signoff, including configuring a GitHub no-reply email to keep my personal email private

Used Claude and Claude Code to work through migration steps, debug CI errors, and generate the mock data implementation

### What I'd Do Differently Next Time

- Learn the relevant lint/CI commands (e.g., API report generation, prettier checks) upfront and run them locally before pushing, rather than discovering failures one at a time in CI
- Lean on AI tools more throughout the process
- Double check the contribution README's own guidelines more carefully before considering a section "done," to make sure documentation and process requirements are fully met

---

## Resources Used

- Backstage frontend system migration guide: https://backstage.io/docs/frontend-system/building-plugins/migrating/
- Dynatrace plugin frontend-system migration PR (used as a reference implementation): https://github.com/backstage/community-plugins/pull/8948
- ADR plugin (used as a closer real-world reference than the migration guide's standalone-page example)
- Prior PR's dev/alpha entrypoint pattern, referenced by @04kash: https://github.com/backstage/community-plugins/pull/5222
- community-plugins CONTRIBUTING.md — changesets and DCO sign-off requirements: https://github.com/backstage/community-plugins/blob/master/CONTRIBUTING.md
- Claude Code — used to generate mock data, dev scripts, and work through migration/CI debugging
