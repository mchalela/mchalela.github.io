---
title: "Five tests that pass but check nothing"
summary: "Patterns I keep finding in AI-generated test suites, and what to look for before trusting a green run."
date: 2026-11-06
tags: ["pytest", "code review", "ai-generated code"]
categories: ["Testing"]
showComments: true
---

*Sample post, written to test the theme. Comments at the bottom are served by giscus once the repo ids are filled in.*

A green test run is only evidence if the tests could have failed. When I review generated code, these are the five patterns that most often make a suite look healthier than it is.

## 1. The assertion-free test

```python
def test_load_catalog():
    load_catalog("data/sample.fits")
```

It only checks that the function does not raise. Add an assertion on the shape, the units, or a known value.

## 2. Asserting the mock

```python
def test_fetch(mocker):
    mocker.patch("client.get", return_value={"ok": True})
    assert fetch() == {"ok": True}
```

The test proves the mock returns what the mock was told to return. The code under test was never exercised.

## 3. `assert result is not None`

True for nearly every object in Python. It is the test-suite equivalent of a shrug.

## 4. Tolerances wide enough to drive through

```python
assert abs(flux - expected) < 1e3
```

For a quantity of order one, this passes for any answer. Pick the tolerance from the numerical method, not from whatever made the test go green.

## 5. Tests that re-implement the function

When the expected value is computed by the same formula the function uses, a bug in the formula is reproduced in the test and both agree. Expected values should come from somewhere independent: a reference implementation, a hand calculation, a published number.

The common thread is that each test *could not fail*. The quickest way I know to spot them is to break the code on purpose and watch which tests stay green. [pytest-deck](/software/pytest-deck/) makes that loop fast enough to do routinely.
