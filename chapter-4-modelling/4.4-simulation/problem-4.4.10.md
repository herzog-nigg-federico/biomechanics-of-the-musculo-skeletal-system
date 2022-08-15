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

`% bicycle.m`&#x20;

`% Program to simulate a downhill coasting cyclist`&#x20;

``

`% system parameters`&#x20;

`g = 9.81; % acceleration of gravity (m s-2)`&#x20;

`m = 75; % mass of the cyclist (kg)`&#x20;

`k = 0.15; % drag coefficient (N s m-1)`&#x20;

`slope = 10; % downhill slope (degrees)`&#x20;

`slope = slopepi/180;` _<mark style="color:blue;"></mark>_ `% same slope, in radians`&#x20;

``

`% set initial conditions`&#x20;

`t = 0;`&#x20;

`tend = 120; % duration of simulation in seconds`&#x20;

`h = 20; % integration step size in seconds`&#x20;

`i = 1; % step counter`&#x20;

`v = 0.0; % initial velocity of cyclist`&#x20;

`data = zeros(tend/h,2); % make space to store t,v (two columns)`&#x20;

`data(1,:) = [t v];`&#x20;

``

`% start simulation loop`&#x20;

`while (t < tend)`&#x20;

`% Calculate acceleration a (=dv/dt) using equation of motion`&#x20;

`a = gsin(slope) - (k/m)v^2;`&#x20;

`% do one forward Euler integration step to calculate new velocity and`&#x20;

`% store data`&#x20;

`v = v + ah;`&#x20;

`t = t + h;`&#x20;

`i = i + 1;`&#x20;

`data(i,:) = [t v];`&#x20;

`end`&#x20;

``

`% plot the results`&#x20;

`plot(data(:,1),data(:,2));`&#x20;

`xlabel(‘Time (s)’);ylabel(‘Speed (m/s)’)`
