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

[Notes on setting up your local development environment - challenges you faced, how you solved them]

---

## Solution Approach

### Analysis

[Your analysis of the root cause - what's causing the issue?]

### Proposed Solution

[High-level description of your fix approach]

### Implementation Plan

Using UMPIRE framework (adapted):

**Understand:** Add the new frontend system to the xcmetrics plugin

**Match:** There is a [recent pull request](https://github.com/backstage/community-plugins/pull/8948/changes/652958bbe252d1f99cdd197d01dbdc18e98ad852#diff-8300cb4af177566db515846e963441ef0d6c3590ebbbe25a5a5184f487939adf) that adds the new frontend system to another plugin, [Dynatrace](https://github.com/backstage/community-plugins/blob/main/workspaces/dynatrace/plugins/dynatrace/README.md)

**Plan:** 
1. Follow [migration guide](https://backstage.io/docs/frontend-system/building-plugins/migrating/)
2. Compare changes to the successful frontend system update of Dynatrace
3. Ensure all tests pass

**Implement:** [](https://github.com/backstage/community-plugins/compare/main...TishG:community-plugins:xcmetrics-new-frontend-support)

**Review:** [Self-review checklist - does it follow the project's contribution guidelines?]

**Evaluate:** All tests pass, App runs locally

---

## Testing Strategy

### Unit Tests

- [ ] Test case 1: [Description]
- [ ] Test case 2: [Description]
- [ ] Test case 3: [Description]

### Integration Tests

- [ ] Integration scenario 1
- [ ] Integration scenario 2

### Manual Testing

[What you tested manually and results]

---

## Implementation Notes

### Week [X] Progress

[What you built this week, challenges faced, decisions made]

### Week [Y] Progress

[Continue documenting as you work]

### Code Changes

- **Files modified:** [List]
- **Key commits:** [Links to important commits]
- **Approach decisions:** [Why you chose certain approaches]

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

[What was hard and how you solved it]

### What I'd Do Differently Next Time

[Reflection on your process]

---

## Resources Used

- [Link to helpful documentation]
- [Tutorial or Stack Overflow post that helped]
- [GitHub issues or discussions that helped]
