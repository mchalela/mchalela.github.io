---
title: "NIRDust: hot dust temperatures from K-band spectra"
summary: "A Python package that finds the glow of hot dust around a galaxy's central black hole in infrared spectra and measures its temperature, published in MNRAS."
date: 2021-08-01
weight: 6
tags: ["python", "astropy", "open source", "astronomy"]
showHero: true
heroStyle: "big"
---

**Role:** developer, second-largest contributor, in a team led by Gaia Gaspar at IATE, CONICET.\
**Code:** [Gaiana/nirdust](https://github.com/Gaiana/nirdust) · [Documentation](https://nirdust.readthedocs.io/) · [Paper](https://doi.org/10.1093/mnras/stae008)

## The problem

Many galaxies have a supermassive black hole at their centre, wrapped in a thick ring of gas and dust called the torus. In the galaxies known as Type 2 AGN, that ring hides the black hole from view, but the dust closest to it is heated to around 1000 K and glows in the infrared. In the K-band, a window of the infrared spectrum near 2.2 μm, that glow shows up as a faint reddish excess on top of the ordinary light of the galaxy's stars.

The temperature of that dust tells astronomers about the ring's density, composition and shape. Measuring it meant separating two signals that arrive mixed together, the stars and the dust, and doing it in a way that gives an honest error bar. Several groups had done this with their own scripts and different techniques, so results were hard to compare. What was missing was one documented, tested, reproducible tool that anyone could run on their own spectra.

## What I did

NIRDust takes two spectra: the galaxy nucleus, where the dust is expected, and a reference spectrum that contains only starlight. It models the nucleus as starlight plus a glowing body at a single temperature, and finds the temperature that best explains the data. Because both spectra are normalised first, the data do not need the delicate absolute brightness calibration that infrared observations usually require. My part was the fitting engine and the engineering around it.

- **The fitting engine.** A four-parameter model, a likelihood that accounts for the noise measured in the data, and a basin-hopping optimiser, a method that alternates random jumps with local refinement so the fit does not settle on a wrong answer when the problem has many near-solutions.
- **Results with error bars.** A results object that reports the temperature with its uncertainty, and warnings when a fit has not converged, so users can trust what they get or know when not to.
- **The engineering.** The unit test suite, continuous integration across Python versions, the documentation site with an executable tutorial, and the releases on PyPI.

## Outcome

Published on PyPI and described in *Monthly Notices of the Royal Astronomical Society* (2024). On simulated spectra, the method recovers the temperature to within 100 K in most cases once the data are reasonably clean (signal to noise above 20), and the paper quantifies how the error grows as the data get noisier. Applied to the nearby galaxy Centaurus A, it gives consistent temperatures from three independent datasets taken with different instruments, which is the test that matters: the same answer regardless of who took the data.
