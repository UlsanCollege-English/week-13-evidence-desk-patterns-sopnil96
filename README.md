[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/cm6PS4yt)
# Week 1 Homework: Evidence Desk Patterns

## Student Name

Sopnil

## Summary

This homework asks you to practice core data structure patterns in Python by solving problems set in a detective/evidence desk theme. You will use frequency counting with dictionaries to tally evidence labels, duplicate detection with sets to find repeated suspect IDs, stack matching with a list to validate nested bracket tags, and lookup tables with dictionaries to resolve criminal aliases. Two optional challenges extend the practice to queue processing with `collections.deque` and a sorting-plus-scan pattern to find the largest time gap between events.

## How to Run Tests

From the repository root, run:

```bash
pytest -q
```

To run one test file:

```bash
pytest -q tests/test_challenges.py
```

## Required Problems

Complete these functions in `src/challenges.py`:

1. `count_evidence`
2. `first_repeated_id`
3. `valid_tags`
4. `lookup_alias`

## Optional Challenges

These are extra practice unless your instructor tells you otherwise:

1. `process_reports`
2. `largest_time_gap`

Optional tests are skipped by default. To run them, remove the `@pytest.mark.skip(...)` line above the optional test you want to check.

---

# Problem Notes

## 1. Evidence Counter

### Pattern

Frequency counting

### Data Structure

Dictionary (`dict`)

### Approach

- Step 1: Create an empty dictionary to store label counts.
- Step 2: Loop through each item in the evidence list.
- Step 3: If the item is already a key, increment its count by 1; otherwise set it to 1. Return the dictionary.

### Complexity

- Time: `O(n)`
- Space: `O(k)`

`n` is the number of items in the list. We visit each item once, so time is linear. `k` is the number of unique labels; in the worst case `k = n`, so space is also linear.

### Edge Cases Checked

- [x] Empty list
- [x] One item
- [x] Repeated items
- [x] Different labels

---

## 2. Repeat Suspect ID

### Pattern

Seen-before detection

### Data Structure

Set (`set`)

### Approach

- Step 1: Create an empty set called `seen`.
- Step 2: Loop through each ID in the list.
- Step 3: If the ID is already in `seen`, return it immediately; otherwise add it to `seen`. Return `None` after the loop if no repeat was found.

### Complexity

- Time: `O(n)`
- Space: `O(n)`

Set membership checks are O(1) on average, so the loop runs in O(n) total. In the worst case (no repeats) the set holds all `n` IDs.

### Edge Cases Checked

- [x] Empty list
- [x] No repeated IDs
- [x] First two IDs match
- [x] Multiple repeated IDs

---

## 3. Evidence Tag Validator

### Pattern

Stack matching

### Data Structure

List used as a stack (`list`)

### Approach

- Step 1: Create an empty stack and a dictionary that maps each closing bracket to its matching opening bracket.
- Step 2: Loop through each character; push opening brackets onto the stack. For closing brackets, check that the top of the stack holds the correct opener — return `False` immediately if not, otherwise pop the stack.
- Step 3: After the loop, return `True` only if the stack is empty (every opener was closed).

### Complexity

- Time: `O(n)`
- Space: `O(n)`

Each character is visited once. In the worst case (all opening brackets) the stack holds `n` items.

### Edge Cases Checked

- [x] Empty string
- [x] Correctly nested tags
- [x] Mismatched tags
- [x] Closing tag before opening tag
- [x] Unclosed opening tag
- [x] Non-bracket characters

---

## 4. Alias Directory

### Pattern

Lookup table

### Data Structure

Dictionary (`dict`)

### Approach

- Step 1: Use `dict.get(alias, None)` to look up the alias key in the dictionary.
- Step 2: Return the value if it exists, or `None` if it does not.

### Complexity

- Time: `O(1)`
- Space: `O(1)`

Dictionary lookup is O(1) on average. No extra space is used beyond the input dictionary.

### Edge Cases Checked

- [x] Known alias
- [x] Unknown alias
- [x] Empty dictionary

---

# Assistance & Sources

## AI Used?

- [x] Yes
- [ ] No

## If yes, what did AI help with?

- Helped structure the step-by-step approach for each problem following the TODO comments.
- Explained the time and space complexity for each solution.
- Assisted with writing the README documentation.

## Other Sources

None.
