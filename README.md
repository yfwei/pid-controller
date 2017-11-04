## PID Controller
The fourth project of the Udacity Self-Driving Car Nanodegree term 2.

## Basic Build Instructions

1. Clone this repo.
2. Make a build directory: `mkdir build && cd build`
3. Compile: `cmake .. && make`
4. Run it: `./pid`. 

## Rubric Points
### Here I will consider the [rubric points](https://review.udacity.com/#!/rubrics/824/view) individually and describe how I addressed each point in my implementation.  

---

#### 1. Describe the effect each of the P, I, D components had in your implementation.

The P (Proportional) component determines how hard the vehicle turns the wheel, the I (Integral) component compensates the systematic bias and keeps the vehicle on the center of the lane. Finally, the D (Derivative) component removes the overshooting problem that makes the vehicle move like a drunk driver. 

#### 2. Describe how the final hyperparameters were chosen.

My final P, I, D coefficients are *0.12, 0.005, 1.7*. They are chosen empirically with the following procedure:

1. Initialize P and D coefficients with very small values and set I coefficient to 0.0.
2. Increase the P coefficient to ensure the vehicle can make the turn.
3. If the vehicle starts oscillating, increase the D coefficient until there is no oscillation.
4. Repeat the step 2 and 3 until the vehicle can drive around the track.
5. Increase the I coefficient until the vehicle can drive on the center of the lane.

The following rule governs how I tune them:

**D coefficient >> P coefficient >> I coefficient**
