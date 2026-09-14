# Test plan — WizBiz Website

This is a worked example. It shows what `tests/test-plan.md` looks like once
somebody has actually filled it in, so you can see the level of detail expected
before you write your own.

Copy the structure, not the results. Your results must be things you saw.

---

## How to use this file

One section per issue. Add a section when you start the issue, fill in the
**Result** and **Date** columns as you test, and commit the file in the same
pull request as the work.

| Result | Means |
|---|---|
| `PASS` | You ran it and it behaved as the Expected column says |
| `FAIL` | You ran it and it did not. Raise a defect issue and link it here |
| `N/A` | Genuinely does not apply. Say why in the Notes column |

Leave nothing blank. A blank row and a failed row look identical to an
assessor, and to you in three weeks.

---

## Issue #13 — Responsive navigation

**Tested by:** Charlie Chen
**Branch:** `feature/13-responsive-navigation`
**Date:** 2026-09-12
**Environment:** Windows 11 · Chrome 141 · Edge 141 · Firefox 143 · served from `http://localhost:8000`

### Acceptance criteria from the issue

| # | Criterion | Result |
|---|---|---|
| AC1 | Below 768px the menu collapses to a button | PASS |
| AC2 | Tapping the button opens the list | PASS |
| AC3 | Choosing a link closes the menu | PASS |
| AC4 | Every link reachable with the Tab key | PASS |

### Test cases

| ID | Area | What I did | Expected | Result | Notes |
|---|---|---|---|---|---|
| TC-01 | Layout 320px | Set DevTools device width to 320 | Menu is a button, no horizontal scrollbar | PASS | Tightest width tested |
| TC-02 | Layout 375px | Set width to 375 | Same as TC-01 | PASS | |
| TC-03 | Layout 768px | Set width to 768 | Links show as a row, button hidden | PASS | Breakpoint behaves at exactly 768 |
| TC-04 | Layout 1440px | Set width to 1440 | Links as a row, spaced evenly | PASS | |
| TC-05 | Open menu | At 375px, tapped the button | List appears below the header | PASS | |
| TC-06 | Close on link | With menu open, tapped **About** | About page loads, menu is closed on arrival | PASS | Closes because the page reloads |
| TC-07 | Keyboard order | Pressed Tab from the top of the page | Brand, then button, then each link in order | PASS | Focus outline visible on every item |
| TC-08 | Keyboard open | Focused the button and pressed Space | Menu opens without a mouse | PASS | |
| TC-09 | Console | Opened DevTools Console and reloaded | No red error lines | PASS | Checked on all four pages |
| TC-10 | Assets | Checked the Network tab | `style.css` returns 200 | PASS | |
| TC-11 | Cross-browser | Repeated TC-01 to TC-09 in Edge | Same behaviour as Chrome | PASS | |
| TC-12 | Cross-browser | Repeated TC-01 to TC-09 in Firefox | Same behaviour as Chrome | PASS | |
| TC-13 | Regression | Opened every page completed before this issue | Nothing previously working is broken | PASS | Home only, at this point |

### Defects raised

| Issue | Summary | Status |
|---|---|---|
| — | None found | — |

### Notes

TC-03 is worth keeping for every later issue. The breakpoint is the place a
change is most likely to go wrong, and it is the one width nobody checks by
accident.

---

## Issue #14 — Home page

**Tested by:**
**Branch:** `feature/14-home-page`
**Date:**
**Environment:**

### Acceptance criteria from the issue

| # | Criterion | Result |
|---|---|---|
| AC1 | | |
| AC2 | | |

### Test cases

| ID | Area | What I did | Expected | Result | Notes |
|---|---|---|---|---|---|
| TC-01 | | | | | |
| TC-02 | | | | | |

### Defects raised

| Issue | Summary | Status |
|---|---|---|
| | | |

---

## Issue #9 — Integrated test pass

Part J uses this section. It is not one feature: it is the whole site tested
together, after every issue has merged. Cover navigation, all four pages, the
contact form, keyboard access, the console, and every width again.

Record the rows that passed as well as the ones that failed. An untested area
and a failed area look the same in an audit.

| ID | Area | What I did | Expected | Result | Notes |
|---|---|---|---|---|---|
| TC-01 | | | | | |

---

## Out of scope for Stage 1

- Automated tests. Stage 2 adds these as a GitHub Actions workflow.
- Server-side form handling. The contact form validates in the browser only.
- Screen-reader testing with NVDA or VoiceOver. Issue #8 covers the markup
  that makes it possible; testing it properly is beyond this stage.
