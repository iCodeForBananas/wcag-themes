WCAG-HIGH-CONTRAST THEME GUIDELINES (TARGET ≥ 8:1)

---

### 1. General principles

* Do: Treat contrast as non-negotiable; design “cool” within those limits.
* Do: Use a small, consistent palette (8–14 core colors).
* Don’t: Tune each token ad-hoc; enforce rules (by role, not random).

Example

* Do: “Base scale = background/foreground; all other colors derived from it.”
* Don’t: “Pick colors by eye until it looks nice.”

---

### 2. Base palette & neutrals

* Do: Use very dark and very light neutrals for main contrast; avoid pure #000 / #FFF to reduce glare.
* Do: Keep text on backgrounds at ≥ 8:1 contrast.
* Don’t: Put text on colored backgrounds that drop below 8:1.

Examples

* Do: Background `#050811`, Primary text `#F5F7FF` (≈ 15+:1)
* Do: Sidebar `#0B0F1C`, Sidebar text `#E0E4F5`
* Don’t: Background `#181A1F` with text `#8C8C8C` (too low).

---

### 3. Use color roles, not arbitrary colors

Define roles like:

* `bg.primary`, `bg.elevated`, `bg.statusBar`

* `fg.primary`, `fg.muted`, `fg.disabled`

* `accent.primary`, `accent.success`, `accent.error`, `accent.warning`

* Do: Map VS Code colors to these roles (e.g. `editor.background` → `bg.primary`).

* Don’t: Hardcode random colors to each VS Code key.

Example

* Do: `editor.foreground` = `fg.primary`, `editorLineNumber.foreground` = `fg.muted`.
* Don’t: Make line numbers pale blue and comments pale green “because it looks nice”.

---

### 4. Syntax highlighting

* Do: Use luminance + hue to keep ≥ 8:1 contrast against editor background.
* Do: Reserve strong, saturated colors for a few key token types (keywords, errors).
* Don’t: Use low-contrast “pastel on dark” for text tokens.

Examples (dark background `#050811`):

* Do:

  * Identifiers: `#DDE3FF`
  * Keywords: `#FFB347`
  * Strings: `#7FE7A8`
  * Functions: `#5BB8FF`
    All tested ≥ 8:1 vs background.
* Don’t:

  * Strings `#93E5C0` on `#1E1E1E` (likely <8:1).
  * Comments `#555` on `#1E1E1E` (< 4.5:1).

---

### 5. Comments, disabled text, and “muted” states

* Do: Make comments and disabled text lower contrast, but still ≥ 4.5:1 (or ≥ 8:1 if you require strict).
* Do: De-emphasize using hue and saturation (e.g. cooler/warmer, slightly desaturated), not just low contrast.
* Don’t: Use “nearly invisible” comments.

Examples

* Do: Background `#050811`, Comments `#8A93B3` (still highly readable).
* Don’t: Background `#050811`, Comments `#3A3A3A`.

---

### 6. UI chrome (sidebars, tabs, status bar)

* Do: Maintain strong contrast for labels, icons, and active elements.
* Do: Use contrast between active vs inactive tabs via border/underline + slight background shift.
* Don’t: Distinguish state using only a subtle color change.

Examples

* Do:

  * Inactive tab: bg `#050811`, fg `#A8B0CC`
  * Active tab: bg `#0F1424`, fg `#FFFFFF`, border `#FFB347`
* Don’t:

  * Inactive tab: `#1E1E1E`, Active tab: `#242424` with same text color.

---

### 7. State indicators (focus, hover, selection, error)

* Do: Provide visible focus rings and selection with ≥ 3:1 contrast against surrounding area (WCAG non-text contrast).
* Do: Combine color + shape (underline, outline, thicker border) to indicate state.
* Don’t: Use only a subtle color shift for focus; don’t rely only on color.

Examples

* Do:

  * Focused tab: 2px outline `#FFB347` around tab.
  * Selection: background `#193763` with text still ≥ 8:1 vs editor bg.
* Don’t:

  * Focus: slightly lighter background with no border.
  * Selection: darkening text color instead of changing background.

---

### 8. Color usage rules for the LLM

Give the LLM explicit constraints:

* All text/background pairs MUST have contrast ≥ 8:1 (use a contrast checker algorithm).
* Comments may have lower emphasis but MUST remain ≥ 4.5:1 (or 8:1 if you require).
* Limit syntax token categories to 5–7 distinct hues; adjust brightness/saturation, not hue count, for variety.
* Avoid pure `#000000` / `#FFFFFF`; use near-black and near-white while keeping ≥ 8:1.
* Never place text on accent colors unless contrast ≥ 8:1 with that accent.

---

### 9. Testing and iteration

* Do: Automatically validate all theme colors with a contrast checker before output.
* Do: Test both light and dark variants (if generated) for the same rules.
* Don’t: Trust manual eyeballing.

Examples of automated checks the LLM should honor:

* Check `editor.foreground` vs `editor.background`.
* Check token foreground vs `editor.background`.
* Check `statusBar.foreground` vs `statusBar.background`, `tab.activeForeground` vs `tab.activeBackground`, etc.
