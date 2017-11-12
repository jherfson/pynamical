[![PyPI version](https://badge.fury.io/py/pynamical.svg)](https://badge.fury.io/py/pynamical)
[![Anaconda-Server Badge](https://anaconda.org/conda-forge/pynamical/badges/downloads.svg)](https://anaconda.org/conda-forge/pynamical)
[![Build Status](https://travis-ci.org/gboeing/pynamical.svg?branch=master)](https://travis-ci.org/gboeing/pynamical)
[![Coverage Status](https://coveralls.io/repos/github/gboeing/pynamical/badge.svg?branch=master)](https://coveralls.io/github/gboeing/pynamical?branch=master)

# pynamical

**Python package for modeling, simulating, visualizing, and animating discrete nonlinear dynamical systems and chaos**

pynamical uses pandas, numpy, and numba for fast simulation, and matplotlib for beautiful visualizations and animations to explore system behavior. Compatible with Python 2+3.

You can read/cite the journal article about pynamical: Boeing, G. 2016. "[Visual Analysis of Nonlinear Dynamical Systems: Chaos, Fractals, Self-Similarity and the Limits of Prediction](http://geoffboeing.com/publications/nonlinear-chaos-fractals-prediction/)." *Systems*, 4 (4), 37. doi:10.3390/systems4040037.

## Install:

You can install pynamical with [conda](https://anaconda.org/conda-forge/pynamical):

```
conda install -c conda-forge pynamical
```

Or with pip:

```
pip install pynamical
```

## Documentation:

Available on [readthedocs](https://pynamical.readthedocs.io/en/latest/).

## Demos/tutorial:
  1. [Pynamical: quick overview](examples/pynamical-quick-overview.ipynb)
  1. [Pynamical: the logistic model and bifurcation diagrams](examples/pynamical-demo-logistic-model.ipynb)
  1. [Pynamical: 2D and 3D phase diagrams](examples/pynamical-demo-phase-diagrams.ipynb)
  1. [Pynamical: static and animated cobweb plots](examples/pynamical-demo-cobweb-plots.ipynb)
  1. [Pynamical: animated 3D phase diagrams](examples/pynamical-demo-3d-animation.ipynb)
  1. [Pynamical: demonstrating other models](examples/pynamical-demo-other-models.ipynb)

## Quick walkthrough:

First load pynamical. Then simulate some model and visualize its bifurcation diagram in just 2 lines of code:

```python
from pynamical import logistic_map, simulate, bifurcation_plot
pops = simulate(model=logistic_map, num_gens=100, rate_min=0, rate_max=4, num_rates=1000, num_discard=100)
bifurcation_plot(pops)
```

![](examples/images/readme/logistic-map-bifurcation-1.png)

Zoom into a slice of this bifurcation diagram to see its [fractal structure](examples/pynamical-demo-logistic-model.ipynb):

```python
pops = simulate(model=logistic_map, num_gens=100, rate_min=3.7, rate_max=3.9, num_rates=1000, num_discard=100)
bifurcation_plot(pops, xmin=3.7, xmax=3.9)
```
![](examples/images/readme/logistic-map-bifurcation-3.png)

Plot a two-dimensional [phase diagram](examples/pynamical-demo-phase-diagrams.ipynb) of the logistic map:

```python
from pynamical import phase_diagram
pops = simulate(model=logistic_map, num_gens=4000, rate_min=3.6, rate_max=4.0, num_rates=50, num_discard=100)
phase_diagram(pops, xmin=0.25, xmax=0.75, ymin=0.8, ymax=1.01, size=7, color='viridis')
```

![](examples/images/readme/logisitic-map-2d-phase.png)

Or a three-dimensional phase diagram of the [cubic map](examples/pynamical-demo-other-models.ipynb):

```python
from pynamical import cubic_map, phase_diagram_3d
pops = simulate(model=cubic_map, num_gens=3000, rate_min=3.5, num_rates=30, num_discard=100)
phase_diagram_3d(pops, xmin=-1, xmax=1, ymin=-1, ymax=1, zmin=-1, zmax=1, alpha=0.2, color='viridis', azim=330)
```

![](examples/images/readme/cubic-map-3d-phase.png)

Animate the 3D phase diagram of the logistic map [to reveal](examples/pynamical-demo-3d-animation.ipynb) the strange attractor's structure:

![](examples/images/phase-animate/05-logistic-3d-phase-diagram-chaotic-regime.gif)

Animate a cobweb plot of the logistic map's parameter space [to explore](examples/pynamical-demo-cobweb-plots.ipynb) sensitivity and behavior:

![](examples/images/animated-logistic-cobweb.gif)

## For more info:
  - [Read the journal article](http://geoffboeing.com/publications/nonlinear-chaos-fractals-prediction/)
  - [Chaos Theory and the Logistic Map](http://geoffboeing.com/2015/03/chaos-theory-logistic-map/)
  - [Visualizing Chaos and Randomness with Phase Diagrams](http://geoffboeing.com/2015/04/visualizing-chaos-and-randomness/)
  - [Animated 3D Plots in Python](http://geoffboeing.com/2015/04/animated-3d-plots-python/)
