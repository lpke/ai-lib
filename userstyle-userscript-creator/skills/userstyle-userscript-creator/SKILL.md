---
name: userstyle-userscript-creator
description: Live browser workflow using Chrome DevTools MCP to create robust userstyles or userscripts by inspecting a live page, injecting candidate CSS or JavaScript into the DOM, testing behavior, and extracting the result. Use when the user asks to come up with, test, iterate, debug, return, or save userstyles, Stylus `.user.css`, userscripts, Violentmonkey `.user.js`, custom CSS, custom JavaScript, browser tweaks, or page-specific behavior/styling for a site, app, or currently open Chrome tab.
---

# Userstyle Userscript Creator

## Overview

Use Chrome DevTools MCP as the primary tool. Inspect the live page, inject candidate CSS or JavaScript directly into the page, verify behavior in the browser, then extract the working result for the user. The final result may be returned in chat, saved to a file, or adapted into an existing userstyle or userscript.

## Choose Style Or Script

- Use a userstyle when the request is mainly visual or layout-related and can be solved with CSS: sizing, spacing, colors, hiding elements, scroll behavior, sticky positioning, typography, or hover/focus styling.
- Use a userscript when the request changes behavior or needs JavaScript: event handling, keyboard shortcuts, click automation, DOM mutation, computed logic, persistence, network interception, or dynamic behavior CSS cannot reliably express.
- If the user does not specify userstyle versus userscript, choose the smallest robust fit. Prefer CSS for pure presentation. Use JavaScript when behavior must change.
- Stylus consumes userstyles copied by the user from `.user.css` files. Violentmonkey consumes userscripts copied by the user from `.user.js` files.

## Default Locations

If the user does not specify a destination, use these source directories:

- Userstyles: `/home/luke/.config/browser-usercode/styles/`
- Userscripts: `/home/luke/.config/browser-usercode/scripts/`

Inspect existing files first with `rg --files` and match local naming, metadata, and directory conventions.

## Required Tooling

- Use Chrome DevTools MCP whenever a live browser tab is available.
- Prefer `list_pages`, `select_page`, `take_snapshot`, `evaluate_script`, `click`, `fill`, `press_key`, `resize_page`, and `take_screenshot` as needed.
- If Chrome DevTools MCP is unavailable, state that live verification cannot be done and use the best available fallback.

## Workflow

1. Inspect the target tab.
   - Use Chrome DevTools MCP `list_pages` and select the page matching the user's description, or the active page if that is what they asked for.
   - Take an accessibility snapshot first. Use screenshots only when visual layout details matter.
   - Identify relevant DOM structure, scroll containers, stable attributes, app-specific classes, event targets, dynamic rendering behavior, and computed styles with `evaluate_script`.

2. Prototype live.
   - For CSS, add or update a `<style>` element with a stable test id, such as `codex-userstyle-test`.
   - For JavaScript, run minimal candidate code with `evaluate_script`. If repeated testing needs event handlers or observers, install them under a stable global namespace such as `window.__codexUserscriptTest` so they can be replaced or removed.
   - Keep live injections reversible and scoped to the target site or feature.
   - Prefer stable selectors: semantic app classes, `data-*` attributes, roles, ARIA labels, and structural context. Avoid hashed/generated classes unless no better selector exists.

3. Verify behavior, not just code shape.
   - Exercise the page the way the user described: scroll, hover, open panels, resize, edit, click, type, navigate, or otherwise trigger the affected state.
   - Measure success with DOM facts where possible: `scrollTop`, `scrollHeight`, bounding rects, computed styles, focused elements, visible text, event results, storage values, or changed DOM state.
   - Iterate until the CSS or JavaScript works in the live browser.

4. Test adjacent page contexts.
   - Try other wrappers that likely share the same issue: modals, side peeks, drawers, full-page views, nested pages, database item pages, popovers, responsive widths, dark/light themes, SPA navigation, or dynamically inserted content.
   - Only create or edit live app content when needed to validate the tweak and the user has implied that is acceptable. Keep test content minimal.

5. Extract the working result.
   - If the user asked for the result in chat, return the smallest working CSS or JavaScript block plus any scope notes.
   - If saving a userstyle, create or update a `.user.css` file. For Stylus, include `/* ==UserStyle== */` metadata and an `@-moz-document` domain scope when that pattern is present locally.
   - If saving a userscript, create or update a `.user.js` file. For Violentmonkey, include `// ==UserScript==` metadata with appropriate `@match` or `@include` scope and avoid broad permissions unless needed.
   - Use `apply_patch` for file edits.

6. Report outcome.
   - Include the final destination: chat, saved file path, or existing file updated.
   - Briefly list the live contexts tested and any known gaps.

## Guardrails

- Do not stop at generated CSS or JavaScript when a browser tab is available; inject and test it.
- Do not persist unrelated page/app changes.
- Do not broaden selectors, `@match` patterns, or `@-moz-document` scopes across the whole web unless the user explicitly wants a global tweak.
- For userscripts, keep privileges minimal. Do not add network access, cross-origin permissions, or persistent storage unless the behavior requires it.
- If Chrome DevTools MCP is unavailable, say so and make clear that live verification was not possible.
