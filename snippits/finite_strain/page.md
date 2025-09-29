<!-- ---
# layout: default
title:  "Finite strain page"
date:   2025-09-28
categories: Jekyll update
theme: jekyll-theme-cayman
--- -->
# Finite strain
The main goal, from my point of view, of finite strain theory is to argue about the deformation of materials in a mathematical sense. 


## Kinematics
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
The most important ones we will discuss now are the right Cauchy-Green tensor $\boldsymbol{C}$ and the dilatation component $\boldsymbol{J}$.

$$  
    \boldsymbol{C} = \boldsymbol{F}^{T}\boldsymbol{F}
$$  
$$  
    \boldsymbol{J} = Det\left(\boldsymbol{F}\right)
$$  
The dilatation component is simply the change of volume of a material point. 
As you may have learned before, the determinant of a matrix simply returns the area or generalized volume of the matrix.
Considering that $\boldsymbol{F}$ indicates the infinitesimal change of a material point with respect to the current configuration, we can start to see that $\boldsymbol{J}$ is the factor with which we multiply the original volume to obtain the new volume. 
Again, these statements are very hand-wavy. 
A great resource for better understanding this concept is seen in [this video](https://www.youtube.com/watch?v=u6sVUzIHuIg) by Motiz Flaschel.

Using, what are called invariants, of this tensor we obtain some quantities of our potato which do not depend on our reference or current configuration.
This is a wishy washy way of saying that the quantities are observer independent.

$$\begin{equation}
    \begin{aligned}
        & I_{1} = tr\left( \boldsymbol{C}\right),\\
        & I_{1} = \frac{1}{2}\left( tr\left( \boldsymbol{C}\right)^2 -  tr\left( \boldsymbol{C^2}\right)\right),\\
        & I_{3} = Det\left( \boldsymbol{C}\right),\\
    \end{aligned}
\end{equation}$$


## Strain energy
These invariants are useful quantities if we want to postulate some type of energy based on the strain.
One of the simplest examples can be formulated as follows:

$$
    \Psi = a(I_{1}-3)^2
$$

This is an example of a hyperelastic material model.
These types of models are the main focus of my current research and are relatively easy to understand.

>An important thing to note is that we need these strain energy functions to be quasi convex.
This is a difficult thing to prove analytically (I haven't tried this myself, but smarter people than me have tried and failed) so we usually want to show polyconvexity instead.
For now, just know that a quick check you can do is to verify that increasing the invariant value can only increase the strain energy or keep its value constant.


## Stress measures
The reason that these models are relatively simple to work with is because the stress and stiffness of these materials has a simple relationship with the strain energy function, 
$$
    \boldsymbol{P} = \frac{\partial \Psi}{\partial \boldsymbol{F}}.
$$
This is what's known as the First Piola Kirchoff stress and is, in my opinion, the most straightforward.
It specifically relates the forces in the current configuration to the affected areas of the reference configuration.
Therefore, it can be viewed as a linking stress between the two configurations.
Calculating this stress analytically however, is not so straightforward.
If you want a stress function that you can derive by hand my suggestion would be the second Piola Kirchoff Stress, 
$$
    \boldsymbol{S} = \frac{\partial \Psi}{\partial \boldsymbol{C}}.
$$
This stress value is purely represented in the reference configuration.
As a result it is easier for engineers to compare the features of their geometry with the resulting stresses.

I like to stick within this reference-configuration-centric point of view.
Deriving the cauchy stress using the left cauchy-green tensor is therefore out of scope.
I will however, provide one of the most useful conversion tables out there [(yoinked straight from wikipedia)](https://en.wikipedia.org/wiki/Alternative_stress_measures):


| Equation for | $\sigma$                              | $\tau$                            | $P$            | $S$             | $T$             | $M$                                 |
| ------------ | ------------------------------------- | --------------------------------- | -------------- | --------------- | --------------- | ----------------------------------- |
| $\sigma=$    | $\sigma$                              | $J^{-1}\tau$                      | $J^{-1}PF^{T}$ | $J^{-1}FSF^{T}$ | $J^{-1}RTF^{T}$ | $J^{-1}F^{-T}MF^{T}$ (non isotropy) |
| $\tau=$      | $J\sigma$                             | $\tau$                            | $P F^{T}$      | $FSF^{T}$       | $RTF^{T}$       | $F^{-T}MF^{T}$ (non isotropy)       |
| $P=$         | $J\sigma F^{-T}$                      | $\tau F^{-T}$                     | $P$            | $FS$            | $RT$            | $F^{-T}M$                           |
| $S=$         | $J F^{-1}\sigma F^{-T}$               | $F^{-1}\tau F^{-T}$               | $F^{-1}P$      | $S$             | $U^{-1}T$       | $C^{-1}M$                           |
| $T=$         | $J R^{T} \sigma F^{-T}$               | $R^{T} \tau F^{-T}$               | $R^{T}P$       | $US$            | $T$             | $U^{-1}M$                           |
| $M=$         | $J F^{T}\sigma F^{-T}$ (non isotropy) | $F^{T}\tau F^{-T}$ (non isotropy) | $F^{T}P$       | $CS$            | $UT$            | $M$                                 |

Where the cauchy stress is $\sigma$ and $\tau$ is the kirchoff stress.
The latter will not be considered for the remainder of this page.
For any of the other mentioned stresses I will kindly refer you to the original wikipedia page.

## (in-)Compressibility
One of the most important assumptions we can make for the mechanical behavior of materials is its (in-)compressibility.
An example of an incompressible material is rubber, and in fluid dynamics water is also (usually) seen as an incompressible material.
This simply means that when we look at any infinitessimally small point of material in the current configuration, we will not observe any volume change $\boldsymbol{J}=1$.
The way to do this in our strain energy and stress models is by adding constraints to our model.
We could state that it is a constraint to be enforced by some optimization algorithm, but another way to do this is by using lagrange multipliers.

These Lagrange multipliers are usually solved for during optimization procedures as an extra variable to optimize for.
Another way of obtaining a similar result is by using penalty functions through the use of a bulk modulus.
These penalty functions are generally just terms added to the strain energy model which increase the energy in the system if the material changes volume.
The degree with which this energy increases is goverened by the value of the bulkmodulus and the functional which quantifies the change in volume.
Some typical versions of the penalizing functionals and bulk modulus $K$ are:

$$
    K(J-1)^2,
$$
and 
$$
    K\left(\frac{J^2-1}{2} - ln(J)\right).
$$

One thing to notice is that, adding these terms directly to strain energy functions as we did before will doubly penalize the change in volume.
Remember that we multiply material model parameters to invariants which are based on $\boldsymbol{C}$.
This tensor itself will "increase in value" due to change in volume and so will its invariants.
Thus, if we want to disentangle the contribution of change in volume in the strain energy function from the other material model parameters we need to do something extra.

It turns out that we need to do an isochoric-deviatoric split.
All you need to remember is that when such a split is used, we use a bar over the invariant as such $\overline{I}_\star$.
Furthermore, it is quite easy to calculate these invariants.
Instead of using the classic deformation gradient you compute it as follows:

$$
    \overline{\boldsymbol{F}} = \boldsymbol{J}^{-1/3} \boldsymbol{F}
$$

and then use $\overline{\boldsymbol{F}}$ to calculate $\overline{I}_\star$.

A simple example of a compressible material model would be:
$$
    \Psi = \Psi_{iso} + \Psi_{vol} = a(\overline{I}_{1}-3)^2 + K(J-1)^2
$$

Where,

$$
    \overline{I}_1 = tr\left( (\boldsymbol{J}^{-1/3} \boldsymbol{F})^T (\boldsymbol{J}^{-1/3} \boldsymbol{F}) \right) = tr\left( \boldsymbol{J}^{-2/3} \boldsymbol{F}^T  \boldsymbol{F} \right)
$$
