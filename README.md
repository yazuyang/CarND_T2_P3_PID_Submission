# CARND Project: PID Control 

## Introduction
This repository is a submission of CARND Project "PID Control". In this README, I will explain the point of rubric.

## Compilation
This repository has CMakeList.txt and source codes under the directory "./src". 
To complie and run, pleae do below. I confirmed that this repository works well.

* Clone this repo.
* Make a build directory: mkdir build && cd build
* Compile: cmake .. && make
* Run it: ./pid.

## Implementation
In PID.cpp, calculate steering angle with standard PID method. It means below.

* A value of cross track error (variable name is cte) is input to the class method PID::UpdateError. It calculate three cte errors below.
    * p_error: A proportional error.
    * i_error: A integral error.
    * d_error: A derivative error.
* The class method PID::UpdateError multiplies three errors by parameters respectively and sums them up to make a steering angle.

## Reflection

#### The effect each of the P, I, D components in this implementation.

"P" is a parameter that if the current cte is bigger, "P" becomes bigeger. So, if K_p is large, the car will oscillate. 

"I" is a parameter that reflects long-term effects. In this simulation, I thought that the change of the curve of the road was the scene which clarified the influence of the parameter. I executed a simulation with small K_i parameter. The behavior is unstable when entering the curve.

"D" is a parameter that responds more as the difference from the previous cte increases. I executed a simulation with big K_d parameter. Because cte changed rapidly according to the curve, the parameter of D reacted excessively, and the behavior reacted excessively.


#### How the final parameters were chosen
First, I decided the initial value and printed the value of each error. From the results, I decided a good initial value, and twiddle ran the simulator many times and got converged parameters.

## Simulation
I confirmed that the program in this repository controls the car well by making the track run 5 times in simulation.
