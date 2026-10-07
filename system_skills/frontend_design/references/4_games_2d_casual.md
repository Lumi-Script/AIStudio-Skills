# 2D & Casual Games Design Guidelines

This reference covers 2D web games, competitive card games, board games, chess
bots, word search & puzzle games, and arcade/defense mechanics.

## 1. Game State Machine
type GameState = 'TITLE_MENU' | 'PLAYING' | 'PAUSED' | 'ROUND_SUMMARY' | 'GAME_OVER';

- Title Menu: Instructions, difficulty selection, Start Game CTA.
- Active Play: Responsive table layout, drag & drop or click input.
- Summary / Game Over: Final score, breakdown, Play Again restart without page reload.

## 2. HUD & Overlay Discipline
- Unobtrusive HUD positioned in top/side header.
- Distinct card zones: Player hand (bottom), Opponent/Bot hand (top), Battle arena (center), Deck (side).
- Word search puzzle accessibility: Large touch cells (≥ 44px), 4-tier hint system.

## 3. Audio & Visual Feedback
- Synthesized Web Audio API sound effects for moves, captures, hits, and victories.
- Fast compositor transforms (≤ 200ms) for snappy dealing and flips.
- Non-hue-only indicators: combine colors with explicit text and icons.
