<!-- ---
# layout: default
title:  "Finite strain page"
date:   2025-09-28
categories: Jekyll update
theme: jekyll-theme-cayman
--- -->
# Finite strain
The main goal, from my point of view, of finite strain theory is to argue about the deformation of materials in a mathematical sense. 

We generally consider some domain $\Omega$ which undergoes some generic type of deformation.
Such a domain is usually represented as a potato.
Having a domain and some visual to aid us, we can now consider the two most important points in time.
The reference time and its configuration and the current one.
For now, we will not dive into time dependent processes, so let's define the reference configuration as $\boldsymbol{X}$ and the current configuration as $\boldsymbol{x}$.
We can even be a little bit more specific by considering that $\boldsymbol{x}$ is a function of time and the reference configuration itself i.e. $\boldsymbol{x}(\boldsymbol{X}, t)$.

![Tempfigure](/images/pic01.jpg)

The definition of the displacement is now simply given as $\boldsymbol{u}(\boldsymbol{X}, t) = \boldsymbol{x}(\boldsymbol{X}, t) - \boldsymbol{X}$.
Now that we have some notion of change with respect to two configurations, we might want to drill down from these "large" patches of material to conisdering tiny points in the domain $\Omega$.
These material points are interesting to us because we usually see interesting things happening at these points.
A clear example is failure of the material, which is often due to large stress or strain at these points.
So, let's consider an inifitesimally small point in the reference configuration: $\partial\boldsymbol{X}$ and one in the current configuration $\partial\boldsymbol{x}$.
The quantity that relates these points of interest is what's called the deformation gradient,


$$  
    \boldsymbol{F} = \frac{\partial \boldsymbol{x}}{\partial \boldsymbol{X}} 
$$  

This is a fundamental tensor and is used for constructing most other useful tensors in finite strain theory.
The most important one we will discuss now is the right Cauchy-Green tensor.

$$  
    \boldsymbol{C} = \boldsymbol{F}^{T}\boldsymbol{F}
$$  

Using, what are called invariants, of this tensor we obtain some quantities of our potato which do not depend on our reference or current configuration.
This is a wishy washy way of saying that the quantities are observer independent.

$$\begin{equation}
    \begin{aligned}
        & I_{1} = tr\left( \boldsymbol{C}\right),\\
        & I_{1} = \frac{1}{2}\left( tr\left( \boldsymbol{C}\right)^2 -  tr\left( \boldsymbol{C^2}\right)\right),\\
        & I_{3} = Det\left( \boldsymbol{C}\right),\\
    \end{aligned}
\end{equation}$$

These invariants are useful quantities if we want to postulate some type of energy based on the strain.
One of the simplest examples can be formulated as follows:

$$
    \Psi = a(I_{1}-3)^2
$$

Another important thing to note is that we need these strain energy functions to be quasi convex.
This is a difficult thing to prove analytically (I haven't tried this myself, but smarter people than me have tried and failed) so we usually want to show polyconvexity instead.

Here is an inline equation test: $\boldsymbol{P} = \frac{\partial \Psi}{\partial \boldsymbol{F}}$

Here is another test using the `\begin{equation}` command:


