# **Car Control Project: PID**
#### _Lorenzo's version_
[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)

[results]: ./simulator.png

![alt text][results]
---

## Project Introduction
In this project, we drive a car around a track (with Udacity's car simulator) using a PID (proportional, integral, derivative) controller.
The implementation is in C++ and the parameters have been tuned manually. The throttle is set as to be inversely proportional to the angle, which makes us able to reach a speed above 60 mph when not turning.

## Parameter tuning
The parameters P, I and D are obivously critical to the controller, as together they define what the steering angle needs to be for a given cross-track error (i.e. how far the car is, compared to its target track).
- Proportional: this is a direct comparison of the position of the car vs its target position, we have set this parameter in order to ensure a strong enough response during turns
- Integral: this is the accumulated cross-track error, we set this parameters to avoid oscillations due to the proportional term
- Derivative: this is the rate of change of the error, using mainly to smooth the trajectory, this parameter is set to be very small, in order to have some smoothing but still allow the car to correct its trajectory quickly when it turns

## Implementation
The key part of the code is located in `src/PID.cpp`.

- `PID::Init` initializes the PID controller with the parameters
- `PID::UpdateError` updates the P, I and D errors
- `PID::TotalError` returns the sum of all errors
The steering value is set in the `src/main.cpp`.

## Running the code
This project involves the Term 2 Simulator which can be downloaded [here](https://github.com/udacity/self-driving-car-sim/releases)

1. Clone this repo.
2. Make a build directory: `mkdir build && cd build`
3. Compile: `cmake .. && make`
4. Run it: `./pid`.
