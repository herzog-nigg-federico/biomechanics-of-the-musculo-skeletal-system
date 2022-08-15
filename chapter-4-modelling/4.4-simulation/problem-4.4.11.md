---
description: Simulation program modification (arm movement).
---

# Problem 4.4.11

(a) Modify the equations of motion for arm movement, and the simulation model (Listing 2) to include constant joint torques at both joints.

(b) Modify the equations of motion for arm movement, and the simulation model (Listing 2) to simulate movement in a vertical plane by including gravitational forces. Simulate this two-segment pendulum. What is different, compared to the simulated movement in the horizontal plane?



_<mark style="color:blue;">Listing 2: Matlab program for simulation of arm movement in the horizontal plane. The program can be downloaded from http://www.bme.ccf.org/isb/tgcs/software/bogert.</mark>_

`% arm.m`&#x20;

`% Program to simulate a two-segment arm model in the horizontal plane`&#x20;

``

`% body segment parameters`&#x20;

`m1 = 3; m2 = 20;`&#x20;

`I1 = 0.01; I2 = 0.01;`&#x20;

`d1 = 0.3; d2 = 0.3;`&#x20;

`cm1 = 0.15; cm2 = 0.15;`&#x20;

`A = I1 + m1cm1^2 + m2d1^2; D = I2 + m2cm2^2;`&#x20;

``

`% set simulation parameters and initial conditions`&#x20;

`t = 0; % start at time=0`&#x20;

`tend = 2; % duration of simulation in seconds`&#x20;

`h = 0.002; % integration step size in seconds`&#x20;

`i = 1; % step counter`&#x20;

`ph1 = 1.0; ph2 = 1.0; % initial segment orientations (rad)`&#x20;

`ph1d = 0.0; ph2d = 10.0; %initial segment angular velocitied (rad/s)`&#x20;

`data = zeros(tend/h,3); % make space to store three columns of data` \
``

`% start simulation`&#x20;

`while (t < tend) % continue until t reaches tend`&#x20;

`% equations of motion`&#x20;

`B = m2d1cm2cos(ph1-ph2);`&#x20;

`C = m2d1cm2cos(ph1-ph2);`&#x20;

`E = -m2d1cm2sin(ph1-ph2);`&#x20;

`F = -m2d1cm2sin(ph2-ph1);`&#x20;

`ph1dd = (DEph2d^2 - BFph1d^2)/(AD - BC);`&#x20;

`ph2dd = (AFph1d^2 - CEph2d^2)/(AD - BC);`&#x20;

`% do one integration step for all four state variables and store result`&#x20;

`ph1d = ph1d + ph1ddh;`&#x20;

`ph2d = ph2d + ph2ddh;`&#x20;

`ph1 = ph1 + ph1dh;`&#x20;

`ph2 = ph2 + ph2dh;`&#x20;

`t = t + h; i = i+1;% increment time and step counter`&#x20;

`data(i,:) = [t 180ph1/pi 180ph2/pi];`&#x20;

`end`&#x20;

``

`% plot the results as angles vs. time plot(data(:,1),data(:,2),data(:,1),data(:,3),’--’);`&#x20;

`xlabel(‘Time [s]’);ylabel(‘Angle [deg]’);`
