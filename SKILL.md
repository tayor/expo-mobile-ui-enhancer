---
name: expo-mobile-ui-enhancer
description: Enhance, polish, and refactor React Native Expo mobile app UIs. Use when improving screen layouts, visual hierarchy, spacing, animations, accessibility, responsiveness, safe areas, Expo Router screens, native-feeling interactions, haptics, image handling, forms, lists, or overall mobile design quality. Do not use for backend-only tasks or non-Expo web-only UI.
---

# Expo Mobile UI Enhancer

Use this skill to upgrade React Native Expo app interfaces into polished, native-feeling, production-ready mobile experiences.

## Primary Goal

Improve the app’s UI without breaking existing behavior. Preserve business logic, navigation, data flow, API contracts, and existing component responsibilities unless the user explicitly asks for broader refactoring.

## First Pass: Inspect Before Editing

Before making changes:

1. Identify the screen, route, or component being enhanced.
2. Check the existing styling system:
   - StyleSheet
   - NativeWind / Tailwind
   - Tamagui
   - Restyle
   - custom design tokens
   - inline styles
3. Reuse existing theme tokens, spacing, colors, typography, and components where possible.
4. Check whether the project uses:
   - Expo Router
   - React Navigation
   - react-native-safe-area-context
   - expo-image
   - expo-haptics
   - react-native-reanimated
   - gesture-handler
5. Avoid adding new dependencies unless the improvement clearly requires one.

## UI Enhancement Principles

Prioritize:

- Clear visual hierarchy
- Better spacing and alignment
- Larger tap targets
- Native-feeling motion
- Safe-area correctness
- Scroll resilience on small screens
- Empty, loading, error, and disabled states
- Accessibility labels and roles
- Consistent typography and color usage
- Better list performance
- Platform-appropriate behavior on iOS and Android

Avoid:

- Generic gradient-heavy “AI-looking” UI
- Overdecorated cards
- Tiny text
- Low contrast
- Hardcoded magic spacing everywhere
- Web-only elements such as `div`, `img`, or CSS-only assumptions
- Replacing working app architecture just to restyle a screen

## Expo + React Native UI Rules

### Safe Areas and Scroll

- Prefer `react-native-safe-area-context` over React Native’s deprecated `SafeAreaView`.
- For stack-based screens, the first visual child should often be a `ScrollView` or list that handles safe-area and header behavior.
- Use `contentInsetAdjustmentBehavior="automatic"` on iOS scroll containers where appropriate.
- Ensure screens remain usable on small devices and with large dynamic type.

### Images

- Prefer `expo-image` for remote and performance-sensitive images.
- Add placeholders, transitions, cache policy, and content fit when helpful.
- Avoid unoptimized image usage in long lists.

Example:

```tsx
import { Image } from "expo-image";

<Image
  source={{ uri: imageUrl }}
  style={styles.image}
  contentFit="cover"
  transition={180}
/>
````

### Touch and Feedback

* Prefer `Pressable` for custom press states.
* Add pressed/disabled states.
* Use `expo-haptics` sparingly for important interactions, especially on iOS.
* Do not overuse haptics for routine taps.

### Lists

* Use `FlatList`, `SectionList`, FlashList, or LegendList for long datasets.
* Avoid rendering large arrays inside `ScrollView`.
* Keep `renderItem` lightweight.
* Use stable callbacks and stable item keys.
* Move expensive formatting outside item render paths when possible.

### Forms

* Labels must be clear.
* Inputs need focus, error, disabled, and helper states.
* Validation errors should be visible and specific.
* Primary actions should be obvious and reachable.
* Keyboard behavior must be handled with `KeyboardAvoidingView`, scroll containers, or existing project conventions.

### Motion

Use animation only when it improves clarity or delight.

Prefer animating:

* opacity
* transform
* scale
* translateY / translateX

Avoid animating layout-heavy properties unless necessary.

When Reanimated is already installed, use it for gesture-linked or high-frequency animations. Otherwise, use built-in `Animated` for simple transitions.

## Visual Polish Checklist

When enhancing a screen, check:

* Is the main action visually obvious?
* Is there enough vertical rhythm?
* Are groups/cards/sections visually distinct?
* Are icons used consistently?
* Are destructive actions clearly separated?
* Does the empty state explain what to do next?
* Does loading preserve layout stability?
* Are errors recoverable?
* Does the screen work in dark mode if the app supports it?
* Are colors pulled from theme tokens?
* Are tap targets at least around 44x44 points?
* Is text readable on small devices?
* Does the UI avoid clipping behind notches, home indicators, and headers?

## Accessibility Requirements

Add or preserve:

* `accessibilityRole` for buttons, tabs, switches, and links
* `accessibilityLabel` where visible text is not enough
* semantic button states via `accessibilityState`
* sufficient contrast
* support for larger text where practical
* no reliance on color alone for errors or statuses

## Refactoring Boundaries

Allowed:

* Improve component structure for readability.
* Extract small presentational components.
* Consolidate repeated styles.
* Replace fragile inline styles with tokens.
* Add missing UI states.

Avoid unless requested:

* Rewriting navigation
* Replacing state management
* Changing API behavior
* Adding a new UI framework
* Large dependency changes
* Unrelated cleanup

## Implementation Workflow

For each UI task:

1. Summarize the intended UI improvement briefly.
2. Make the smallest coherent change.
3. Preserve existing props and behavior.
4. Check TypeScript types.
5. Run available checks if known:

   * `npm run lint`
   * `npm run typecheck`
   * `npm test`
   * `npx expo-doctor`
6. Mention any checks that could not be run.

## Output Expectations

When finished, report:

* What changed visually
* Which files changed
* Any accessibility or responsiveness improvements
* Any assumptions made
* Any follow-up polish ideas, only if relevant

## Example Requests That Should Trigger This Skill

* “Make this Expo screen look more polished”
* “Improve the UI/UX of this React Native component”
* “Make this mobile app feel more native”
* “Fix spacing, safe area, and layout issues”
* “Add loading, empty, and error states”
* “Improve this Expo Router screen”
* “Make this list perform and look better”
* “Modernize this mobile onboarding flow”