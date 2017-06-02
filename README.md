# Model-predictive-control
Using model predictive control(MPC) to control a car in Udacity simulator. A simple explanation of MPC is that it tries to optimize the input parameters (steering and throttle) in a way that makes the trajectory of the car as close as possible to a reference trajectory. It simply considers the control of the car as an optmization problem with certain conditions.

## State space model
The car is modeled using 5 states which are poition(x,y,psi), velocity (v) and errors (cte,epsi). The error vector [cte,epsi] consists of 2 error states, the cross track error which is the difference between the desired trajectory and the predicted trajectory, and the difference in the orientation between the car and the reference trajectory(the orientation of ref. trajectory is the tangent at some point). The (actuators) input vector of the car is [delta,a], where controls the steering and a controls the acceleration of the car.
