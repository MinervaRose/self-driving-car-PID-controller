# Reflection

## Describe the effect each of the P, I, D components had in your implementation.

*Student describes the effect of the P, I, D component of the PID algorithm in their implementation. Is it what you expected?



PID controllers are named after the Proportional, Integral and Derivative control modes they have.
A proportional–integral–derivative controller is a control loop mechanism employing feedback. 
In this project, we implemented the **PID controller to respond with steering and throttle commands**.
After the CTE value sent by the simulator is read, the PID controller updates the error value and predicts the steering angle based on the total error.


**P** corrects steering wheel scale errors. The wheel is turned in another direction when too far from the target.

**D** suppresses the oscillation effect. By adding the change in error, it provides smoothening by reducing the angle if the error is reduced.

**I** corrects the mechanical error that makes us turn the wheel more or less forcefully so that the vehicle stays upright. It penalizes the sum of cumulative errors. 

Twiddle PID curve corresponds to the use of the Twiddle algorithm .
**Twiddle** is a “local hill-climber” optimization routine. It iterates through each parameter. It makes a change (both positive and negative). If it improves the controller we keep that change and try a larger one the next time. If it does not improve the controller, we discard the change and try a smaller change the next time. 
In this project, the Twiddle PID curve allows us he to find the coefficients more rapidly and  to converge more quickly to the reference trajectory.


## Describe how the final hyperparameters were chosen.

*Student discusses how they chose the final hyperparameters (P, I, D coefficients). 
*This could be have been done through manual tuning, twiddle, SGD, or something else, or a combination!

I decided to use manual tuning first.
I did initially think of using Twiddle immediately but it would not work. So I changed my mind and used manual tuning. By reading the forum I understood that it is not recommended to start with automated opmization because there is no room for error on a narrow track like this project and that was the reason why the car would leave the track. 


```
    vector<double> p = {0.15000, 0.00100,1.70000}; 
    vector<double> dp = {0.01000, 0.00010, 0.1000};
```

Then as advised, I let twiddle take over to fine tune the parameters to their final values.

