# Metrics to Calculate


## Cycle Time

We can use multiple varying definitions:

#### Simple definitions straight from the data
1. In Progress Minutes
2. Resolution Time Minutes


#### Derived definitions

Start indicators:
1. Issue created timestamp
2. First transition to "In Progress"

End indicators:
1. Resolution Date (datetime)
2. First transition to "Done" (datetime)
3. Last transition to "Done"/Closed/Resolved

#### What do calculate:

CT1 = Resolution_Time_Minutes
CT2 = In_Progress_Minutes
CT3 = Resolution - Created
CT4 = Resolution - First_In_Progress_Timestamp
CT5 = Final_Done_Timestamp - First_In_Progress_Timestamp
CT6 = First_Done_Timestamp - First_In_Progress_Timestamp


#### First Pass of Data:

| Project  | Issues | Has start (`First_In_Progress`) | Has final done | Has both start + final done | Verdict           |
| -------- | -----: | ------------------------------: | -------------: | --------------------------: | ----------------- |
| SERVER   | 18,806 |                   9,647 (51.3%) | 16,029 (85.2%) |               9,248 (49.2%) | Usable            |
| MDL      |  8,521 |                   3,872 (45.4%) |  4,926 (57.8%) |               3,491 (41.0%) | Probably usable   |
| JRACLOUD |  5,433 |                      351 (6.5%) |  2,082 (38.3%) |                  287 (5.3%) | Not really usable |


#### Context Factors (do later)

1. Issue Type (Bug, Suggestion, Task, Improvement, New Feature)
2. Priority (Low, Medium, High, Critical)


## What the coverage says

### SERVER

* **CT3 = Resolution - Created**: 15,974 / 18,806 (**84.9%**)
* **CT4 = Resolution - First In Progress**: 9,215 / 18,806 (**49.0%**)
* **CT5 = Final Done - First In Progress**: 9,248 / 18,806 (**49.2%**)
* **CT6 = First Done - First In Progress**: 9,248 / 18,806 (**49.2%**)
* **CT2 > 0**: 8,645 / 18,806 (**46.0%**)

**Verdict:** ready.
SERVER can support both a resolution-based definition and a status-based definition.

---

### MDL

* **CT3**: 4,901 / 8,521 (**57.5%**)
* **CT4**: 3,489 / 8,521 (**40.9%**)
* **CT5**: 3,491 / 8,521 (**41.0%**)
* **CT6**: 3,491 / 8,521 (**41.0%**)
* **CT2 > 0**: 0 / 8,521 (**0.0%**)

**Verdict:** usable, but not with `In_Progress_Minutes`.
The status-derived cycle-time definitions are usable if you document the workflow mapping. `In_Progress_Minutes` is effectively useless here.

---

### JRACLOUD

* **CT3**: 1,646 / 5,433 (**30.3%**)
* **CT4**: 275 / 5,433 (**5.1%**)
* **CT5**: 287 / 5,433 (**5.3%**)
* **CT6**: 287 / 5,433 (**5.3%**)
* **CT2 > 0**: 218 / 5,433 (**4.0%**)

**Verdict:** not suitable for status-based cycle time.
Coverage is too low to treat CT4–CT6 as representative.

---

## The main conclusion

You are ready to calculate cycle time, but not with one single definition across all projects.

A defensible setup would be:

* **CT3** for all three projects as a broad baseline
* **CT5** and **CT6** for **SERVER** and **MDL**
* exclude **JRACLOUD** from status-based cycle-time analysis, or treat it as a negative case showing that some Jira workflows do not support this metric well

That is actually a strong robustness result, not a failure.

---

## Important correction to expectations

These are **not** safely true:

* `CT3 should be equal to CT1`
* `CT4 should be equal to CT2`

Your mismatch counts are large:

* **SERVER**: `CT1_vs_CT3_mismatch = 10,000`
* **MDL**: `3,524`
* **JRACLOUD**: `645`

and

* **SERVER**: `CT2_vs_CT4_mismatch = 9,147`
* **MDL**: `3,489`
* **JRACLOUD**: `233`

---
