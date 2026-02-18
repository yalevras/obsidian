**1. Why automatic control? Categorization of control systems**
Manual and automatic control. Focus on automatic control.
Automatic can hold output steady signal.
	Regulator: keep output at a steady, known value
	Tracking or servo system: Make output track a reference system.

Open-loop:
Closed-loop: Controllers (or feedback controllers) compute the control action based on the measured output of the system being controlled.

**2. Block diagrams, the effect of feedback**
Automatic control benefits:
- reduces workload
- performs tasks people can't
- reduces the effects of disturbances
- reduces the effects of plant variations
- stabilizes an unstable system
- improves the performance of a system (time response)
- improve the linearity of the system

Control System components:

![[Pasted image 20260218152252.png]]

Reference: r(t), the desired value you want the system to reach, input
Controller: e = r - m, pid controller, algorithm
Control signal: u(t), signal sent from controller to actuator, voltage to motor, throttle position, instructions sent to system
Actuator: physical device that converts control signal into physical action, motor, heater, hydraulic piston
Plant: dynamic process,