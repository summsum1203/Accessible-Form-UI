# Accessible Form UI

A static, accessible form UI built with only HTML and CSS. This repository contains a single UI component — a non-functional (static) form that demonstrates accessible markup and styling for a full name, email, password, and confirm password fields, plus a password-visibility toggle control (visual only), a completeness progress bar, and a checklist of requirements that must be met for the form to reach 100% completeness.

Project purpose

- Practice building well-structured, accessible form UIs using semantic HTML and CSS only.
- Provide a reusable static UI that can be enhanced with JavaScript later to become fully functional.

Live roadmap

This project follows the public roadmap: https://roadmap.sh/projects/accessible-form-ui

How to view

1. Clone the repository:

   git clone https://github.com/summsum1203/Accessible-Form-UI.git
2. Open accessibleFormUI.html in your browser (no build step required).

What you'll find

- accessibleFormUI.html — the static form UI (Full name, Email, Password, Confirm Password, password-visibility toggle control, completeness progress bar, and checklist).
- style.css — the CSS used to create accessible focus, visual structure, and responsive layout.
- assets/demo.gif — a small demo GIF showing the UI in action (placeholder).
- TESTING.md — detailed accessibility testing notes and suggested checks.

Demo

A short demo GIF is included in this repository at `assets/demo.gif` to illustrate the form UI and focus states. The GIF is a visual aid only; it does not change the static nature of the component.

Testing & Accessibility notes

Detailed testing guidance is available in `TESTING.md`. It covers automated tooling (axe, Lighthouse, Pa11y), manual testing with screen readers (VoiceOver, NVDA, TalkBack), keyboard-only navigation checks, and color-contrast verification steps. Please consult that document when evaluating or extending the UI.

Accessibility goals and guidelines

This project was built with the following accessibility principles in mind:

- Semantic labeling: Every input has an associated `<label>` with a `for` attribute connected to the input's `id`.
- Focus states: Inputs and interactive elements have visible focus styles to support keyboard-only users.
- Error message placeholder: The layout includes space for inline error messages associated to inputs via `aria-describedby`.
- ARIA attributes: Use `aria-required` for required controls and `aria-invalid` when inputs have errors (provided as static attributes/placeholders in the UI where appropriate).
- Keyboard access: The password visibility control and other interactive elements are represented so they can be made keyboard-accessible when JS is added.
- Color contrast: Colors were chosen to meet WCAG contrast recommendations; high-contrast focus rings are included.

Note: This repository contains a visual/static UI only. JavaScript is intentionally omitted for this project; it can be added in future work to provide runtime behaviors (toggle password visibility, live progress updates, validation, etc.).

Form details (static)

- Fields: Full name, Email, Password, Confirm Password
- Toggle: Visual button to indicate show/hide password state (not functional in this version)
- Progress: A completeness progress bar showing how many checklist criteria are met (static visuals)
- Checklist: A visible list of requirements (e.g., password length, uppercase, number, match) presented as checkable items in the UI (static)

Contributing

Contributions are welcome. Please open issues or pull requests for:

- Bug fixes to markup or styling
- Accessibility improvements and suggestions
- Adding an optional JavaScript enhancement that preserves accessibility

Before contributing, please include a short accessibility rationale for UI/behavior changes.

License

This project is released under the MIT License. See LICENSE for details.

Maintainer

- summsum1203 (you)
