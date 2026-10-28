# PROMPTS.md: Living Prompt Pack

> Module 3 · Prompt Chaining. Re-architect the build with prompt chains; capture the reusable ones here.

## How to use this pack

_Each prompt is a reusable step. Chain them: the output of one becomes the input to the next._

## Prompt chain: Value and retention hardening chain

### Step 1: Expand: add the two missing screens
```
Build the next phase of this app in a strict sequence:
1. Add a screen "Value Realization & ROI Report". Match the layout and spacing of the attached Asana screenshot.
2. Add a screen "Customer Health & Retention Dashboard". Match the data density of the attached Asana screenshot.
3. Navigation: write the logic so Value Realization & ROI Report links to Customer Health & Retention Dashboard.

Build these in order so Value Realization & ROI Report is the anchor for Customer Health & Retention Dashboard.
```

### Step 2: Behavior: handle loading, empty and error states
```
Apply the following logic constraints to the Value Breakdown flow:
- Use skeleton screens for the Workflow activity loading state.
- If no data is present, show the empty state: "No activity yet. Start using the product to capture actitvity".
- On fetch failure, trigger the error state: "Connection lost. Please refresh the dashboard".

Maintain the same design language throughout and tether all behavior strictly to these rules.
```

### Step 3: Refine: polish one thing on one screen
```
The Value Breakdown needs a professional Asana - style polish.
1. Start by listing the 3 biggest gaps in typography and spacing compared to Asana design system.
2. Once you've identified those, resize the headers and update the The workflows in workflow activity are in light color - make it dark and legible. to match.

Don't change anything else in the project or touch the underlying logic.
```

## Reusable techniques learned

- Naming the exact element to alter preserves the other elements intact.
- Naming constraints handles situations where users can get frustrated with graceful failure-handling.

## What broke (and the fix)

_Where a single mega-prompt failed and chaining fixed it._

_____
