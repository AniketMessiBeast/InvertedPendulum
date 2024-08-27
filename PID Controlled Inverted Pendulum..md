A **PID (Proportional-Integral-Derivative)** controlled inverted pendulum is a classical problem in control theory, widely used to demonstrate the effectiveness of feedback control systems. 
The inverted pendulum system consists of a rod (pendulum) pivoted at its base, where the objective is to maintain the rod in an upright position despite gravitational forces pulling it downward.

The PID controller, a fundamental algorithm in control engineering, is employed to achieve this stabilization by continuously adjusting the control input — the position of the pendulum tip based on three terms: 
proportional (P), integral (I), and derivative (D).

The `proportional` term responds to the current angle of deviation from the vertical position, the `integral` term accounts for the accumulation of past errors to eliminate steady-state offset, 
and the `derivative` term  predicts future error by evaluating the rate of change of the angle. By tuning these three parameters, the PID controller can provide a balanced corrective force to
counteract disturbances and achieve a desired dynamic response.

u = k<sub>p</sub> * θ + k<sub>d</sub> * θ̇   + k<sub>i</sub> * ∫ θ dt

where, **u** is the control input to the motor as an analog signal (PWM).<br>
NOTE : θ is the error term. Actually the reference angle which the IMU is calculating at the upright position must be **calibrated to 0**. Now, in reference to that, the
input θ from the IMU sensor will be simply the error or deviation from the reference or target angle.<br>


Now, this is an analog controller. To fit it into a microcontroller, we have to dicretize this controller. The following paragraphs would be about the discretization.

**Derivative term Dicretization**

The derivative term θ̇ (theta dot) is calculated as:

θ̇ = (θ(t) - θ(t-1)) / Δt

Here, Δt is the sampling time of the program, which is a constant value. This value can be absorbed into the K<sub>d</sub> parameter. Thus, the derivative component is simply:

K<sub>d</sub> * (θ(t) - θ(t-1))

**Integral term Discretization**

∫ θ dt is approximated by ∑ (θ * Δt)

Since \(\Delta t\) is sampling time which is constant, it can be absorbed into the \(K<sub>i</sub>\) parameter. Therefore, the integral component simplifies to:

K<sub>i</sub> * ∑ θ

So, the microcontroller based PID code would have the logic of : <br>
`u = K<sub>p</sub> * θ(t) + K<sub>d</sub> * (θ(t) - θ(t-1)) + K<sub>i</sub> * ∑ θ`
