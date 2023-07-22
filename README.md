# InvertedPendulum
I am a Bachelor student aiming to design and explore various controllers to control an unstable Inverted pendulum position

The system in this example consists of an inverted pendulum mounted to a cart sliding over a belt controlled by a stepper motor .The fact is the upright position of pendulum is very unstable without control, that is, the pendulum will simply fall over if the cart isn't moved to balance it. Additionally, the dynamics of the system are non-linear. The objective of the control system is to balance the inverted pendulum by applying a force to the cart that the pendulum is attached to. 
 
![Slider](https://github.com/AniketMessiBeast/InvertedPendulum/assets/106831571/f161e7df-f687-446f-badd-2231419d65e7) 

So, we would start first with the dynamics of the system : 

We go with the basic free body diagram to write the NLM equations :
