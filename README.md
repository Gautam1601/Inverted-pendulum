# README: Balancing an Inverted Pendulum on a CartPole Using PID Control

## Overview

This project demonstrates the concept of balancing an inverted pendulum using a PID (Proportional-Integral-Derivative) controller. The inverted pendulum system, often referred to as a CartPole, is a classic problem in control theory and reinforcement learning. It involves a pole that is attached to a cart, where the objective is to keep the pole balanced in an upright position by moving the cart horizontally.

## Inverted Pendulum Concept

An inverted pendulum is a pendulum that has its center of mass above its pivot point. Unlike a regular pendulum, which is stable in its equilibrium (hanging downwards), an inverted pendulum is inherently unstable. To maintain balance, the cart must move to counteract the forces acting on the pole.

### Key Components:
1. **Cart:** The base that can move left or right to stabilize the pole.
2. **Pole:** The rod attached to the cart that needs to be balanced upright.
3. **Pivot:** The point where the pole is attached to the cart.

### Dynamics:
- When the pole leans in one direction, the cart needs to move in that direction to prevent the pole from falling.
- The objective is to keep the pole's angle close to zero (i.e., upright) while minimizing the movement of the cart.

## PID Control

The PID controller is a control loop mechanism widely used in industrial control systems. It calculates an error value as the difference between a desired setpoint and a measured process variable. The controller attempts to minimize the error by adjusting the control inputs to the system.

### PID Components:
1. **Proportional (P):** The control action is proportional to the error. It provides a control force that is directly proportional to how far the pole is from the upright position.
2. **Integral (I):** The control action is proportional to the cumulative sum of past errors (integral of error). It helps eliminate steady-state errors.
3. **Derivative (D):** The control action is proportional to the rate of change of the error (derivative of error). It provides a damping effect, reducing the likelihood of oscillations.

### PID Formula:
   
```latex
u(t) = K_p \cdot e(t) + K_i \cdot \int_0^t e(\tau) d\tau + K_d \cdot \frac{de(t)}{dt}


## Code Explanation

The provided code implements a basic PID controller to balance the pole on a CartPole environment using the `gym` library.

### Steps in the Code:

1. **Environment Setup:**
   ```python
   env = gym.make('CartPole-v1', render_mode='human')
The environment is created using OpenAI's gym library, which simulates the CartPole dynamics.

PID Controller Initialization:

python
Copy code
Kp = 2.0
Ki = 0.01
Kd = 0.9
prev_error = 0
integral = 0
The PID constants 
𝐾
𝑝
K 
p
​
 , 
𝐾
𝑖
K 
i
​
 , and 
𝐾
𝑑
K 
d
​
  are defined. The prev_error and integral variables are initialized to zero.

Main Loop:

python
Copy code
for t in range(1000):
    state = env.reset()
    pole_angle = state[1]
The loop runs for 1000 iterations, resetting the environment at the start of each iteration and extracting the pole's angle.

Error Calculation:

python
Copy code
error = pole_angle
integral += error
derivative -= prev_error
control = Kp*error + Ki*integral + Kd*derivative
The error is calculated as the difference between the desired angle (which is zero) and the current angle. The integral of the error and the derivative of the error are also updated. The control signal is computed using the PID formula.

Environment Step:

python
Copy code
state, reward, done, info = env.step(control)
env.render()
The control signal is applied to the environment, and the resulting state is updated. The environment is rendered to visualize the balancing.

Environment Closure:

python
Copy code
env.close()
The environment is closed after the loop completes.

Notes
The provided code has a small issue in the derivative calculation where it incorrectly subtracts prev_error rather than updating it properly. The correct approach would be:
python
Copy code
derivative = error - prev_error
prev_error = error
Fine-tuning the PID parameters is crucial for achieving stable balancing. The given values are starting points and may require adjustment depending on the specific behavior of the system.
Conclusion
This project demonstrates the basics of using a PID controller to balance an inverted pendulum on a cartpole. It provides a foundational understanding of both the inverted pendulum problem and the implementation of a PID control loop in a simulated environment.
