
# Overview

This project simulates quantum tunneling phenomenon through evolution of wavefunction over time and also calculates Transmission Probability using Analytical Methods, Numerical Method such as Crack-Nicolson, and Physics Informed Neural Network. The methods for calculating transmission probability are compared later.

## Key Concept:

1.Quantum Tunnelling: Quantum Tunneling is a phenomenon where a particle when imposed upon a potential barrier of a certain height crosses the potential barrier despite having its total energy lesser than the potential energy of a system. There is a non zero probability of particle to be found on the other side of potential barrier and it is calculated by Transmission Probability (T). 

Case: Tunnelling occurs for when E < V0.[V = V0] 

How Tunnelling Probability is Calculated:

1. Evolution of Wavefunction.

2. Integration of Probability Density of Wavefunction.
   
3.Calculation of Transmission Probability - 
$Transmission Probability = \frac{Probability density at Transmission_Region}{Total_Probability}$

2.Schrodinger Equation: This equation governs evolution of Wavefunction under quantum system with time, here a wavefunction is a complex valued number that contains probabilistic information of quantum system means every information about a quantum system for example position, momentum, etc can be figured out by operating mathematical function on Wavefunction. 

$i\hbar\frac{\partial \psi}{\partial t} = \hat H \psi$

$i\hbar\frac{\partial \psi}{\partial t} =(\frac{\partial^2\psi}{\partial^2 x} + \frac{\partial^2\psi}{\partial^2 y})\psi + V(x,t)\psi(x,t)$

where:

$V(x, y, t)$ represents potential energy function; it defines how a potential energy of a particle changes due to its position and time in energy landscape.

$\hat H$ is a Hamiltonian that represents the total energy of a particle inside a system.

$\psi$ represents the wavefunction that evolves over time.

$x,y$ is a spatial component

$t$ is time.

$\hbar$ = h/2m where 'h' is plank constant and m is mass of electron. 


### Physical Setup:

A particle is assumed to be moving along X direction, and at a point in X it encounters a potential barrier which is formed by change in energy landscape of a system; means potential energy of a system is higher than the particle's total energy in that point in X direction.

1.Initial Wavefunction -: Gaussian Wavepacket that describes how my wavefunction of a system will behave at time = 0

2. Energy Landscape of a system to define potential energy over spatial dimension -:
 
a. The region where V(X) = V_0 is a region of potential barrier.
b. The region where V(X) = 0 where a particle is defined as free particle(particle moving without influence of any potential)

V = 0 , for x<O
V = V0, where 0-a/2<x<0+a
V = O, where x>a 

here a is barrier's width and barrier is placed at a origin(X = 0).

3. Boundary Conditions -:
 The Dirchelets boundary condition has been applied here; solutions at the boundary will remain fixed valued.

4. Barrier Parameter-:

Height of barrier - 

Width of barrier - 


### Methods Used :

a. Analytical Method -


b. Crack Nicolson- This method is an average of Euler's implicit and explicit method to achieve numerical solutions to the partial differential equation.
Crank Nicolson Method

Steps to follow:
1. Discretizing Spatial and Time component.
let X be discretized into $\Delta x$ and Y be discretized into $\Delta y$ and T be discretized into $\Delta t$

2. From Time Dependent Schrondiger Equation:
   $$\frac{\partial \psi}{\partial t} = \frac{-i}{\hbar}\hat H \psi$$

4. Approximating partial time derivative through midpoint rule:
$$\frac{\partial \psi}{\partial t}= \frac{\psi_{n+1} - \psi_{n}}{\Delta t}$$

5. Implementing Implicit and Explicit Euler expression for $\psi_{n+1}$ will yield-
   
   for forward :
   $$\frac{\psi_{n+1} - \psi_{n}}{\Delta t} = \frac{-i}{\hbar}\hat H \psi_{n}$$
   
   for backward:
   $$\frac{\psi_{n+1} - \psi_{n}}{\Delta t} = \frac{-i}{\hbar}\hat H \psi_{n+1}$$

   rearranging this term and adding both implicit and explicit method will yeild-
   $${\psi_{n+1} - \psi_{n}} = \frac{-i \Delta t}{\hbar}\hat H \psi_{n} + \frac{-i \Delta t}{\hbar} \hat H \psi_{n+1}$$

   rearranging $psi_{n+1}$ on the left-hand side and $psi_n$ on the right-   
   $$\psi_{n+1} - \frac{-i \Delta t}{\hbar}\hat H \psi_{n+1} = \psi_{n} + \frac{-i \Delta t}{\hbar}\hat H \psi_{n}$$

   The Cranck Nicolson will solve the following linear system for right hand side to produce $psi_{n+1}$ for each time-step-
   
   $$(I - \frac{-i \Delta t}{\hbar}\hat H)\psi_{n+1} = (I - \frac{-i \Delta t}{\hbar}\hat H)\psi_{n}$$

   

   
   
   
7.

   
   
    
   
  
  
8. Applying time derivation of mid-point rule will yield:







c. Physics Informed Neural Network-

Neural Network:
Loss Function:
Optimization:

Wavefunction Evolution

### Analysis and Results:
The calculation of Transmission Probability for each method is given below:

Analytical Transmission Probability - 0.23

Crack Nicolson Transmission Probability - 0.15

PINN Transmission Probability - 0.12


It can be seen that  

