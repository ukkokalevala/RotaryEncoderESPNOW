o split the rotary encoder and the OLED combination lock logic across two ESP devices using ESP-NOW, the encoder's ESP will act as a transmitter, sending updates (like position changes or button presses) to the OLED ESP, which acts as a receiver.
Overview of the Changes
1. Transmitter (Encoder ESP):
o Reads the rotary encoder's position and button state.
o Sends these values via ESP-NOW to the receiver.
2. Receiver (OLED ESP):
o Receives the position and button state updates from the transmitter.
o Updates the OLED display and processes the combination logic.

1  Define a Multi-Digit Combination:
• Allow the user to enter multiple digits by pressing the button after each digit.
• Store the digits in a buffer.
2  Validate Only After Full Combination is Entered:
• The system validates the entered code only after all digits are input.
3  Clear the Buffer After Validation:
• Reset the system for the next attempt after a validation.

How It Works
1. Multi-Digit Entry:
o Turn the rotary encoder to select a number.
o Press the encoder button to store the current number and move to the next digit.
o After entering all digits, the system validates the combination.
2. Combination Validation:
o The entered combination is compared with the predefined correctCombination array.
o If it matches, "Access Granted" is displayed.
o Otherwise, "Access Denied" is displayed.
3. Reset After Validation:
o The system clears the entered combination and resets for the next attempt.

Example Walkthrough
1. Combination: 423. In this case 
2. Turn the rotary encoder to 4 and press the button.
3. Turn the rotary encoder to 2 and press the button.
4. Turn the rotary encoder to 3 and press the button.

The system checks the entered combination (423):
o If correct, displays "Access Granted."
o If incorrect, displays "Access Denied."

Wiring (ESP32 + OLED RECEIVER)
OLED SDA GPIO 7
OLED SCL GPIO 6
Wiring (ESP32 + ROTARY ENCODER TRANSMITTER)
Rotary Encoder CLK GPIO 4
Rotary Encoder DT GPIO 3
Rotary Encoder SW GPIO 5
