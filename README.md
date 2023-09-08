![image](images/microchip.jpg) 

## an957 sensored bldc motor control


## BLDC MOTORS


<p style='text-align: justify;'>BLDC motors are basically inside-out DC motors. In a DC motor the stator is a permanent magnet. The rotorhas the windings, which are excited with a current.The current in the rotor is reversed to create a rotating or moving electric field by means of a split commutator and brushes. On the other hand, in a BLDC motor the windings are on the stator and the rotor is a permanent magnet. Hence the term inside-out DC motor.To make the rotor turn, there must be a rotating electric field. Typically a three-phase BLDC motor has three stator phases that are excited two at a time to create a rotating electric field. This method is fairly easy to implement, but to prevent the permanent magnet rotor from getting locked with the stator, the excitation on the stator must be sequenced in a specific manner while knowing the exact position of the rotor magnets.Position information can be gotten by either a shaft encoder or, more often, by Hall effect sensors that detect the rotor magnet position. For a typical threephase, sensored BLDC motor there are six distinct regions or sectors in which two specific windings are excited. 
These are as shown in Figure 1.</p>

 

<p align="center">
<img  src="images/figure1.png"></p>
<p align = "center"> Figure 1  BLDC commutation diagram
</p> 
<br />

 

<p style='text-align: justify;'>By reading the Hall effect sensors, a 3-bit code can be obtained with values ranging from 1 to 6.Each code value represents a sector on which the rotor is presently located. Each code value, therefore, gives us information on which windings need to be excited.Thus a simple lookup table can be used by the program to determine which two specific windings to excite and, thus, turn the rotor.
Note that state ‘0’ and ‘7’ are invalid states for Hall effect sensors. Software should check for these values and appropriately disable the PWM.</p>

 

### Change Notification Inputs
<p style='text-align: justify;'>
Taking this technique a step further, the Hall effect sensors can be connected to dsPIC inputs that detect a change (Change Notification (CN) inputs).
An input change on these pins generates an interrupt. In the CN Interrupt Service Routine (ISR) the user application program reads the Hall effect sensor value
and uses it to generate an offset in the lookup table for driving the windings of the BLDC motor.</p>


