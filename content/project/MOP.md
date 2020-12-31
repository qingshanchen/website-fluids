+++
title = "Mathematical Ocean Prototype"
date = 2018-09-04T21:52:38-04:00
draft = false

# Tags: can be used for filtering projects.
# Example: `tags = ["machine-learning", "deep-learning"]`
tags = []

# Project summary to display on homepage.
summary = "A high-level compact prototypical model for the ocean"

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
This project is driven by three distinct objectives: simplicity, use of vorticity-divergence
variables, and preservation of the simpletic structure of the analytical model. 

<b>Simplicity</b><br>
A modern-day operational weather/climate model is an enterprise that only big research groups within government funded
laboratories or centers 
can manage. The model is built over years or even decades, and usually
involves tens of thousands of lines of codes. The model is so
complex and delicate that running it requires years of hands-on experiences, and is almost a profession by itself. A direct
consequence of such intimidating complexity within the climate models is that mathematicians, especially those in academia,
are largely left out of weather and climate modeling . A climate model will take years to fathom, and such a big
enterprise is not sustainable in an 
academic setting anyway. There are further collateral damages from the complexity of weather/climate models: there are
relatively few mathematicians working in the area of weather and climate sciences,
a fact that is certainly detrimental to both math and  weather/climate sciences. 

But do things have to be this way? Can weather/climate models be made simpler? In the 165-pages
long book "Spectral Methods in Matlab", Lloyd N. Trefethen demonstrated
 that the advent of MATLAB allows one to do an astonishing amount of serious
computing in a few inches of computer code. Packing a whole climate model into a few inches of
codes may be too much to ask for. However, the ideas and machineries that enable Trefethen to do such an amazing
job with at most one page of codes, namely vectorizations of discrete models and high-level linear algebra routines,
still exist, and have actually being made more prevalently available thanks to years
of developments by volunteers in the open-source community. There is no doubt that the same ideas and machineries
can be applied to climate models as well, which after all, are just discretizations of partial differential equations on the globe.

The first objective of this project is to utilize compact vector-matrix data structures, 
high-level scripting languages, and high-performance linear algebra routines
to build a prototypical ocean model that is as <i> compact,  manageable, and approachable</i> as possible, and
yet still capable of capturing the essential nonlinear dynamics of the world ocean. In addition to
serving our own research needs, it is hoped that the model will also be useful as a research tool to other
mathematicians requiring a model of the essential dynamics of the ocean, but don't want to spend months just getting
one of the operational ocean models up and running, and more generally, it will serve as a vehicle to the mathematically
oriented new-comers hoping to get into the exciting and important field of weather and climate sciences. 

<b>Use of the vorticity and divergence variables</b><br>
The main advantages of the vorticity-divergence formulation of geophysical flows,
compared with the momentum formulations where the velocity is one of prognostic variables,
are accurate representations of the inertial-gravity wave relations, and better accuracies in
general. An accurate representation of the inertial-gravity waves is considered essential
for maintaining the geostrophic balance within the flows. Geostrophic balance is such a prevalent
feature of our oceanic and atmospheric flows that, if it is gone, then either a catastrophe
has happened, or the simulation
has gone wild. 
Use of the vorticity and divergence
as the prognostic variables should, in principle, lead to
better overall accuracy in the solutions. If there is only one order of accuracy in
the momentum, then no convergence can be inferred for the vorticity and divergence, as they are
derivatives of the momentum. On the other hand, a first order convergence
for the vorticity and divergence will ensure that the momentum will converge at least as fast.

The vorticity-divergence formulation also has well-known disadvantages. First, the vorticity and divergence are <i> not </i>
subject to
any types of boundary conditions, and therefore, it is thorny an issue whenever boundary conditions are required, whether
artificially
or numerically. Second, to recover the streamfunction and velocity potential from the vorticity and divergence requires the
solution of Poisson equations globally at each time step, which is very expensive. Our answer to the first issue
is to always impose boundary conditions and define boundary behaviors in terms of the velocity variable, whether it should be
no-flux or no-slip. There is no easy and quick answer to the second issue. However, there have been tremendous progresses in
the past few years in both computer hardwares (GPUs extending the life of the Moore's law) and in algorithms (highly efficient and
scalable linear solvers). It is our hope, and also our belief, that from the progresses already made and to be made in both softwares
and hardwares, a satisfactory answer can be found to the issue of Poisson solvers in the models for large-scale geophysical flows.


<b>Preservation of the simpletic structure</b><br>
In the interior, large-scale geophysical flows are largely inviscid, with a Reynolds number on the order of
$10^{20}$. As any other non-dissipative physical models, they contain a simpletic structure. Specifically, the model
can be expressed as a single equation,
$$\dfrac{\partial F}{\partial t} = [F, \,H].$$
Here $H$ is the Hamiltonian, usually the energy of the system.
The Poisson bracket $[\cdot,\cdot]$ is anti-symmetric, and satisfies the so-called Jacobian property. 
Each state variable, such as vorticity, evolves according to this equation. What is remarkable is that an arbitrary
functional of the state variables also evolves according to this equation. The energy $H$, being a functional itself,
evolves according to this equation. Since the Poisson bracket is anti-symmetric, the right-hand side vanishes when $F$ is
replaced by $H$, and thus energy is constant in time, i.e. conserved! Enstrophy is also an conserved quantity, which is due to the fact that,
in the case of geophysical flows, enstrophy is a singularity for the Poisson bracket.

The Hamiltonian formulation and its intrinsic simpletic structure suggests an entirely new approach for constructing numerical schemes, by approximating
the Hamiltonians and the Poisson brackets. If the simpletic structure is preserved, then the discrete system automatically acquires
the conservative properties of the analytic system.

The Hamiltonian approach also has an advantage in computing quantities of interest (QoI). An QoI is nothing
other than a functional of the state variables. In the Hamiltonian approach, the equation governing the evolution
of this QoI is explicitly available.

## Chronicle of developments
0. A co-volume scheme ([Chen et al 2013, JCP]({{<ref "publication/Chen2013-fa.md">}}))
was proposed for the shallow water equations on unstructured non-orthogonal meshes.
The co-volume scheme, together with other staggered and non-staggered schemes were analyzed
in [Chen (2016, NM)]({{<ref "publication/Chen2016-eg.md">}}).

1. [Chen and Ju (2018, QJRMS)]({{<ref "publication/Chen2018-bu.md">}}) proposed a series of finite volume  schemes
for the inviscid and viscous barotropic QG equations on unstructured meshes. The main contribution of this work
is a two-stage process for implementing the boundary conditions in the viscous case. This process seems particularly suitable
for large-scale geophysical flows, where the viscosity is small, and only one set of boundary conditions (no-flux) is needed
for the leading components,
while the no-slip boundary conditions are needed either for numerical reasons, or for the generation of boundary layers.
<iframe width="676" height="380" src="https://www.youtube.com/embed/BJyA85pmdJ0?rel=0&amp;showinfo=0" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe></br>
The animation above comes from a simulation where the no-flux BC's are
enforced at the stage of solving the Poisson equations, and the
no-slip BC's are enforced while advancing the system by the Runge-Kutta method.



