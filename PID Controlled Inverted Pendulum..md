A **PID (Proportional-Integral-Derivative)** controlled inverted pendulum is a classical problem in control theory, widely used to demonstrate the effectiveness of feedback control systems. 
The inverted pendulum system consists of a rod (pendulum) pivoted at its base, where the objective is to maintain the rod in an upright position despite gravitational forces pulling it downward.

The PID controller, a fundamental algorithm in control engineering, is employed to achieve this stabilization by continuously adjusting the control input — the position of the pendulum tip based on three terms: 
proportional (P), integral (I), and derivative (D).

The `proportional` term responds to the current angle of deviation from the vertical position, the `integral` term accounts for the accumulation of past errors to eliminate steady-state offset, 
and the `derivative` term  predicts future error by evaluating the rate of change of the angle. By tuning these three parameters, the PID controller can provide a balanced corrective force to
counteract disturbances and achieve a desired dynamic response.

u = k<sub>p</sub> * θ + k<sub>d</sub> * θ̇ + k<sub>i</sub> * ∫ θ dt

where, **u** is the input to the motor as an analog signal (PWM).
