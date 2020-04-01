# CarND-Controls-PID
### Effect of PID controller in the implementation

A PID controller is a controller characterized by the control law below:
$$
u(t) = K_{p}e(t) + K_{i}\int_{}^{} e(t)dt\ + K_{d} \frac{de(t)}{dt}
$$
In other words, there is:

- a **Proportional** part, where the control action is directly proportional to the error
- an **Integral** part, where the control action is directly proportional to the error
- a **Derivative** part, where the control action is directly proportional to the variation of the error (its derivative in continuous-time domain)

All three parts play decisive yet different roles in the controller. The PID behavior change to the variation in the control gains have been well known for a quite long time now, and what was observed in this project only confirms it. 

* The proportional part affects the ability of the system to stick around the reference value. Small values of Kp cause a slow response to cross-track-error variation. Conversely, high values lead to a too aggressive response, inducing oscillations in the system.
* The derivative part is used to compensate for the oscillating phenomenon without sacrificing readiness to the response. Nonetheless, a Kd value that is too large also leads to too aggressive responses and thus system instability. 
* Ki is needed to compensate the long-term steady-state error that accumulates over time due to imperfections in the controller on in the model. 

### PID Tuning

The PID was manually tuned, following an approach conceptually similar to the Ziegler-Nichols method.

First off, all the gains were set to 0. Then Kp was set, starting from a value suggested by other Udacity students. Once a value leading to reasonable oscillations was found, the Kd was set to introduce the derivative part in the controller. Since the integral part only matters on the long shot, the first turns of our track are well enough to evaluate good Kp and Kd final values. After increasing Kd to a sufficient value, Ki was finally introduced. 

Once this phase concluded, I played around with value to find the optimal ones.
