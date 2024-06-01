# Notes / Journal

OpenMower on the Worx Landroid WR105SI.

Plan for næste gang: Find ud af hvad pinouts på motor er. Bekræft om de er kompatible med xESC (2 mini?) motor controller.

Find ud af om det giver mening at købe dem af ham, eller at bestille dem på PCBWay.

Virker den xESC controller uden CAN chippen?


"    2. xESCs are flashed with latest firmware and app/motor configuration was uploaded.

    3. ⚠️ Central xESC (mower) is different from left/right xESC (wheels), don’t mix them
"

Why is it different?


Lav et budget / shopping list

## Dimensions
OG: 170x180

Landroid (Box): 120x190

## Motor
The wheels are powered by Brushless DC (BLDC) motors. It seems that the pinouts are as follows:

Power Phases:

    U (Phase A): Color unknown
    V (Phase B): Color unknown
    W (Phase C): Color unknown

Hall Sensors:

    Hall Sensor 1: Color unknown
    Hall Sensor 2: Color unknown
    Hall Sensor 3: Color unknown
    Hall Power (+5V): Red
    Hall Ground (GND): Black

## Mainboard reshaping

Initial observations:

- Mainboard will never fit in the original Landroid motherboard box. Ignoring box from now on and assuming we 3D-print something to hold the new PCB.
- OG board is U-shaped. An L-shaped board in this approximate area seems feasible:
  ![mainboard-position](photos/mainboard-position.jpg)

Status 31/5-24:

- Forked OpenMower and started reshaping mainboard: [https://github.com/tausen/OpenMower/tree/landroid](https://github.com/tausen/OpenMower/tree/landroid)
- The three motor controllers and connectors north of those have been rotated counterclockwise and moved west. Moved fuses and charging connector out far west. Looks like this now (rev 9017d31):
  ![reshaped-mainboard-initial](photos/reshaped-mainboard-initial.png)
- There's about 15mm between motor controller caps and buck converter that can probably be squeezed if we need it to be narrower. Currently occupied by a mounting hole (accounting for about 10mm and will probably be moved) and a large `V_BATT` zone that is unaltered from the OG OpenMower mainboard (the remaining 5mm). Would it be safe to squeeze that zone?

Status 1/6-24:

- Initial fit check seems promising. Did a slight resize in bottom mid to get some more freedom when placing the PCB in the Landroid.

Next tasks:

- Mounting holes:
  - Can we use existing mounting used by original Landroid motherboard box?
  - If no: align mounting holes between PCB and new mainboard box, design new mainboard box to support existing Landroid mounting.
- Fit check: print board outline in 1:1 on A4, check
- Fit check: final height needed for motherboard? Will this be an issue?
- Any production parameters we should worry about? Like board thickness, copper weight, via covering, ...
- Fiducials: moved some around, where should they be?

## New mainboard box

Need to design a box for the reshaped mainboard.

- Ensure mounting holes fit somewhere we can place a screw in the Landroid
- How weather resilient must the new box be? Original Landroid motherboard is protected by epoxy, but connectors and motors etc are not particularly protected.

## GPS antenna mounting

Where? How?

# TODO

Buy a crimp tool.

4 New screws for battery box.

Hvordan virker charging? Kan den nuværende basestation genbruges?

# Resources
Landroid-Board: BLDC Motor Controller: https://www.onsemi.com/pdf/datasheet/mc33035-d.pdf
