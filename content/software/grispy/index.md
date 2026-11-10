---
title: "GriSPy: grid search in Python"
summary: "A fixed-radius nearest-neighbour search library for large astronomical catalogues, published in Astronomy & Computing and maintained since 2019."
date: 2021-03-01
weight: 5
tags: ["python", "numpy", "open source", "astronomy"]
showHero: true
heroStyle: "big"
---

**Role:** lead developer and maintainer, project manager of a team of five developers at IATE, CONICET.\
**Code:** [mchalela/GriSPy](https://github.com/mchalela/GriSPy) · [Documentation](https://grispy.readthedocs.io/) · [Paper](https://doi.org/10.1016/j.ascom.2020.100443)

## The problem

Much of extragalactic astronomy comes down to asking which objects lie within some distance of others: the neighbours of every galaxy in a survey, the particles around every halo in a simulation, the pair counts behind a correlation function. Catalogues now run to tens of millions of points, so brute force is out. Tree-based searches handle this well up to a point, but their build time grows quickly with catalogue size, and simulation and survey data bring their own needs: periodic boxes, angular distances on the sky, and often a different search radius for every centre.

## What I did

I designed GriSPy, wrote most of its core and led the team that built, tested and documented it.

- A regular grid index over k-dimensional points, with three query types: all neighbours within a radius, within a shell between two radii, and the n nearest.
- Per-axis periodic boundary conditions for simulation boxes, a search radius per centre, and Euclidean, haversine and Vincenty metrics for searches on the sky, plus custom distance callables.
- Benchmarks against SciPy's cKDTree and scikit-learn's BallTree on uniform and N-body data, written up in *Astronomy & Computing* (2021).
- Test suite, continuous integration, documentation on Read the Docs and releases on PyPI.
- In 2026, a 0.3.0 release that moved the grid storage to a compressed sparse row layout for faster builds and queries, added a Periodicity class, and brought support up to Python 3.14.

## Outcome

Published on PyPI, registered in the Astrophysics Source Code Library and described in a refereed paper. In the paper's benchmarks GriSPy builds its index faster than the tree methods beyond about a million points and is faster end to end beyond about ten million. Seven years after the first commit it is still maintained, with the latest release in August 2026.
