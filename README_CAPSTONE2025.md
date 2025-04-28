<div align="center" style="text-align: center;">

<h1>Capstone 2025 opendbc Changes</h1>

</div>

---

The primary purpose for editing the opendbc repo thus far has been to add newly discovered CAN messages and signals to the Nissan Leaf DBC file and ensure that those signals can be recognized by Openpilot. 

---

## Newly Added Messages and Signals

### Throttle
A new message called Throttle was named. The signals for the electric throttle control actuator was identified and the counter for the message. 

The electric throttle control works by allowing air to enter and exit the engine to provide power to the engine for acceleration adn deceleration. The signal is called "THROTTLE_CONROL"

### Brake_Pedal
A new signal was added to the Brake_Pedal message. The newly added signal is "BRAKE_PRESSURE". The brake fluid pressure signal controls how much pressure is applied to the wheels of the vehicle to enable braking. 


## Modified Files

### car.capnp

This file defines variables for the struct of the car state. Adding variables for both throttle and brakePressure allows us to store the values sent over CAN communication in a different file. 

### carstate.py

This file parses out the relevant information from the CAN stream using the car's DBC file. The messages and signals for throttle and brakePressure needed to captured in the variable that we added to car.capnp

### nissan_leaf_2018.dbc

This is the dbc file that the nissan leaf uses. The newly discovered messages and signals needed to be added here in accordance with the dbc file format. Specific parameters for this format were found by viewing the signal in cabana. 

