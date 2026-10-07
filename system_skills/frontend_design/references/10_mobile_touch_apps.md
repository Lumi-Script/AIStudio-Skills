# Mobile & Touch-First Applications Design Reference

This guide covers design aesthetics, thumb-zone ergonomics, touch target dimensions, card hierarchies, and mobile navigation patterns for smartphone viewports (375px–430px).

## 1. Touch Target & Ergonomic Thumb Zones
- Minimum Touch Hitbox: Every interactive trigger MUST have an interactive touch hitbox of at least 44 × 44px (48 × 48px for primary CTAs).
- Natural Reach Zone (Bottom 40%): Primary navigation tabs, key action buttons, bottom sheet triggers.
- Stretch Zone (Middle 30%): Content feed, scrollable cards, list rows.
- Hard Reach Zone (Top 30%): Page titles, search triggers, secondary filters.
- 15% Aggregate Sticky Surface Cap: Combined height of all fixed bars must never exceed 15% of viewport height.

## 2. Mobile Navigation Patterns
- Fixed Bottom Tab Bar: 3 to 5 evenly distributed destinations with 22px icon and 10px label.
- Mobile Top App Bar: Compact 52px–56px sticky header.
- Bottom Sheet / Action Drawer: Rounded top corners (rounded-t-3xl) with top drag handle affordance.

## 3. Mobile Card & Tracker Layouts
- Daily tracker top metric cards with SVG progress rings.
- Horizontal date scroller with active day buttons.
- Full-width list tap rows (56px–68px height).
