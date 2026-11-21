# SC2 Test Log — Functional vs. Non-Functional

Record one row per check as you run the lab. Fill the shaded example row first,
then your own results.

## Test results

| # | Check | Type (Functional / Non-functional) | Input / Condition | Expected result | Actual result | Pass / Fail |
|---|-------|-----------------------------------|-------------------|-----------------|---------------|-------------|
| 0 | *Example: search returns matches* | *Functional* | *Search term: `Testing`* | *Only courses matching "Testing" are listed* | *3 matching cards shown* | *Pass* |
| 1 | Search returns matching courses | Functional | Search term: `Testing` | Only courses matching "Testing" are listed | 12 matching course cards shown | Pass |
| 2 | `/api/courses` response time | | Same search re-run, Network tab open | Under ~1000 ms for a responsive product | Measured: `3030` ms (`3.03 s`) | Fail |
| 3 | Layout below ~768 px width | Non-functional | Window width: `680` px | Cards stack cleanly, nothing overflows | Cards appear side by side at 680 px instead of stacking cleanly | Fail |
| 4 | Layout at 768 px or wider | Non-functional | Window width: `800` px | Grid displays correctly | Multi-column grid displays cleanly with cards side by side | Pass |

## STLC mapping

One sentence per check: which STLC phase produced the observation, and why.

| Check | STLC phase | Why |
|-------|-----------|-----|
| 1 | Test Execution | We actively ran the search feature with the test input (`Testing`) in the live application and compared the actual course cards displayed against the expected functional requirement. |
| 2 | Test Execution | We executed the search request in the running environment while monitoring the Network tab to measure actual API response time against our non-functional performance threshold (`< 1000 ms`). |
| 3 | Test Execution | We ran a responsive layout test in the browser at a narrow viewport (`680 px`) and observed the actual UI rendering defect compared to the expected mobile stacking behavior. |
## Wrap-up answers

1. Which check was **functional**, and why?
   Check 1 (Search returns matching courses) was functional because it verified *what* the system does—specifically, whether entering a search term filters and returns the correct matching course records according to business logic.

2. Which two checks were **non-functional**, and why?
   Checks 2 (`/api/courses` response time) and 3 (Layout below ~768 px width) were non-functional (along with Check 4) because they evaluated *how well* the system performs and behaves under operational conditions—measuring speed/responsiveness (performance) and screen-size adaptability (usability/responsive design) rather than core feature logic.

3. Can a feature pass functional testing and still have problems? Use your
   measured response time or the broken narrow layout as evidence.
   Yes—a feature can pass functional testing and still deliver a poor or broken user experience. In this lab, the search feature passed functional testing (Check 1) by returning the right courses, yet `/api/courses` took `3.03 s` (`3030 ms`) to respond—more than three times slower than the `1000 ms` responsiveness target—and the course cards failed to stack cleanly at `680 px` width, showing that functional correctness alone does not guarantee good performance or usability.
