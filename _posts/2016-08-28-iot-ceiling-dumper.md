---
layout: post
title: "IoT Ceiling Dumper project"
excerpt: "Rain down food from above, automatically"
tags: [Clouds, IoT]
image:
# pic silver robot white skin handshake 1900x500
  feature: https://cloud.githubusercontent.com/assets/300046/14622149/306629f0-0585-11e6-961a-dc8f60dadbf6.jpg
  credit: 
  creditlink: 
comments: true
---
<i>{{ page.excerpt }}</i>

[![Gitter](https://badges.gitter.im/wilsonmar/wilsonmar.github.io.svg)](https://gitter.im/wilsonmar/wilsonmar.github.io?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge)

{% include _toc.html %}

Here is (the beginnings of) a description of how I made it happen, so you can, too.

<hr />

## Why drop stuff from the ceiling? #

There are several reasons why someone would want to drop stuff from the ceiling.
Balloons at a celebration.
Red liquid at a <a target="_blank" href="http://www.imdb.com/title/tt0074285/">
Carrie" movie</a> remake.

Or hay for animals in a barn, which is my interest here.
I have a barn for two donkeys.
My wife gets up before dawn each morning to feed them,
or they will <a target="_blank" href="https://www.youtube.com/watch?v=nWS4Eu8E2z4&t=5s">
bray annoyingly</a>.

We can't leave a lot of food laying around 
because they eat everything they can reach.

Thus, I want a box above the animals to hold their hay 
for release automatically at a set time.

(BTW, my wife's against all this automation because she says she has to get up
anyway for other chores with the chickens and ducks, etc. :)
Anyway, I'm undeterred by practicality.
So read on.

<a target="_blank" href="http://forum.arduino.cc/index.php?topic=300690.0">
This post talks about</a>
a trap door held by a pin attached to a solenoid.
A quick pulse releases it.
A transistor or MOSFET to drive the release to protect the Arduino from excess current or spikes.

<a target="_blank" href="https://www.youtube.com/watch?v=zi3AFFOQSaw">
One video</a>
shows how to release from an RC plane a parachute release mechanism
using a 9 gram servo with an armature arm with a wire that holds 
(until release)
a rubber band that holds the package.


## How it works #

Here's a wish list:

   0. The shelf is raised and lowered by four ropes,
   one on each corner. 

   0. During the dumping (feed) operation, 
   only one side is fully lowered so whatever is on it slides off.

   0. The <a href="#Release">release</a> if a vertical door is needed
   to hold enough stuff without spilling over.

   0. We use two sets of <a href="#Pulleys">pulleys</a>, one for each side.
   Pulleys enable a smaller motor to be used.

   0. <strong>Safety wire cables</strong> 
   keep the shelf from crashing to the floor ?

   0. Like a garage door, <strong>lasers</strong> sense whether there is something in the
   way before the platform is lowered.

   0. <a href="#StepperMotors">Two stepper motor</a> 
   controls each of 2 sides of the platform.
   Both would operate to raise or lower. Only one would operate to dump contents.
   
   0. A <strong>bell</strong> sounds before the food is dumped
   so the donkeys know to avoid the dump. Right.

   0. <a href="#Sensors">Sensors</a> identify if conditions are safe - 
   the position of the various parts (motor) 
   and whether each is still working.

   0. There would be <a href="#Logic">logic</a> on the Ardunio board that 
   to not do something if sensors indicate.

   0. In "productive mode", when it's time (5 minutes before dawn each day),
   the shelf is emptied automatically by lowering one side
   and releasing a latch.

   0. There should be a <strong>manual alternative</strong>
   to lower the shelf and open the door. That's in case of loss of electricity
   or when the computer part doesn't work.

   0. In "test mode", we would press a button to raise it; another button to lower it;
   and a third button to dump the food.
   This could be a multi-purpose button where one tap raises,
   two taps lowers it, and a long press to dump from above.

## Parts #

  <a name="Platform"></a>

* [__] <a target="_blank" href="http://www.homedepot.com/p/Pine-Plywood-Common-23-32-in-x-4-ft-x-8-ft-Actual-0-688-in-x-48-in-x-96-in-799397/202677224">
   $30 from Home Depot</a>
   one finished sheet of 3/4 inch pine <strong>plywood</strong> -
   4x8 foot or 48 x 96 inches used for framing. 

   At 2.5 pounds per square foot,
   the whole sheet weights about 84 lbs.

* [__] Have the yard make 4 cuts. 
   Cut it in half along the long edge for a 48x48 inch square shelf,
   then cut the four 12x48 slats for the walls and door.

   <strong>QUESTION: Does this provide enough volume to hold enough feed?</strong>
   We would need enough space to hold enough 
   for a single meal for two donkeys. Maybe 3.

* Make a 45 degree edge on each of the 3 side boards.

* [__] <a target="_blank" href="http://www.homedepot.com/p/Simpson-Strong-Tie-ZMAX-18-Gauge-Galvanized-Steel-Angle-A21Z/100375047">
   $0.58 from Home Depot</a> 14 galvanized steel 
   <strong>L brackets</strong>. 
   Attach 3 each of 3 to attach the 3 sides to the base.

* [__] 192 wood screws (4 each for 14 brackets), 1/2 inch long with tapered head.

* [__] Drill a hole on each of 4 corners.

* [__] 4 <strong>eye rings</strong> on the top of the sides
   for ropes to attach to the box.

  <a name="Release"></a>

* [__] Hinges for the door.

* [__] <a target="_blank" href="https://solarbotics.com/product/gm2/">
   gear motor</a> actuator to lock and release latch.

* [__] Install the door release with a cable to the Arduino.

  <a name="Pulleys"></a>

   A hoist for a bicycle of about 100 lbs. is
   <a target="_blank" href="https://www.amazon.com/dp/B003VOX1XU?psc=1">
   $20 from Amazon</a>. Two sets should support 200 lbs, right?
   But that may not be enough for the platform.

* [__] 4 sets of block and tackle pulleys for 1/2 inch diameter size rope.
   <a target="_blank" href="https://www.amazon.com/Generic-Pulley-Block-Tackle-Hoist/dp/B001Z0WELC">$21 each from Amazon</a>.

   The four wheels provides 7:1 lifting ratio power for 2 tons of working load capacity.

* [__] <strong>Bolts</strong> on the ceiling to hold the pulleys
   should be braced to support that.

   Additional bracing may be needed for your ceiling.

   Check with a construction specialist.

* [__] 4 ropes to lower the platform almost to the ground.
   Although the height is about 10 feet each,
   about 4 times that is needed to go through the pulleys.
   So we get a standard size rope of 100 feet (30.48 meters).

   The 1/2 inch climber ropes are about $30 used, $40 new 
   <a target="_blank" href="http://www.ebay.com/bhp/rock-climbing-rope">
   on Ebay</a>

   - Measure the weight of the platform with ropes 
   at maximum load. The estimate is 100 pounds max.

   <a name="StepperMotors"></a>

   How to move the rope electronically?

* [__] TODO: Stepper motors sized to handle the weight.

   

   <a name="Sensors"></a>

* [__] Sensors to detect slippage.

* [__] Notification

* [__] Arduino board to signal the stepper motor.

* [__] Power supply


## Breadboard #

Research:

   https://www.youtube.com/watch?v=RakXequOrSY

   and

   https://www.youtube.com/watch?v=WKdyBZvlFXk

0. Blue wire DC-   


## Servo vs. Stepper Motors

<a target="_blank" href="https://www.arduino.cc/en/Reference/Servo">
The Arduino website explains</a>
Servos have integrated gears and a shaft that can be precisely controlled. 
Standard servos allow the shaft to be positioned at various angles, 
usually between 0 and 180 degrees.
Continuous rotation servos allow the rotation of the shaft to be set to various speeds.
The Servo library supports up to 12 motors on most Arduino boards and 
48 on the Arduino Mega. 
On boards other than the Mega, use of the library disables analogWrite() (PWM) functionality on pins 9 and 10, whether or not there is a Servo on those pins. On the Mega, up to 12 servos can be used without interfering with PWM functionality; use of 12 to 23 motors will disable PWM on pins 11 and 12.

<a target="_blank" href="https://www.youtube.com/watch?v=FBA4zzVNds8">
This video explains:</a> A stepper motor is used in applications requiring about 2000 rpm or less where you need a lot of torque at the low end, where as a servo motor is typically used for your higher speed applications that are more dynamic and require more acceleration and deceleration typically 2000 rpm and higher.

A servo is always built with a feedback mechanism.

* https://www.youtube.com/watch?v=oOvRf7xa5r4


<a target="_blank" href="https://www.youtube.com/watch?v=AcLUopVZMco">
YouTube video: Practical Insight in selecting stepper motors for your build</a>
describes the difference between NEMA (National Electrical Manufactures Association)
stepper motor numbers:

   * NEMA 17 is 1.7" <br />
   holds 53 ounces of weight

   * NEMA 23 is 2.3" takes a #10 machine screw<br />
   holds 425 ounces (26.5 pounds)

   * NEMA 34 is 3.4" takes a 1/4" screw<br />
   holds 1232 ounces (77 pounds)

<a target="_blank" href="https://www.youtube.com/watch?v=mSU-GeEe0P0">
Some salvage the motors from scrap copy machines</a>


## Resources #

* http://www.leevalley.com/US/wood/page.aspx?p=74353&cat=51&ap=3


## More on IoT #

This is one of a series on IoT:

{% include iot_links.html %}
