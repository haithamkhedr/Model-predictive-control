# Model-predictive-control
Using model predictive control(MPC) to control a car in Udacity simulator. A simple explanation of MPC is that it tries to optimize the input parameters (steering and throttle) in a way that makes the trajectory of the car as close as possible to a reference trajectory. It simply considers the control of the car as an optmization problem with certain conditions.

## State space model
The car is modeled using 5 states which are position and orientation(x,y,psi), velocity (v) and errors (cte,epsi). The error vector [cte,epsi] consists of 2 error states, the cross track error which is the lateral distance difference between the desired trajectory and the predicted trajectory, and the difference in the orientation between the car and the reference trajectory(the orientation of ref. trajectory is the tangent at some point). The (actuators) input vector of the car is [delta,a], where `delta` controls the steering and `a` controls the acceleration of the car. The state equations can be described as follows

X<sub>t+1</sub> = X<sub>t</sub> + V * cos(psi) * dt

Y<sub>t+1</sub> = Y<sub>t</sub> + V * sin(psi) * dt

psi<sub>t+1</sub> = psi<sub>t</sub> + V * delta * dt / Lf

V<sub>t+1</sub> = V<sub>t</sub> + a * dt

cte<sub>t+1</sub> = cte<sub>t</sub> + V * sin(epsi) * dt

epsi<sub>t+1</sub> = epsi<sub>t</sub> + V * delta * dt /Lf


where Lf is the distance from the front of the vehicle to its center of gravity.

## Trajectory horizon and time sampling
MPC uses the state space model to predict the trajectory of the car. The length of this trajectory `N`(number of points on the trajectory) and the time between predictions `dt` are 2 hyperparameters which were chosen manually to be `N = 20` and `dt = 0.05`. Other values such as 10 and 0.1 were tried but the control of the car was not smooth so I chose to decrese dt to make the trajectory smoother.
