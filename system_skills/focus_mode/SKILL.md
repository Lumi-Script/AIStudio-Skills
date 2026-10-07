---
name: focus-mode
description: Instructions for responding to UI element selection (CSS selectors).
---

### Focus Mode: Responding to Element Selection

The following "Focus Mode" instructions apply only if the current request
contains a metadata block with CSS selector information. The metadata block
appears at the end of the user's prompt in this format:

```
[AIS_METADATA_SECTION_START]
CSS selector: <selector>
[AIS_METADATA_SECTION_END]
```

Or:

```
[AIS_METADATA_SECTION_START]
CSS selector 1: <selector>
CSS 1: { <css properties> }
CSS selector 2: <selector>
CSS 2: { <css properties> }
[AIS_METADATA_SECTION_END]
```

If no metadata block is present, this section can be ignored.

When a selector *is* provided, it signifies the user's current focus on a
specific UI element. Your changes should be primarily focused on this element.
Even if there are other elements that look similar, only the element matching
that CSS selector should be changed. Ignore any other selectors mentioned in the
conversation history, as they are from previous selections and no longer active.
Your code modifications should be highly targeted to modifying that element.

-   **Handling CSS Blocks:** If `CSS N:` blocks are provided in the metadata,
    you MUST apply those CSS rules FIRST, before processing any text prompt.
    Apply ONLY those CSS rules to their matching `CSS selector N:` elements.
    After applying the CSS, proceed to handle the user's text prompt (if any).
    When applying CSS, you MUST NOT modify any files or elements beyond what is
    strictly necessary to apply the provided CSS rules. In particular, you MUST
    NOT introduce accessibility updates, theme updates, or fix other styling
    issues not covered by the provided CSS, even if you notice them as problems.
-   **Analyze Context:** Use the provided CSS selector to locate the element
    within the code files. Examine the element's markup, content, and any
    associated styles to understand its purpose and context. This will give you
    a better understanding of what changes are permissible and relevant for that
    element.
-   **Keep Changes Focused:** Changes should prioritize the selected element and
    its children. However, you can make changes to a parent or related component
    if it's a logical extension of the user's action (e.g., modifying a table's
    properties when a row is selected). When making style changes, apply them
    directly to the element to avoid unintended global changes.
-   **Maintain Overall Relevance:** Ensure that even element-specific changes
    are aligned with the application's purpose.
