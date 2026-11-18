# Day 0: Entry Gate and Baseline Assessment

> **Purpose:** Record my honest starting point *before* learning anything, so real progress can be measured later.
> **Rules followed:** Baseline answered from memory only. No Googling, no AI help. Corrections were made after review and are marked as revisions.

| Item | Detail |
|---|---|
| Date | 2026-11-18 |
| Status | Day 0 complete ✓ (revised after review) |
| Next step | Day 1: Data Analyst Mindset |

---

## B1. Self-Rating (Mastery Scale, Level 0 to 5)

| Level | Meaning |
|---:|---|
| 0 | No understanding |
| 1 | I recognize the concept |
| 2 | I can explain it with help |
| 3 | I can apply it with guidance |
| 4 | I can independently apply it |
| 5 | I can apply, explain, troubleshoot, evaluate limitations, and teach it |

| Skill | Self-rated start |
|---|:---:|
| Excel | 3 |
| SQL | 2 |
| Statistics | 3 |
| Python | 2 |
| Pandas | 1 |
| Data Visualization | 2 |
| Power BI | 0 |
| Git / GitHub | 4 |
| Financial Concepts | 0 |
| Football Metrics | 3 |

> Self-assessed only. These will be compared with assessed results, and any gap goes into `progress/mistakes-log.md`.

---

## B2. Baseline Questions

### Q1. Row, column and grain

**First answer:** Row = horizontal values, column = vertical values, grain = smallest part of the dataset.

**Revised after review:**
- A row is a **record**. A column is a **variable**.
- **Grain** tells exactly what one row represents.
- Football example: one row = one player's performance in one match (player ID + match ID).
- Bank example: one row = one individual transaction (transaction ID).

**Review note:** Correct. Remember that grain is the *level of detail* of a row, not simply "the smallest part".

### Q2. Which player is the better finisher?

**First answer:** The player with 6 goals in 900 minutes, based on the given information. Goals per minute is needed. Shots taken would help for advanced metrics.

**Revised after review:**

| Player | Calculation | Goals per 90 |
|---|---|---:|
| Player 1 | (10 / 2000) x 90 | 0.45 |
| Player 2 | (6 / 900) x 90 | 0.60 |

- 900 minutes may be too few to trust, because a few goals or missed chances can change the rate a lot.
- My reasoning: a smart finisher chooses his shots well, so shots taken matter.

**Review note:** Calculations are correct. Goals per 90 is a **scoring rate**, not a measure of **finishing quality**. Finishing compares goals scored with the quality of chances taken (xG). Shot selection and finishing are two different things. This is revisited on Football Day A6.

### Q3. Average loan Rs. 500,000 but most loans Rs. 100,000

**Answer:** A few very large loans pull the mean up (skew). The **median** gives the typical value and is much less sensitive to extreme values.

**Review note:** Correct.

### Q4. SQL JOIN

**Answer:** A JOIN matches rows from two tables using a common or related column, usually a primary key in one table and a foreign key in the other. Example: student ID is the primary key in the student table and a foreign key in the course-enrollment table.

**Review note:** Correct.

### Q5. Sales rose 20%: questions before saying "sales are improving"

My questions:
1. Did costs also increase?
2. What profit was made from the sales, or did it lead to a loss?
3. Was supply high, so that sales rose?
4. Over what time period did sales rise?
5. What is the sales figure in absolute numbers and volume, not only a percentage?
6. Was it a peak season or a low season?
7. Is the percentage figure real?

**Review note:** Good business instincts (cost, profit, absolute numbers, seasonality). Two points to revisit:
- Question 7 is too vague. What could make a sales figure *not real*? (Hint: returns, cancelled orders, refunds, duplicate records.)
- Still missing: **20% compared to what?** (last month, last year, a target?)

Carry-over: rewrite Q5 item 7 after Day 1.

---

## B3. My "Why"

For me, Data Analytics is one of my major topics of interest. Whenever I see something called data, I like to understand why it is the way it is, what it implies, and how data represents a real system.

By finance I mean financial institutions such as banks, co-operatives and fintechs. In the context of Nepal this area is still largely overlooked. If I explore it, I can see how these institutions work with data and how that data is used for financial research and financial decisions.

Football is my love. I enjoy watching it not only physically but statistically. I want to know how a striker or a midfielder performed, who is closest to a given metric, and how it all works out. I also want to understand how real sports organizations scout: is it through the kind of metrics I only see on Transfermarkt, or does it work differently?

Success for me means creating projects, using them well, and standing out in a competitive job market, knowing what I want to achieve and how to achieve it. I want to be good enough that when I am suddenly asked what some data means, I can work it out.

**Measurable success target:** 2 published projects that I can explain comfortably in an interview.

---

## Part C. Tool Check

| Tool | Status | Notes / Plan |
|---|:---:|---|
| Git | ✅ | 2.46.0.windows.1 |
| GitHub | ✅ | Account and profile README done |
| Excel | ✅ | Desktop, Excel 2016 (no XLOOKUP or dynamic arrays; use VLOOKUP and INDEX-MATCH) |
| Google Sheets | ✅ | Backup |
| Python | ✅ | 3.13.7 |
| VS Code | ✅ | |
| Jupyter | ✅ | |
| PostgreSQL | ⬜ | Install and test **before Day 10** |
| pgAdmin / DBeaver | ⬜ | Install and test **before Day 10** |
| Power BI Desktop | ⬜ | Install **before Day 46** |

**Operating system:** Windows

---

## Part D. Time Budget

| Item | Answer |
|---|---|
| Daily study time | Target 4 hours/day |
| Busy period | About 2 weeks of exams, dates to be set later |
| Target finish | About 3 months |

> Planning rule: the 3-month target is a goal, not a rule. If a day's assessment is not passed, the day stays open. Dates will be adjusted once the exam schedule is known.

---

## Day 0 Deliverables

- [x] Repository created and public
- [x] README with all required sections
- [x] Baseline self-rating (B1)
- [x] Baseline questions (B2), revised after review
- [x] "Why" statement with measurable target (B3)
- [x] Tool check (Part C)
- [x] Time budget (Part D)
- [x] Day 0 approved
