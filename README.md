# Expo Mobile UI Enhancer

Skill for Codex, Claude, GitHub Copilot, and other AI coding assistants to polish React Native Expo app interfaces into native-feeling, production-ready mobile UIs.

## What This Skill Does

This skill helps improve Expo and React Native screens without rewriting working app architecture. It focuses on visual hierarchy, spacing, touch targets, safe areas, motion, accessibility, responsiveness, and common mobile UI states such as loading, empty, error, and disabled states.

It is designed for UI enhancement work, not backend changes or broad product refactors.

## Best Fit

Use this skill when you want the assistant to:

- improve a screen layout or component structure
- polish spacing, typography, alignment, and hierarchy
- make interactions feel more native on iOS and Android
- fix safe-area, scrolling, keyboard, or list UX issues
- add or improve loading, empty, error, and disabled states
- strengthen accessibility labels, roles, states, and contrast
- modernize an Expo Router or React Navigation screen without changing business logic

## Not A Fit

This skill is not intended for:

- backend-only work
- non-Expo web UI tasks
- navigation rewrites unless explicitly requested
- state management migrations
- API contract changes
- large dependency churn for cosmetic changes

## Skill Behavior

The skill instructs the assistant to:

1. identify the specific screen, route, or component being improved
2. inspect the project's existing styling and component conventions first
3. reuse current theme tokens, spacing, colors, and typography where possible
4. preserve behavior, props, navigation, and data flow unless the user asks for broader refactoring
5. prefer mobile-appropriate patterns for safe areas, lists, touch feedback, motion, and accessibility
6. keep changes small, coherent, and validated with available checks

## UI Priorities

The skill emphasizes:

- clear visual hierarchy
- better spacing and alignment
- larger tap targets
- safe-area correctness
- resilient scrolling on small screens
- performant lists
- polished but restrained animation
- accessible controls and readable text
- platform-appropriate iOS and Android behavior

It explicitly avoids generic, overdecorated, gradient-heavy UI redesigns that ignore the app's established design system.

## Example Prompts

- Make this Expo screen look more polished.
- Improve the UI/UX of this React Native component.
- Fix spacing, safe area, and layout issues on this mobile screen.
- Add loading, empty, and error states to this Expo Router page.
- Make this onboarding flow feel more native.
- Improve this list's visual design and mobile usability.

## Files

- [SKILL.md](./SKILL.md): the skill definition and detailed operating instructions

## Notes

This repository contains the skill definition itself. The operational rules live in [SKILL.md](./SKILL.md), while this README explains the skill's purpose, boundaries, and expected usage at a glance.