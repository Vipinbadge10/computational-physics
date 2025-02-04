# Solving a 2D Heat Equation 

The Simulation Output file can be found on Google Drive-(https://drive.google.com/file/d/1dyRJPvkbFp7dXPHU5d8djUMQ2W3BAKGm/view?usp=sharing) 

## Overview
This project solves and visualizes 2D heat equation using Finite Difference Method.

## Table of Contents:
1. A brief introduction to Heat Equation.
2. Significance of Finite Difference Method.
3. Computational Method.
   * Defining a system.
   * Introducing heat sources, and Boundary Condtions.
   * Solution using Finite Difference Method.
   * Visualizing Results.

## Concepts
**Heat Equation**: A partial differntial equation that shows the rate of change in temperature of some spatial domain or volume with change in time.
**Finite Difference Method**: This is a numerical method to solve differential equation by approximating their solution in finite differences.
**Intial Condtion**: An initial condition that a system has at Time t = 0. In this case the initial temperature that a system has at Time t = 0 before heat starts to flows in system.
**Boundary Condition**: A boundary condtion refers to the fixed solution at the boundaries when Time t varies. In this case the boundary condition refers to fixed temperature at the boundary when t varies.

## Process
1.**Define a system where heat flows**: The system has thermal diffusity 2D space(X,Y) of length(X,Y) =(20,20) that is divided into smaller grids points of 200 with length dx,dy and the total time of simulation into K numeber of smaller timesteps of value dt.

2.**Introducing heat sources,an initial and boundary conditions**. : 5 heat sources with some specific temperature has been introduce at some locations of the 2D spatial grid, and we applied Dirchilet Boundary condtion at left,right ,top and bottom of 2D surface.

3.**Using Finite Difference Method**:This numerical method is used to calculate the temperature at the next timestep using the current temperature, and we use vectorized operation for updating the temperature distribution over time.
We use FDM to calculate temperature distribution values at a one timestep, copy the current value of temperature ditribution in new array to store the updated value of temperature distribution for next timestep,We use second spatial derivative to calculate temperature at initerior grid points over next timestep, apply boundary condition before returning the updated temperature distribution we repeat this process for simulating temperature distribution in 2D space.

4.**Visualizing Results**: The results are animated using Matplotlib Funcanimation that calls step function iteratively to animate the results over frames.

## Installation
To run this project you need to have Python and the following libraries needs to be installed
- `numpy`
- `matplotlib`

This libraries can be installed using :
```sshh
pip install numpy
pip install matplotlib
