---
title: "Pyedra: continuous integration for an asteroid toolkit"
summary: "Moved an asteroid phase-curve package from Travis CI to GitHub Actions, so every change runs the full test, style, docs and coverage checks before it is merged."
date: 2021-02-24
weight: 7
tags: ["python", "pytest", "github actions", "open source"]
showHero: true
heroStyle: "big"
---

**Role:** contributor and co-author, in a project led by Milagros Colazo at IATE, CONICET.\
**Code:** [milicolazo/Pyedra](https://github.com/milicolazo/Pyedra) · [Documentation](https://pyedra.readthedocs.io/) · [Paper](https://doi.org/10.1016/j.ascom.2021.100533)

## The problem

An asteroid's brightness changes with the angle between it, the Sun and the observer. Plotting brightness against that angle gives a phase curve, and fitting a model to the curve yields parameters that feed estimates of the asteroid's size and reflectivity. Pyedra fits three standard phase-curve models to observations and plots the results, so that the large sky surveys now running can be processed in bulk instead of object by object.

The project already had a thorough quality gate defined with tox: unit tests, style and docstring checks, a packaging check, a documentation build that fails on warnings, and a 95 percent coverage threshold. What it lacked was a reliable place to run it all, since Travis CI had just ended its free plan for open-source projects.

## What I did

I migrated the project's continuous integration to GitHub Actions in a single, self-contained contribution.

- **A workflow that runs on every push and pull request**, across Python 3.7+, installing the system dependency the docs build needs and then running the existing tox suite.
- **A mapping from Python version to tox environments**, so each version runs the tests and one of them also runs the style, docs, manifest and coverage checks, without duplicating work.
- **No changes to the tests themselves.** The point was to make the checks the team had already written run on every change, in the same place the code is reviewed.

## Outcome

The workflow has run Pyedra's checks on every change since February 2021, and the maintainers have kept it as the project's CI, extending the Python matrix to 3.12 and 3.13 in 2025. The package is on PyPI and described in *Astronomy & Computing* (2022), where I am a co-author.
