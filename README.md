# Assignment 1 — Simulated Annealing: Exam Timetable Scheduling

## Observation Report

**Student Name  :** Srinandhini
**Student ID    :** 2310040045
**Date Submitted:** 26 march 26

---

## How to Submit

1. Run each experiment following the instructions below
2. Fill in every answer box — do not leave placeholders
3. Make sure the `plots/` folder contains all required images
4. Commit this README and the `plots/` folder to your GitHub repo

---

## Before You Begin — Read the Code

**Q1. What does `count_clashes()` measure? What value means a perfect timetable?**

The `count_clashes()` function counts how many scheduling conflicts exist in the timetable. A clash occurs when a student has two exams assigned to the same time slot. A value of **0** means there are no conflicts and the timetable is perfect.

---

**Q2. What does `generate_neighbor()` do? How is the new timetable different from the current one?**

The `generate_neighbor()` function creates a slightly modified version of the current timetable. It randomly selects one exam and assigns it to a different time slot. This results in a small change that helps explore nearby solutions.

---

**Q3. In `run_sa()`, there is this line:**

```python
if delta < 0 or random.random() < math.exp(-delta / T):
```

**What does this line decide? Why does SA sometimes accept a worse solution?**

This line decides whether a new solution should be accepted. If the new solution is better, it is always accepted. If it is worse, it may still be accepted with a certain probability depending on the temperature. This helps the algorithm escape local minima and explore better solutions.

---

## Experiment 1 — Baseline Run

**Fill in this table:**

| Metric                             | Your result |
| ---------------------------------- | ----------- |
| Number of iterations completed     | 1379        |
| Clashes at iteration 1             | 12          |
| Final best clashes                 | 3           |
| Did SA reach 0 clashes? (Yes / No) | No          |

---

**Copy the printed timetable output here:**

```
Final Timetable
------------------------------------------
Slot 1:  Geography
Slot 2:  Chemistry, English
Slot 3:  History, Computer Science, Economics
Slot 4:  Biology, Statistics
Slot 5:  Mathematics, Physics
------------------------------------------
Total clashes : 3
```

---

**Plot observation:**

The graph shows a steep drop in clashes at the beginning, indicating rapid improvement in the early iterations. After this, the curve gradually flattens, showing slower improvements over time. This suggests that the algorithm is converging toward a near-optimal solution but does not reach zero clashes.

---

## Experiment 2 — Effect of Cooling Rate

**Results table:**

| cooling_rate | Final clashes | Iterations completed | Reached 0 clashes? |
| ------------ | ------------- | -------------------- | ------------------ |
| 0.80         | 8             | ~5000 (runs full)    | No                 |
| 0.95         | 3             | ~5000 (runs full)    | No                 |
| 0.995        | 3             | 1379 (early stop)    | No                 |

---

**Comparison of plots:**

With a fast cooling rate (0.80), the algorithm quickly reduces temperature and stops exploring early, leading to a poor solution with more clashes. With a moderate cooling rate (0.95), the performance improves and finds a better solution. With slow cooling (0.995), the algorithm explores more thoroughly and achieves a similar but more stable result. Slower cooling allows better exploration but may take more time.

---

**Best cooling rate:**

The best result is achieved with **0.995 (and also 0.95 gives similar result)**, as both produce the lowest number of clashes (3). The slower cooling rate works better because it allows more exploration and avoids getting stuck in poor solutions.

---

## Summary

| Experiment       | Key setting          | Final clashes | Main finding in one sentence                          |
| ---------------- | -------------------- | ------------- | ----------------------------------------------------- |
| 1 — Baseline     | cooling_rate = 0.995 | 3             | Slow cooling helps reach a good near-optimal solution |
| 2 — Cooling rate | cooling_rate = 0.995 | 3             | Slower cooling performs better than fast cooling      |

---

**Reflection:**

The most important thing I learned is that Simulated Annealing uses randomness and temperature to explore solutions effectively. At high temperatures, it explores widely, even accepting worse solutions. As the temperature decreases, it becomes more focused on improving the solution. The cooling rate is very important because it controls how long the algorithm explores. Slower cooling generally produces better solutions, while fast cooling may lead to suboptimal results.

---

## Submission Checklist

* [ ] Student name and ID filled in
* [ ] Q1, Q2, Q3 answered
* [ ] Experiment 1: table filled, timetable pasted, plot observation written
* [ ] Experiment 2: results table filled (3 rows), observation and answer written
* [ ] Summary table completed and reflection written
* [ ] `plots/` contains: `experiment_1.png`, `experiment_2a.png`, `experiment_2b.png`, `experiment_2c.png`
