# InvertedPendulum
I am a Bachelor's student aiming to design and self-explore various controllers to control an unstable Inverted pendulum position.

## Abstract
The inverted pendulum is a classic problem in control theory and robotics, exemplifying the challenges of maintaining stability in dynamic systems. The system consists of a rod mounted on a pivot or a moving base, where the goal is to keep the pendulum balanced in an upright position despite the force of gravity. This problem is fundamental in the study of control systems due to its non-linear dynamics and the requirement for precise control to achieve stability. <be>
Techniques such as PID (Proportional-Integral-Derivative) control, state-space control, and modern control methods like LQR (Linear Quadratic Regulator) or adaptive control are employed to address the system's complexities. These methods adjust the input forces or torques to the system based on real-time measurements of the pendulum's angle and angular velocity, aiming to minimize deviations from the desired upright position.

## Mathematical Analysis of Sliding Model of Inverted Pendulum
The system in our case consists of an inverted pendulum mounted to a cart sliding over a belt controlled by a stepper motor. The upright position of the pendulum is precarious without control, that is, it will simply fall over if the cart isn't moved to balance it. 
 
![Slider](https://github.com/AniketMessiBeast/InvertedPendulum/assets/106831571/f161e7df-f687-446f-badd-2231419d65e7) 

So, we would start first with the general dynamics of the system : 

We go with the basic free-body diagram to write the NLM equations,

![Free-body](https://github.com/AniketMessiBeast/InvertedPendulum/assets/106831571/bea23864-cf71-442e-b82c-b3277b66f94d)

After solving all the equations, we would end up with the 2 equations in hand , and then after converting it into frequency domain we achived these expressions :

 $(I+Ml^2)\phi(s)s^2 - mgl\phi(s) = mlX(s)s^2$                       ........(1)
 
 $(M+m)X(s)s^2 + b X(s)s - ml\phi(s)s^2 = U(s)$                      ........(2)

 Recall that a transfer function represents the relationship between a single input and a single output at a time. To find our first transfer function for the output $\Phi(s)$ and an input of $U(s)$ we need to eliminate $X(s)$ from the above equations. Solve the first equation for $X(s)$

 $$ X(s)=\left[{\frac{I+ml^2}{ml}-\frac{g}{s^2}}\right]\Phi(s) $$

 Then substitute the above into the second equation.

$$(M+m)\left[\frac{I+ml^2}{ml}-\frac{g}{s^2}\right]\Phi(s)s^2+b\left[\frac{I+ml^2}{ml}-\frac{g}{s^2}\right]\Phi(s)s-ml\Phi(s)s^2=U(s)$$

Rearranging, the transfer function is then the following

$$\frac{\Phi(s)}{U(s)}=\frac{\frac{ml}{q}s^2}{s^4+\frac{b(I+ml^2)}{q}s^3-\frac{(M+m)mgl}{q}s^2-\frac{bmgl}{q}s}$$

where,

$$q=[(M+m)(I+ml^2)-(ml)^2]$$

From the transfer function above it can be seen that there is both a pole and a zero at the origin. These can be canceled and the transfer function becomes the following.

$$P_{pend}(s) = \frac{\Phi(s)}{U(s)}=\frac{\frac{ml}{q}s}{s^3+\frac{b(I+ml^2)}{q}s^2-\frac{(M+m)mgl}{q}s-\frac{bmgl}{q}} \qquad [ \frac{rad}{N}]$$

`After various simulations, to simplify the task, we jumped to the PID Controlled method of balancing the Pendulum.`
