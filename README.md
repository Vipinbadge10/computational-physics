
# Overview

This project simulates quantum tunneling phenomenon through evolution of wavefunction over time and also calculates Tunnelling Probability using Analytical Methods, Numerical Method such as Crack-Nicolson, and Physics Informed Neural Network. The methods for calculating tunnelling  probability are compared later.

The simulation result can be found on google drive-
[https://drive.google.com/file/d/1lH6v4BPuNW9EA_696EYzBX_-s0SRVNTs/view?usp=sharing](https://drive.google.com/file/d/1lH6v4BPuNW9EA_696EYzBX_-s0SRVNTs/view?usp=drive_link)

## Key Concept:

1.Quantum Tunnelling: Quantum Tunneling is a phenomenon where a particle when imposed upon a potential barrier of a certain height crosses the potential barrier despite having its total energy lesser than the potential energy of a system. 
In simple terms, there is always non zero probability of finding a particle on the other side of potential barrier despite particle's energy is less than the energy of a potential barrier and it is given by Transmission Probability (T). 

Case: Tunnelling occurs for when E < V0.[V = V0] 

Here, Tunnelling Probability 'T' is calculated from Evolution of Wave-function by following certain steps.

1. Schrodinger equation is solved for evolution of initial wavefunction.

2. We find Probability Density of Wavefunction by the modulus of wavefunction over spatial domain.

$$P(X,Y) = |\psi (x,y)|^2$$

3. We find total probability we need to integrate the probability density of wave-function over whole spatial area.
   
$$ Total Probability = \int_{-5}{5}\int_{-5}^{5} P(X,Y) dx dy $$

5. We ensure that the conservation of total probability(probability of finding a particle = 1)
Total Probability needs to be normalized to conserve total probability.

$$\int_{-5}{5}\int_{-5}^{5} P(x,y) dx dy = 1$$

6. By integrating the probability density at transmitted area we calculate probability at transmitted region.
   
$${Probability at transmitted region} = \int_{a}{5}\int_{a}^{5} P(x,y) dx dy$$

7. Finally the Transmission Probability is calculated by taking the ratio of Probability at Transmitted region with Total Probability.
   
$$Tunnelling Probability = \frac{Probability at transmitted region}{Total Probability}$$


2.Schrodinger Equation: This equation governs evolution of Wavefunction under quantum system with time, here a wavefunction is a complex valued number that contains probabilistic information of quantum system -every information for given state of an electron for example position, momentum, etc can be figured out by operating mathematical function on Wavefunction. 

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

A particle with an initial wavefunction\[Gaussian Wavepacket\] is assumed to be moving along X direction, and at an origin it encounters a potential barrier which is formed due change in energy landscape of a system; means potential energy of a system is higher than the particle's total energy in that point in X direction.

1.Initial Wavefunction -: Gaussian Wavepacket that describes how my wavefunction of a system will behave at time = 0

2. Energy Landscape of a system to define potential energy over spatial dimension -:
 
a. The region where V(X) = V_0 is a region of potential barrier.
b. The region where V(X) = 0 where a particle is defined as free particle(particle moving without influence of any potential)

V = 0 , for x<O
V = V0, where 0-a/2<x<0+a
V = O, where x>a 

here a is barrier's width and barrier is placed at a origin(X = 0).

3. Boundary Conditions -:
 The Dirchelets boundary condition has been applied here; solutions at the boundary will remain 0.

4. Barrier Parameter-:

Height of barrier - 1.05

Width of barrier - 1e-8


### Methods Used :

#### 1. Analytical Method:
The analytical transmission is calculated directly from schrondiger equation and it given by

The energy of the particle is:
$$ E = \frac{\hbar^2 k_0^2}{2 m_e}$$

If \( E < V_0 \), then:
$$\alpha = \frac{\sqrt{2 m_e (V_0 - E)}}{\hbar}$$


And the analytical transmission probability is:
$$ T_{\text{analytical}} = \frac{1}{1 + \left( \frac{V_0^2}{4 E (V_0 - E)} \right) \sinh^2(\alpha a)}$$

If \( E = V_0 \), the transmission is:
$$T_{\text{analytical}} = 1$$


#### 2. Crack Nicolson:
This method is an average of Euler's implicit and explicit method to achieve numerical solutions to the partial differential equation.
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

   rearranging this term and averaging both implicit and explicit method will yeild-
   $${\psi_{n+1} - \psi_{n}} = \frac{-i \Delta t}{2 \hbar}\hat H \psi_{n} + \frac{-i \Delta t}{2 \hbar} \hat H \psi_{n+1}$$

   rearranging $psi_{n+1}$ on the left-hand side and $psi_n$ on the right-   
   $$\psi_{n+1} - \frac{-i \Delta t}{2 \hbar}\hat H \psi_{n+1} = \psi_{n} + \frac{-i \Delta t}{2 \hbar}\hat H \psi_{n}$$

   The Cranck Nicolson will solve the following linear system for right hand side to produce $psi_{n+1}$ for each time-step-
   
   $$(I - \frac{-i \Delta t}{2 \hbar}\hat H)\psi_{n+1} = (I - \frac{-i \Delta t}{2 \hbar}\hat H)\psi_{n}$$


#### 3. Physics Informed Neural Network-
Physics Informed Neural Network are a type of neural network that are useful in solving physics problems such as Heat Equation and Time Dependent Schrodinger Equation because this equations involves solving partial differential equations, the PINN embeds the underlying physical laws into their training process in the form of Loss Function. This approach ensures that prediction of Neural Network is consistent with underlying physics.

Structure of NN architecture:

Input: \[X,Y,T\]

Output: \[ $\psi_{real}$ , $\psi_{imaginary}$\]

Layer: \[3,56,56,2\]

Loss Functions: The physical constraints and laws of physics is constrianed into neural network in the form of loss function.
* Initial Loss - for calculating difference in numerical value of initial state of wavefunction at time t = 0 from predicted psi at time = 0 
* Boundary Loss - for calculating difference in numerical value of psi around the edges of spatial domain, for boundary condition psi at right,left ,top, bottom must be 0
* PDE loss - for calculating the difference in numerical value of predicted wavefunction that gives the residual =0, when substituting the value of predicted psi in Time Dependent Schrondiger Equation.
* Probability Conservation loss - to satisy the probability conservation loss.

A Neural Network learns to predict the real and imaginary part of wavefunction from inputs such as spatial (X,Y) and time(t).

The derivate is computed from the predicted wavefunction from the output of NN to form PDE residual.
This predicted wavefunction from NN is enforced to obey Schrodinger equation which is incorporated in the form of PDE_residual. The predicted psi must give the pde residual = 0 to satisfy the Schrondiger equation.

The Collocation points is sampled across all the domain, the Initial Loss is evaluated on set of collocation point at time t = 0 by calculating the MSE between predicted and actual wavefunction function at time t = 0.

The Collocation points is sampled across boundaries of spatial domain, the boundary loss is evaluated on set of collocation points around the edges by calculating the MSE between predicted and actual wavefunction around the edges, for boundaries the predicted wavefunction needs to be zero

The collocation points are densely increased around post barrier region to capture wavefunctions accurately.

In optimization phase the NN model is optimized by minimizing the gradient of total loss function with respect to networks parameters \[such as weights]\ using backpropagation. The ADAM optimizer here adjusts learning rate, and networks parameter for each iteration. At each iteration \[epoch] the model calculates total loss function, calculates rate of change of total loss w.r.t to network parameters and adjusts the network parameter until the model converges to satifsy the constraints of physical system\[Initial, Boundary and PDE-Schrondiger Equation.]

The total loss is given by: 
$\mathcal{L} = w_{ic} * loss_{ic} + w_bc * loss_{bc} + w_{pde} * loss_{pde} + w_{prob} * loss_{prob}$


and rate of change of total loss w.r.t network parameters: $\frac{\partial L}{\partial W}$

### Analysis and Results:
The calculation of Transmission Probability for each method is given below:

Analytical Transmission Probability - 0.23

Crack Nicolson Transmission Probability - 0.15

PINN Transmission Probability - 0.13

With further refinement with weights(lamda value) for loss function and additional transmission enforcement law, and advance optimizers the NN TDSE model will capture tunnelling behaviour accurately surpassing the Crank Nicolson method and get closer to Analytical method.

