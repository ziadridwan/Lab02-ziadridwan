# Lab 02 - Basic Python: Variables, Conditionals, and Loops

In this lab, we'll practise the building blocks from this week's lectures: storing
values in variables, doing arithmetic, making decisions with conditionals
(`if` / `elif` / `else`), and repeating work with loops. You'll write four small
functions and check them against a set of automated tests.

**Time:** this lab is meant to be finished in the 80-minute session. If you don't
finish, you may keep working during the week and submit any time up to the **first 10
minutes of next week's lab**.  After 10 minutes, though, the lab will not be accepted, 
to avoid a cascade effect. The **Lab 02 quiz on Canvas** closes at that moment - that is
where you hand this lab in, so read [How to Submit](#how-to-submit) before you start.

## Getting Started

Lab repositories are **templates**: you make your own copy with one click.

1. Open the **Lab 02 template** link in the Canvas lab quiz.
2. Click the green **Use this template** button, then **Create a new repository**.
3. Fill in the form:
   - **Owner:** Your own account
   - **Repository name:** `lab02-csci1030u`
   - **Visibility:** **Private**
4. Click **Create repository**.

Use **Use this template**, not **Fork** - a fork can never be made private, which would
show your solution to the whole class.

> From this lab on, every lab repository is **private**.
> Your classmates cannot see it; your TA will need to be added as a collaborator in order to see it.

Then clone it. On your new repo's page, click the green **Code** button and copy the URL.
In the folder where you keep your CSCI 1030U labs:

```
git clone https://github.com/CSCI1030U/lab02-your-username
cd lab02-your-username
```

## Instructions

You will edit **`lab02.py`**. The four function definitions are already written for
you - **do not rename them or change their arguments**, because the tests call them by
name. Replace each `pass` with your code, and use **`return`** to send the answer back
(not `print`).

### Part 1 - `seconds_to_hms(total_seconds)`

Write the body of `seconds_to_hms`, which takes a whole number of seconds and returns
a string in the format `"H:MM:SS"` - hours, then minutes and seconds each padded to
two digits.

Hints: integer division `//` and remainder `%` are useful, here. There are 3600 seconds
in an hour and 60 in a minute. An f-string like `f"{minutes:02d}"` pads an integer to two
digits.

```python
seconds_to_hms(3661)   # returns "1:01:01"
seconds_to_hms(59)     # returns "0:00:59"
seconds_to_hms(7325)   # returns "2:02:05"
```

### Part 2 - `admission_price(age)`

Write the body of `admission_price`, which takes a person's `age` and returns a movie
ticket price (a float) according to this table:

| Age | Price |
|---|---|
| under 5 | $0.00 |
| 5 to 12 | $8.00 |
| 13 to 64 | $15.00 |
| 65 and over | $10.00 |

Use an `if` / `elif` / `else` chain. Watch the boundaries: a 5-year-old pays $8.00, a
12-year-old pays $8.00, a 13-year-old pays $15.00, and a 65-year-old pays $10.00.

```python
admission_price(3)    # returns 0.0
admission_price(10)   # returns 8.0
admission_price(30)   # returns 15.0
admission_price(70)   # returns 10.0
```

### Part 3 - `sum_multiples(limit)`

Write the body of `sum_multiples`, which returns the sum of every whole number below
`limit` that is a multiple of 3 or a multiple of 5. Use a `for` loop over `range(limit)` and
keep a running total.

For example, below 10 the multiples of 3 or 5 are 3, 5, 6, and 9, which add up to 23.

```python
sum_multiples(10)   # returns 23
sum_multiples(20)   # returns 78
sum_multiples(1)    # returns 0
```

### Part 4 - `total_of_positives(numbers)`  (stretch - optional)

Write the body of `total_of_positives`, which takes a list of numbers and returns
the sum of only the ones that are greater than zero. Loop through the list and add
up the positives.

```python
total_of_positives([1, -2, 3, -4, 5])   # returns 9
total_of_positives([-1, -2])            # returns 0
total_of_positives([10, 20])            # returns 30
```

## Verifying Correctness

Run the pre-written tests to check your work:

```
pytest
```

Read the output closely - a failing test tells you which function is wrong and shows
what it expected versus what your code returned. Fix, save, and run `pytest` again.

## Getting Help

There is a lab instructor present for the whole session. Ask them whenever you're
stuck.

*The instructor will usually help you find the problem rather than tell you how to
fix it - the goal is for you to get better at diagnosing and fixing your own bugs.*

## How to Submit

Handing in a lab is two steps: **push your work**, then **record it in the Canvas quiz**.
This is the same routine for every lab from here on.

### Step 1 - Commit and push

Once your tests pass (or the session is ending):

```
git add --all
git commit -m "Lab 02 completed"
git push origin main
```

Then open your repository page on GitHub and check that your changed files are actually
there. That is your confirmation the push worked.

> **Check your own work with `pytest`, on your own machine.** Your repository has an
> autograder, but it does not run when you push - your instructor runs it during marking,
> against the commit hash you submit below. So `pytest` passing locally is the only
> pass/fail signal you get, and it is the one that counts. Don't submit without running it.

### Step 2 - Get the commit hash

Check that everything really is committed and pushed, then read the hash of that snapshot:

```
git status
git rev-parse HEAD
```

`git status` should say `nothing to commit, working tree clean` and that your branch is up
to date with `origin/main`. If it lists changes, go back to Step 1. Then `git rev-parse HEAD`
prints a 40-character hash, like `3f9a1c2e8b7d4056a1f2e3d4c5b6a7f8091a2b3c`.

### Step 3 - Submit the quiz

Open the **Lab 02 quiz on Canvas** and enter:

- your **repository URL**: `https://github.com/CSCI1030U/lab02-your-username`
- your **commit hash**, pasted exactly as `git rev-parse HEAD` printed it

Then answer the remaining questions and submit. **The Canvas submission time is your
submission time**, and the commit hash you give is the snapshot that gets marked - anything
you push afterwards is not seen. If you fix something important later, get the new hash and
resubmit if the quiz still allows it.

## Using AI

You may use an AI assistant to **explain ideas and help you learn** - but **not to
generate code you submit** in this half of the term. Use only a **free** model, and be
ready to explain every line you wrote; the lab instructor may ask you to walk through
your code.
