# QA Manual Testing Portfolio — OrangeHRM

![Status](https://img.shields.io/badge/Status-Completed-brightgreen)
![Test Cases](https://img.shields.io/badge/Test%20Cases-25-blue)
![Bugs Found](https://img.shields.io/badge/Bugs%20Found-2-red)
![Pass Rate](https://img.shields.io/badge/Pass%20Rate-96%25-green)

A complete manual QA testing project for the OrangeHRM demo application,
covering test planning, test case design and execution, bug reporting,
and exploratory testing.

---

## Project Overview

| Item | Detail |
|---|---|
| **Application tested** | OrangeHRM Demo |
| **URL** | https://opensource-demo.orangehrmlive.com |
| **Testing type** | Manual black-box testing |
| **Modules covered** | Login, User Management, My Info |
| **Total test cases** | 25 |
| **Passed** | 24 |
| **Failed** | 1 |
| **Bugs found** | 2 |
| **Pass rate** | 96% |

---

## Repository Structure

```
qa-portfolio-orangehrm/
├── test-plan/
│   └── TEST_PLAN.md
├── test-cases/
│   └── LOGIN_TEST_CASES.md
├── bug-reports/
│   ├── BUG_001.md
│   ├── BUG_002.md
│   └── screenshots/
│       ├── BUG_001.png
│       └── BUG_002.png
└── exploratory-notes/
    └── EXPLORATORY_NOTES.md
```

---

## Test Execution Summary

### Login Module — 15 Test Cases

| ID | Title | Priority | Status |
|---|---|---|---|
| TC_001 | Login with valid credentials | High | ✅ Pass |
| TC_002 | Login with wrong password | High | ✅ Pass |
| TC_003 | Login with wrong username | High | ✅ Pass |
| TC_004 | Login with both fields empty | High | ✅ Pass |
| TC_005 | Login with username only | Medium | ✅ Pass |
| TC_006 | Login with password only | Medium | ✅ Pass |
| TC_007 | Password field is masked | Medium | ✅ Pass |
| TC_008 | Logout works correctly | High | ✅ Pass |
| TC_009 | Back button after logout | Medium | ❌ Fail |
| TC_010 | Login succeeds after a failed attempt | High | ✅ Pass |
| TC_011 | Forgot Password link is visible | Low | ✅ Pass |
| TC_012 | Forgot Password sends reset email | Medium | ✅ Pass |
| TC_013 | SQL injection in username field | High | ✅ Pass |
| TC_014 | Very long username input | Medium | ✅ Pass |
| TC_015 | Spaces only in username | Medium | ✅ Pass |

### User Management Module — 10 Test Cases

| ID | Title | Priority | Status |
|---|---|---|---|
| TC_016 | View user list | High | ✅ Pass |
| TC_017 | Search user by username | High | ✅ Pass |
| TC_018 | Search returns no results | Medium | ✅ Pass |
| TC_019 | Add new user with valid data | High | ✅ Pass |
| TC_020 | Add user with duplicate username | High | ✅ Pass |
| TC_021 | Add user with mismatched passwords | High | ✅ Pass |
| TC_022 | Add user with empty username | Medium | ✅ Pass |
| TC_023 | Add user with password too short | Medium | ✅ Pass |
| TC_024 | Delete an existing user | High | ✅ Pass |
| TC_025 | Reset search filters after searching | Low | ✅ Pass |

---

## Bugs Found

### BUG_001 — Dashboard loads after logout via browser Back button

| Field | Detail |
|---|---|
| **Module** | Login / Session Management |
| **Severity** | Medium |
| **Priority** | Medium |
| **Status** | Open |

**Steps to reproduce:**
1. Login with Admin / admin123
2. Logout via the user menu
3. Press the browser Back button

**Expected:** Login page stays visible. Dashboard not accessible after logout.

**Actual:** Dashboard page loads visually after pressing Back. Clicking
any links redirects back to login but the page briefly appears, which
could confuse users into thinking they are still logged in.

[View screenshot](./bug-reports/screenshots/BUG_001.png)

---

### BUG_002 — Date of Birth accepts today's date with no validation error

| Field | Detail |
|---|---|
| **Module** | My Info → Personal Details |
| **Severity** | Medium |
| **Priority** | Low |
| **Status** | Open |

**Steps to reproduce:**
1. Login with Admin / admin123
2. Go to My Info → Personal Details
3. Set Date of Birth to today's date
4. Click Save

**Expected:** Validation error shown. Today's date should not be a valid
date of birth — a person cannot be 0 days old.

**Actual:** Record saved successfully with no validation error. Note: future
dates are correctly blocked by the date picker, meaning validation is
partial — only today's date slips through.

[View screenshot](./bug-reports/screenshots/BUG_002.png)

---

## Exploratory Testing

Unscripted exploratory testing was conducted on the My Info module after
scripted test execution. Key areas explored:

- Special characters and numbers in name fields
- Empty required fields on the Personal Details form
- Very long text input in text fields
- Date field boundary testing — today's date and future dates

**Key finding:** BUG_002 was discovered during this session, not from any
scripted test case. This highlights the value of exploratory testing
alongside scripted execution.

Full session notes available in [exploratory-notes/EXPLORATORY_NOTES.md](./exploratory-notes/EXPLORATORY_NOTES.md)

---

## Tools Used

| Tool | Purpose |
|---|---|
| Chrome 146.0.7680.80 (arm64) | Test execution browser |
| macOS Tahoe 26.3.1 | Operating system |
| Google Sheets | Test case management and execution tracking |
| GitHub | Version control and portfolio hosting |
| Markdown | Documentation |

---

## What I Learned

- Negative and edge case testing is where real bugs hide — 8 of my 15
  login test cases were negative or edge cases
- Exploratory testing found BUG_002, which no scripted test case would
  have caught
- Session management is a commonly overlooked area — TC_009 revealed the
  app does not fully clear browser cache on logout
- Partial validation (BUG_002) can be more misleading than no validation
  because it creates a false sense of security

---

## Author

**Narayan Thapa**
QA Engineer in Training | Manual Testing | Exploratory Testing

[GitHub Profile](https://github.com/t-rayan)

---

*All testing was performed on the publicly available OrangeHRM demo environment.*
