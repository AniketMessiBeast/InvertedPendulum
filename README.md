# InvertedPendulum
I am a Bachelor student aiming to design and explore various controllers to control an unstable Inverted pendulum position

The system in this example consists of an inverted pendulum mounted to a cart sliding over a belt controlled by a stepper motor .The fact is the upright position of pendulum is very unstable without control, that is, the pendulum will simply fall over if the cart isn't moved to balance it. Additionally, the dynamics of the system are non-linear. The objective of the control system is to balance the inverted pendulum by applying a force to the cart that the pendulum is attached to. 
 
![Slider](https://github.com/AniketMessiBeast/InvertedPendulum/assets/106831571/f161e7df-f687-446f-badd-2231419d65e7) 

So, we would start first with the dynamics of the system : 

We go with the basic free body diagram to write the NLM equations,

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
