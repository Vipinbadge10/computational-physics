# 2D N Body Simulation.
## Overview of this project:

The aim of this project is to simulate a 2D N body Problem of Sun-Earth-Earth's Moon- Mars system and study the orbital eccentricity energy conservation of system when sun losses it's mass every year.

The Simulation output file for the animation can be found on Google Drive- (https://drive.google.com/file/d/1J2MrVHV9Bp4acA3YbPkk50ezqO7MoPqd/view?usp=drive_link)

## Initialization and Setups:
To install these dependencies, you can use `pip`.
sshh:```pip install numpy, pip install matplotlib```

* Key Note: This project use Vpython for Simulation, it is advised to install latest Version of Vpython on Jupyterlab using pip. Vpython causes dependencies issues. 

## Key Concepts:

This Simulation uses Newtonian Mechanics that governs the force of planets and Verlet Leap Frog Integration Method.

By Using Newton's Second Law of Motion and Force to gravitation we get an expression to calculate acceleration of body i

$$F_{i} = M{i}.a$$
$$\vec F = \frac {G. M_{i}.M_{j}{\vec R}}{|R_{i} - R_{j}|^3}$$

Later from acceleration i positions and velocities of bodies are updated with timesteps using Verlet leap frog integration method.

Verlet leap frog method updates positions and velocities in half and full steps:

Velocity at half-step: 

$$ v \left(t +\frac{\Delta t}{2}\right ) = v(t)+\frac{a(t)\cdot\Delta t}{2} $$

Positions at the full step: 

$$ x(t + \Delta t) = x(t) + v \left( t + \frac{\Delta t}{2} \right) \cdot \Delta t $$

Velocity at full step:

 $$ v\left(t + \Delta t\right) = v \left( t + \frac{\Delta t}{2} \right) + \frac{a \left( t + \Delta t \right) \cdot \Delta t}{2} $$

where:
* x is position
* t is time
* v is velocity
* $\Delta t$ is change in time.

## Energy Conservation:
The simulation records the total energy of a system with increase in timesteps to measure the energy conservation of system:

<p align="center">
   $$\sum_{i = 0}^{N} K_i + \sum_{i = 0}^{N} P_i = \text{Constant}$$
</p>


where:


* $K_{E}$ is Kinetic Energy.



* $P_{E}$ is gravitation potential energy of a system.


 
$K_{E}$ is calculated by:

$$ K_{E} = \frac{M.V^2}{2}$$


$P_{E}$ is calculated by:

$$- P_{E} = \frac{G.M_{1}.M_{2}}{R}$$

and where:
* M is mass of a body.
* V is velocity of a body.
* G is Gravitational Constant.
* M1 and M2 are masses of different bodies.
* R is separation distance between 2 bodies.


## Orbital Eccentricity
Orbital Eccentricity is determined by calculating the angular momentum, reduced mass and total energy of orbiting system to measure the deviation of orbital shape from being circular.

It is given by:

$e = \sqrt{1+\frac{(2.E.L2)}{\mu.(G.M1.M2)2}} $$

where 
* E is Energy of system
* L is angular momentum
* G is gravitational constant
* M1 and M2 are masses
* $\mu$ is reduced mass of two masses M1 and M2 

# Results and Analysis
The key finding from the simulations are:
* The energy of a system increases with the timestep as sun losing it's mass every year this results in violation of energy conservation of system.

* The eccentricity of earth has face a significant decline over timestep, on the other hand Mars shows a little declination however Moon shows no declination. This is the consequence of Newton's Force of attraction that one massive body exhibits on other influencing the orbital paths and impacting the momentum and energy of orbiting system.

Newton's Force of Attraction are directly proportional to mass of bodies and inversely proportional to the separation distance between two bodies. When sun loses it's mass it is influencing total energy of a orbiting system, the angular momentum of orbiting bodies. Higher the force of attraction led to lower energy of orbiting system that results in more circular orbit whereas lower gravitational force of attraction results in higher energy of orbiting system that results in more eccentric paths.
