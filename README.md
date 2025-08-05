#  Displacement Tracker

This  project uses the **ADXL345 accelerometer** to estimate displacement in 3D space, applies a simple low-pass filter to smooth the data, and displays displacement and frequency information on an **SSD1306 OLED screen**.

It’s ideal for experimenting with motion tracking, basic sensor fusion, or learning how to process raw accelerometer data in real-time.

---

##  What It Does

- Reads acceleration data from the **ADXL345** accelerometer over I2C.
- Applies a **low-pass filter** to smooth out the raw signal.
- Estimates displacement using:  
  `d = 0.5 * a * t²`
- Displays:
  - X and Z displacement (in cm)
  - Frequency of motion change in X and Z

---

##  Hardware 

- Any compatible board
- ADXL345 accelerometer module (I2C)
- SSD1306 OLED display (128x32, I2C)
- Breadboard and jumper wires
- USB cable 

---

##  Wiring Overview

| Module         | Arduino Pin       |
|----------------|------------------|
| ADXL345 SDA     | A4          |
| ADXL345 SCL     | A5           |
| SSD1306 SDA     | A4 (shared)       |
| SSD1306 SCL     | A5 (shared)       |
| ADXL345 VCC     | 3.3V or 5V        |
| ADXL345 GND     | GND               |
| SSD1306 VCC     | 3.3V or 5V        |
| SSD1306 GND     | GND               |

Note: Both the OLED and ADXL345 use I2C, so they share SDA/SCL.

---

##  How to Use

1. Connect the hardware as shown above.
2. Upload the code 
3. Open the **Serial Monitor** (9600 baud) to see raw displacement values.
4. Watch the OLED screen for:
   - X and Z axis displacement (cm)
   - Frequency (Hz) of displacement changes in X and Z
   

---

##  Customization

- **Displacement Units**: The formula is based on simple Newtonian motion. It’s an approximation — you can calibrate it further using real-world measurements.
- **Filtering**: You can tweak `alpha` in this line to make the filter smoother or more responsive:
  ```cpp
  float alpha = 0.6;
