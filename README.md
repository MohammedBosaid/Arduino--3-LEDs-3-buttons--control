# Arduino-(3-LEDs-3-buttons)-control


## Overview
This project demonstrates how to use three pushbuttons to control three LEDs on an Arduino Uno, utilizing the built-in `INPUT_PULLUP` resistors.

## Components
- Arduino Uno R3  
- Small breadboard  
- 3 × Pushbutton  
- 3 × LED (any color)  
- 3 × 330 Ω resistor  
- Jumper wires  
- USB cable or battery for power  

## Wiring

1. **Buttons (Inputs)**  
   - Button1 → Pin 2  
   - Button2 → Pin 3  
   - Button3 → Pin 4  
   - Other side of each button → GND  
   - (We use `INPUT_PULLUP`, so no external pull-down resistors are needed.)

2. **LEDs (Outputs)**  
   - LED1 Anode → 330 Ω resistor → Pin 8  
     LED1 Cathode → GND  
   - LED2 Anode → 330 Ω resistor → Pin 9  
     LED2 Cathode → GND  
   - LED3 Anode → 330 Ω resistor → Pin 10  
     LED3 Cathode → GND  

![Wiring Diagram](circuitconnection.png)


## How to Run
1- Open this folder in the Arduino IDE (or simulate in Tinkercad Circuits).

2- Verify the wiring matches the diagram above.

3- Upload the sketch to your Arduino Uno.

4- Press each button to light its corresponding LED.

## Possible Enhancements
- Implement toggle mode so each press flips the LED state.

- Add delays or blinking patterns.

- Replace LEDs with buzzers or servos for different outputs.




## Code (`src/button_leds.ino`)

```cpp
// Pin assignments
const int button1 = 2;
const int button2 = 3;
const int button3 = 4;

const int led1 = 8;
const int led2 = 9;
const int led3 = 10;

void setup() {
  // Configure buttons with internal pull-up
  pinMode(button1, INPUT_PULLUP);
  pinMode(button2, INPUT_PULLUP);
  pinMode(button3, INPUT_PULLUP);
  
  // Configure LEDs as outputs
  pinMode(led1, OUTPUT);
  pinMode(led2, OUTPUT);
  pinMode(led3, OUTPUT);
}

void loop() {
  // Turn each LED on when its button is pressed (LOW)
  digitalWrite(led1, digitalRead(button1) == LOW);
  digitalWrite(led2, digitalRead(button2) == LOW);
  digitalWrite(led3, digitalRead(button3) == LOW);
}
