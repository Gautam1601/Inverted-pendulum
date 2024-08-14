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
