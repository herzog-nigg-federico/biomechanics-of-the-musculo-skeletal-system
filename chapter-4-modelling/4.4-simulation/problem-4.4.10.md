---
description: Simulation program modification (downhill coasting cyclist).
---

# Problem 4.4.10

(a) In the simulation of the downhill coasting cyclist (Listing 1), determine which value of the step size $$h$$ is required to get at most a $$5\space\%$$ error in the speed of the cyclist at any given time.

(b) Modify the simulation program in Listing 1 the propulsive force due to pedaling. Consider different ways to model this:&#x20;

1. Constant force.
2. Constant power.

(c) Modify the program in Listing 1 to compute $$x$$, the distance traveled by the cyclist, by including the ODE $$\dot{x}=ν$$ in the model. Then include the effect of change of altitude on the air drag coefficient $$k$$.



_<mark style="color:blue;">Listing 1: Matlab program for simulation of a cyclist coasting downhill. The program can be downloaded from http://www.bme.ccf.org/isb/tgcs/software/bogert.</mark>_
