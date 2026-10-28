# Mistakes Log

This file is for tracking SQL mistakes, fixes, and lessons learned.

## Date
- 2026-10-28

## Mistake 1
- Date: 2026-10-28
- Query/Task: Find agents with no team assigned
- Mistake: `WHERE team = NULL` returned zero rows, with no error
- Why it happened: NULL means "unknown", so `= NULL` is never true
- Correct SQL: `WHERE team IS NULL`
- Learning: Use IS NULL / IS NOT NULL. `= NULL` fails silently.

## Mistake 2
- Date: 2026-10-28
- Query/Task: Suspended accounts from Egypt or Italy
- Mistake: Left out the country filter entirely and used `status IS 'suspended'`
- Why it happened: I didn't re-read every filter in the question, and I used IS instead of =
- Correct SQL: `WHERE country IN ('Egypt', 'Italy') AND status = 'suspended'`
- Learning: Tick off every condition in the question before running. Use = for values, IS for NULL.

## Mistake 3
- Date: 2026-10-28
- Query/Task: Same Egypt/Italy question, written with OR
- Mistake: `country = 'Egypt' OR country = 'Italy' AND status = 'suspended'`
- Why it happened: AND is evaluated before OR, so status only applied to Italy
- Correct SQL: `WHERE (country = 'Egypt' OR country = 'Italy') AND status = 'suspended'`
- Learning: Always add parentheses when mixing AND and OR.

## Mistake 4
- Problem:
- Cause:
- Fix:
- Lesson:

## Mistake 5
- Problem:
- Cause:
- Fix:
- Lesson:

## Common SQL Mistakes to Watch For
- Using SELECT * instead of only needed columns
- Forgetting GROUP BY after aggregation
- Comparing NULL values incorrectly
- Joining tables without proper keys
- Missing aliases or ambiguous column names
- Ignoring indexes on large tables
- Using subqueries when JOIN is clearer
- Not checking data types before calculations

## Quick Notes
- Always test with small data first
- Validate assumptions before writing the final query
- Read the query plan when performance is slow
- Keep a record of what failed and why

## Template
- Date:
- Query/Task:
- Mistake:
- Why it happened:
- Correct SQL:
- Result:
- Learning:
