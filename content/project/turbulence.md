+++
title = "Turbulence Modeling"
date = 2018-09-10T20:53:20-04:00
draft = false

# Tags: can be used for filtering projects.
# Example: `tags = ["machine-learning", "deep-learning"]`
tags = ["turbulence"]

# Project summary to display on homepage.
summary = "Modeling and simulations of turbulent flows"

# Optional image to display on homepage.
image_preview = ""

# Optional external URL for project (replaces project detail page).
external_link = ""

# Does the project detail page use math formatting?
math = false

# Does the project detail page use source code highlighting?
highlight = true

# Featured image
# Place your image in the `static/img/` folder and reference its filename below, e.g. `image = "example.jpg"`.
[header]
image = ""
caption = ""

+++

## Main narrative
Turbulence is ubiquitous around us, e.g. the wake following a boat, the dissolution of milk in your coffee cup. Turbulence is important because it plays a central role in distributing energy, heat, as well as passive tracers like nutrients in the ocean. For most flows, the molecular diffusivity is just too weak to accomplish what the flows are doing, distributing all those quantities. Instead, the flow has a mysterious way of generating a continuous spectrum of eddies which work much more efficiently than the molecular diffusivity, distributing stuff that is to be distributed, and smoothing out the flow field. The problem of turbulence, as of today, is also focused on the eddies: How are they generated? How do they work? How to model their effects if one is not able to solve them all on the computers? The last question is of course, practically, the most important one.  My research in this area focuses on understanding the mechanism of turbulence, as well as designing modeling techniques for turbulent flows.

## Chronicle of developments
1. [Chen et al (2011)]({{<ref "publication/Chen2011-jh">}}) and [Chen et al (2012)]({{<ref "publication/Chen2012-ts">}})
developed a scale-aware version of the Anticipated Potential Vorticity Method (APVM). The APVM has the attractive advantage of
being energy neutral among diffusive eddy closures. The original version of the APVM has only one parameter,
which is independent and hence un-aware of the grid resolutions.
The drawback is that the APVM may be over-diffusive when grid resolutions are actually high, and may be under-diffusive when grid resolutions are inadequate. We developed a new version of the APVM that is able to adjust itself
according to the grid resolution. It was shown that this scale-aware version produces more realistic enstrophy spectra with
little or no parameter tuning on a range of grid resolutions.

2. I extended the GM closure onto the general vertical coordinates ([Saenz 2015]({{<ref "publication/Saenz2015-xk">}}),
[Petersen 2019]({{<ref "publication/Petersen2019-vi">}})). 