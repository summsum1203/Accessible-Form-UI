# Accessibility Testing Notes — Accessible Form UI

This document lists recommended automated and manual tests to validate the accessibility of the static form UI. It is written so you (or contributors) can quickly run checks and interpret results.

Automated checks

- axe-core (browser extension or npm): Run axe in the page context to find common accessibility violations (contrast, missing labels, ARIA misuse, landmark issues).
  - Browser extension: Install the axe DevTools extension (Chrome/Edge/Firefox) and run it on accessibleFormUI.html.
  - CLI: `npx axe-core --help` or integrate into CI with `axe-core` or `axe-cli` wrappers.

- Lighthouse (Chrome DevTools): Open DevTools > Lighthouse > Accessibility and run the audit. Review the actionable items (contrast, ARIA, color, headings).

- Pa11y: `npx pa11y file://$(pwd)/accessibleFormUI.html` to run a quick check from the command line.

Manual checks

1. Keyboard navigation
   - Tab through the page to ensure focus moves in a logical order: Full name → Email → Password → Confirm password → Toggle password → Submit.
   - Ensure the toggle-password control receives focus and has a visible focus ring.
   - Use Shift+Tab to test reverse navigation.

2. Screen reader flow
   - VoiceOver (macOS): Turn on VoiceOver and navigate the page. Ensure that each control announces its label and any helpful descriptions (like help text). Focus the password toggle and confirm the button announces "Show" and that it has a pressed state when JS is added.
   - NVDA (Windows): Use NVDA to navigate the form and validate the reading order and announcements.
   - TalkBack (Android): For mobile checks, host the file on a device or emulator and use TalkBack to confirm announcements.

3. Focus and visible indicators
   - Verify focus styles are high-contrast and clearly show which control has keyboard focus.
   - Check focus styles for interactive elements like the toggle button and submit button.

4. Color contrast
   - Use a contrast checker (WebAIM Contrast Checker or the axe extension) to confirm that body text, form labels, and interactive text meet WCAG AA contrast ratios (4.5:1 for normal text, 3:1 for large text).

5. ARIA and semantic checks
   - Confirm labels are programmatically associated using `for`/`id`.
   - Ensure `aria-describedby` references are valid and point to elements that exist (help and error text placeholders).
   - Verify the progress element is labeled and has a meaningful value.

6. Error message placeholders and dynamic announcements
   - There are static placeholders for error messages with `aria-live="polite"`. When JS is added, update these elements' text content and set `aria-invalid="true"` on invalid fields.

CI integration suggestions

- Add axe-core checks in CI (jest-axe or axe-playwright) to catch regressions.
- Add Lighthouse snapshots with `lighthouse-ci`.
- Run Pa11y in a GitHub Actions workflow on PRs.

Reporting issues

- When filing accessibility bugs, provide: steps to reproduce, expected behavior, actual behavior, browser and assistive technology used, and screenshots or short screen recordings if possible.

Credits & resources

- axe-core: https://github.com/dequelabs/axe-core
- Lighthouse: https://developers.google.com/web/tools/lighthouse
- Pa11y: https://pa11y.org/
- WebAIM: https://webaim.org/
