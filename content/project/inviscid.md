+++
title = "Inviscid Geophyiscal Models"
date = 2018-09-10T20:50:42-04:00
draft = false

# Tags: can be used for filtering projects.
# Example: `tags = ["machine-learning", "deep-learning"]`
tags = ["non-viscous", "well-posedness"]

# Project summary to display on homepage.
summary = "Well-posedness analysis of inviscid geophysical fluid models"

# Optional image to display on homepage.
image_preview = ""

# Optional external URL for project (replaces project detail page).
external_link = ""

# Does the project detail page use math formatting?
math = true

# Does the project detail page use source code highlighting?
highlight = true

# Featured image
# Place your image in the `static/img/` folder and reference its filename below, e.g. `image = "example.jpg"`.
[header]
image = ""
caption = ""

+++
## Main narrative
Via physics-based approximations and asymptotic analyses,
the discipline of GFD has developed and adopted a hierarchy
of models specifically for large-scale geophysical flows.
These models span from the simple strictly two-dimensional
planar flows all the way up to the non-hydrostatic
Boussinesq model for fully three-dimensional flows.
The goals of performing rigorous mathematical analysis
on these models are two folds. The first one is to
establish the well-posedness of the models, or, more
precisely, the conditions under which these models are
well-posed. Only well-posed models can be trusted as
decent approximations to the reality and can be worthy
of being simulated. The other goal, which is equally
important, is to explore and understand the long-term
dynamics of these models. Knowledge obtained through
theoretical analyses can serve as a guide for numerical
simulations, and make the latter much easier. Along
this line, we have established the global well-posedness
for the barotropic quasi-geostrophic (QG) equation under
a free surface (Chen 2017 submitted). Compared with
the two-dimensional Euler equation for strictly planar
flows, the QG model considered in this work adds some
mild variations in the third dimension by incorporating
the top surface fluctuation into the potential vorticity.
A slightly more sophisticated model, the multi-layer QG model,
has also been considered (Chen 2018, submitted). Here,
the interactions between 
the vertical layers require more elaborate estimates
on the streamfunctions.

## Chronicle of developments
1. In [Chen (2017)]({{<ref "publication/Chen2019-fh/index.md">}}) we established the global well-posedness of the
inviscid barotropic QG equation on a bounded domain.

2. [Chen (2018)]({{<ref "publication/Chen2019-bn/index.md">}}) dealt with the global well-posedness of the
multi-layer QG equation. Here, due to the layer interactions, more elaborate estimates were required.
