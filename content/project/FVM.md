+++
title = "FVMs on Unstructured Meshes"
date = 2018-09-10T20:45:55-04:00
draft = false

# Tags: can be used for filtering projects.
# Example: `tags = ["machine-learning", "deep-learning"]`
tags = ["Finite Volume Methods", "Unstructured Meshes", "Vorticity-Divergence Formulation"]

# Project summary to display on homepage.
summary = "Analysis of finite volume methods on unstructured meshes"

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

Finite volume methods (FVMs) are widely employed in physics, engineering. However, theoretical results concerning
the stability and convergence of these methods are relatively few. One major reason is that, unlike
the finite element methods (FEMs), the FVMs do not naturally fit in a theoretical framework that would facilitate
the analyses of them. The situation is even worse on unstructured meshes, where one of the major analysis tool for FVMs and Finite
Difference Methods (FDMs), namely the Taylor series expansion, is rendered ineffective. The current project aims to change this
situation. It starts by constructing a general functional analytic framework for anlayzing FVMs on unstructured meshes, as well as a
complete discrete vector calculus that facilitates the derivation and analysis of FVMs on unstructured meshes. Due to our own
research interests and bias, the project will primarily focus on fluid problems and the vorticity-divergence based FV schemes.

## Chronicle of developments
1. In [Chen (2016, JCAM)]({{<ref "publication/Chen2016-gl.md">}}), we established a functional analytic framework
for the analysis of FVMs on unstructured meshes. The two essential ingredients of this framework are Cea's
external approximation of functional spaces and the use of the vorticity and divergence as the primal variables. A complete
discrete vector calculus on unstructured meshes, in analogue to the analytical vector calculus, was also presented.

2. The framework was employed ([Chen 2016, JCAM]({{<ref "publication/Chen2016-gl.md">}}))
to establish the convergence of the Mark-and-Cell scheme for 
the incompressible Stokes problem on unstructured meshes, without *a priori* assumptions on the true solutions.

3. The framework was employed to establish error estimates for the MAC schemes for the incompressible Stokes problem on
unstructured meshes ([Chen 2017, NMPDE]({{<ref "publication/Chen2017-el.md">}})). It was shown that on general unstructured meshes,
both the velocity and the vorticity converge at the first order. The convergence is one order higher on special meshes such as the
perfect quadrilateral or triangular meshes. 
