# Contribution 1: Help wanted: Support new frontend system (@backstage-community/plugin-xcmetrics)

**Contribution Number:** 1  
**Student:** Tish (Latisha) Griffiths  
**Issue:** [Github Issue](https://github.com/backstage/community-plugins/issues/7539)  
**Status:** Phase I In Progress

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

**PR Link:** [GitHub PR URL when submitted]

**PR Description:** [Draft or final PR description - much of the content above can be adapted]

**Maintainer Feedback:**
- [Date]: [Summary of feedback received]
- [Date]: [How you addressed it]

**Status:** [Awaiting review / Iterating / Approved / Merged]

---

## Learnings & Reflections

### Technical Skills Gained

[What you learned technically]

### Challenges Overcome

- Navigating the Backstage migration guide, which describes migrating a standalone page but the plugin needed adapting for a different context
- Resolving several CI failures including a mismatched yarn.lock, a missing report-alpha.api.md API report, a missing @alpha JSDoc release tag, prettier formatting issues in .yarnrc.yml, and package sync errors — each requiring a separate fix and push
- Understanding the DCO sign-off requirement and retrofitting it onto existing commits using git rebase --signoff, including configuring a GitHub no-reply email to keep my personal email private

Used Claude and Claude Code to work through migration steps, debug CI errors, and generate the mock data implementation

### What I'd Do Differently Next Time

[Reflection on your process]

---

## Resources Used

- [Link to helpful documentation]
- [Tutorial or Stack Overflow post that helped]
- [GitHub issues or discussions that helped]
