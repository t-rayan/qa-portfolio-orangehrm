# Exploratory Testing Notes — OrangeHRM Demo

**Tester:** Narayan Thapa
**Date:** 25/03/2026
**Duration:** 40–45 minutes
**Module explored:** My Info → Personal Details
**Environment:** Chrome 146.0.7680.80 (arm64), macOS Tahoe 26.3.1

---

## Session Goal

Explore the My Info module without a script to discover
defects that scripted test cases may not cover. Focus on
data validation, field boundaries, and unexpected inputs.

---

## What I Explored

### 1. Date of Birth field — boundary testing

**What I tried:**
- Set DOB to today's date and clicked Save
- Tried selecting future dates from the date picker

**What I found:**
- Today's date was accepted with a success message — no
  validation error shown
- Future dates were correctly blocked by the date picker
  (dates beyond 2026 not selectable)

**Verdict:** BUG — today's date should not be a valid DOB.
Logged as **BUG_002**.

---

### 2. Employee Full Name fields — special character testing

**Fields tested:**
- First Name
- Middle Name
- Last Name

**What I tried:**
Entered special characters mixed with letters in all three
name fields:
- First Name: `manda@%`
- Middle Name: `akhil##$`
- Last Name: `%^^usera&&`

Clicked Save after entering all three values.

**What I found:**
All three fields accepted the special character input and
saved successfully. A success message was shown. The values
were stored and displayed exactly as entered — including
the special characters.

**Verdict:** BUG — name fields should only accept alphabets,
spaces, hyphens, and apostrophes (for names like O'Brien
or Mary-Jane). Characters like `@`, `%`, `#`, `$`, `^`,
`&` are not valid in a person's name and should be
rejected with a validation error.

**Severity:** Medium — invalid data is being saved to the
database which could cause issues in generated reports,
payroll documents, or any system that uses employee names.

**Priority:** Medium

> Note: This bug was not in the original scripted test
> cases — it was discovered purely through exploratory
> testing. This shows the value of unscripted exploration
> alongside scripted execution.

---

## Summary of Findings

| # | Area | What I tried | Finding | Bug? |
|---|---|---|---|---|
| 1 | DOB field | Set to today's date | Accepted with no error | ✅ Yes — BUG_002 |
| 2 | DOB field | Set to future date | Correctly blocked | ✅ No — works correctly |
| 3 | First Name | `manda@%` | Accepted and saved | ✅ Yes — BUG_003 |
| 4 | Middle Name | `akhil##$` | Accepted and saved | ✅ Yes — BUG_003 |
| 5 | Last Name | `%^^usera&&` | Accepted and saved | ✅ Yes — BUG_003 |

---

## Bugs Raised from This Session

| Bug ID | Title | Severity |
|---|---|---|
| BUG_002 | DOB accepts today's date with no validation | Medium |
| BUG_003 | Name fields accept special characters | Medium |

---

## Observations (Not Bugs)

- The date picker UI is clean and future dates are
  correctly disabled — partial validation is in place
- The Save button gives clear feedback with a green
  success message when data is saved
- The form does not auto-clear after saving — values
  remain visible which is good UX

---

## What I Would Explore Next (Given More Time)

- Paste a 500+ character string into name fields
- Test the Contact Details tab in My Info
- Test Emergency Contacts section
- Try uploading an invalid file type as a profile photo
- Test all date fields (not just DOB) for the same
  today's date issue
