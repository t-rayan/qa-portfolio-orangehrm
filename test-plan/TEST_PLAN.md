# Test Plan — OrangeHRM Demo

**Prepared by:** Narayan Thapa  
**Date:** 24/03/2026 
**Version:** 1.0

---

## 1. Introduction

This test plan covers manual functional testing of the OrangeHRM 
demo application. Testing focuses on the Login module and User 
Management module — the two most critical areas for an HR system.

**Application under test:** OrangeHRM Demo  
**URL:** https://opensource-demo.orangehrmlive.com  
**Login:** Admin / admin123  
**Test environment:** Chrome [Version 146.0.7680.80 (Official Build) (arm64)], [macOS Tahoe Version 26.3.1]

---

## 2. Scope

### In Scope
- Login and logout functionality
- Admin → User Management (add, search, edit, delete users)
- My Info → Personal details (view and edit)

### Out of Scope
- Leave management module
- Performance module  
- Recruitment module
- Mobile / tablet testing
- Performance / load testing

---

## 3. Test Approach

Manual black-box testing. Test cases cover positive, negative, 
and edge case scenarios. Exploratory testing will follow 
scripted execution to discover unexpected defects.

**Testing types used:**
- Functional testing (does each feature work?)
- Negative testing (what happens with invalid inputs?)
- Boundary value analysis (field length limits)
- Exploratory testing (unscripted, curiosity-driven)

---

## 4. Entry Criteria
- OrangeHRM demo site is accessible at the URL above
- Admin/admin123 credentials are working
- All test cases are written before execution begins

## 5. Exit Criteria
- 100% of planned test cases executed
- All Critical and High severity bugs are documented
- Test summary added to this document

---

## 6. Test Schedule

| Phase | Activity | Duration |
|---|---|---|
| Day 1–2 | Write test plan and test cases | 2 days |
| Day 3–5 | Execute test cases, log results | 3 days |
| Day 6–7 | Write bug reports with screenshots | 2 days |
| Day 8 | Create RTM | 1 day |
| Day 9–10 | Exploratory testing + notes | 2 days |

---

## 7. Risks & Mitigations

| Risk | Mitigation |
|---|---|
| Demo site is shared — data may change | Take screenshots of all bugs immediately |
| Demo site goes down temporarily | Re-test the next day |
| Shared admin account may be modified by others | Reset steps and re-execute if data looks wrong |

---

## 8. Deliverables

| # | Deliverable | Location |
|---|---|---|
| 1 | Test Plan | test-plan/TEST_PLAN.md |
| 2 | Test Cases | test-cases/ |
| 3 | Bug Reports | bug-reports/ |
| 4 | RTM | test-cases/RTM.md |
| 5 | Exploratory Notes | exploratory-notes/ |
