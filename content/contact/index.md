---
title: "Contact"
description: "What I do for clients, how a contract works, and how to reach me."
showTableOfContents: true
showComments: false
---

I work with research groups, startups and engineering teams that have scientific Python code they need to trust. Fixed-price or hourly, English or Spanish, replies within a day.

## Get in touch

- Email: tinchochalela@gmail.com
- Upwork: [upwork.com/freelancers/mchalela](https://www.upwork.com/freelancers/mchalela)
- LinkedIn: [linkedin.com/in/martinchalela](https://linkedin.com/in/martinchalela)
- GitHub: [github.com/mchalela](https://github.com/mchalela)

## What I do

### Testing and CI

Write a pytest suite for an existing codebase: fixtures, parametrisation, coverage reports, and tests that document what the code is supposed to do. Set up GitHub Actions with matrix testing, linting, type checks and coverage gates, plus tox or nox for local runs.

### AI-generated code rescue

Code from Cursor, Lovable, Replit or Copilot often works on the happy path and nowhere else. I review it with [pytest-deck](/software/pytest-deck/), find the untested paths, silent failures and tests that pass but check nothing, and fix them with the tests as the safety net.

### Scientific and numerical code

NumPy, SciPy, Numba, Astropy. Profiling and optimisation with a regression suite that proves the results did not change. Image and signal processing, spectroscopy, Monte Carlo and Bayesian pipelines.

### Legacy and MATLAB migration

MATLAB or Python 2 code ported to modern Python, reproduced to numerical precision, and delivered as an installable package with tests and documentation.

## Client work

**MATLAB to Python port of a scientific analysis codebase.** Ported a client's MATLAB code to NumPy and SciPy, reproducing the results to numerical precision, with a pytest suite checking every function against the MATLAB outputs. Five-star review: "Martin is really incredibly skilled in programming, both in Python and Matlab. His programming skills are at a very professional level and his attention to detail makes it even more valuable."

**Profiling and optimisation of numerical Python code.** Found the hot spots in a client's numerical functions and rewrote them with vectorised NumPy and Numba, results verified by a regression suite, with a short report so the team could apply the same patterns. Five-star review: "Martin was very knowledgeable, intuitive and did much better than expected. Excellent communication skills and adherence to delivery timelines."

## How a contract works

1. A short audit and a written plan: what to test first, what the CI should enforce, and an estimate.
2. Every change comes as a pull request with passing CI, reviewed the way you would review a teammate's work.
3. Regular progress updates, and a short report at the end so your team can keep going without me.
