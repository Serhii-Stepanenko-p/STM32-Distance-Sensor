# HC-SR04 Ultrasonic Distance Sensor with OLED Display

## Project Overview

This project demonstrates how to interface an HC-SR04 ultrasonic distance sensor with an SSD1306 OLED display using the STM32 Blue Pill microcontroller. The system measures distances and displays them in real-time on the OLED screen.

## Hardware Components

- **STM32F103C8T6 Blue Pill** - Main microcontroller
- **HC-SR04 Ultrasonic Sensor** - Distance measurement
- **SSD1306 OLED Display (128x64)** - Visual output
- **Jumper wires** - Connections
- **Breadboard** (optional) - For prototyping
- 
## Wiring Diagram

### HC-SR04 Connections
| HC-SR04 Pin | Blue Pill Pin | Description |
|-------------|---------------|-------------|
| VCC         | 5V            | Power supply |
| GND         | GND           | Ground |
| Trig        | PA9           | Trigger pin |
| Echo        | PA8           | Echo pin |

### SSD1306 OLED Connections
| OLED Pin | Blue Pill Pin | Description |
|----------|---------------|-------------|
| VCC      | 3.3V          | Power supply |
| GND      | GND           | Ground |
| SCL      | PB6           | I2C Clock |
| SDA      | PB7           | I2C Data |

## STM32CubeIDE Configuration

### 1. Clock Configuration
- **RCC**: Set High Speed Clock (HSE) to "Crystal/Ceramic Resonator"
- **Clock Configuration**: Set HCLK to 72 MHz

### 2. Timer Configuration
- **TIM1**: 
  - Clock Source: Internal Clock
  - Prescaler: 71 (for 1µs resolution)

### 3. I2C Configuration
- **I2C1**: 
  - Mode: I2C
  - Speed: Fast Mode (400 kHz)

### 4. GPIO Configuration
- **PA9**: GPIO_Output (Trigger pin)
- **PA8**: GPIO_Input (Echo pin)

## Required Libraries

### Header Files (Core/Inc/)
- `fonts.h` - Font definitions for OLED
- `ssd1306.h` - SSD1306 OLED driver

### Source Files (Core/Src/)
- `fonts.c` - Font implementation
- `ssd1306.c` - SSD1306 OLED driver implementation

## How It Works

1. **Trigger Phase**: A 10µs pulse is sent to the HC-SR04 trigger pin
2. **Echo Measurement**: The sensor sends ultrasonic waves and receives the echo
3. **Time Calculation**: Timer measures the duration of the echo pulse
4. **Distance Conversion**: Time is converted to distance using the formula: `Distance = (Time × 0.034) / 2`
5. **Display Update**: Distance is shown on the OLED display in real-time

![image](https://github.com/user-attachments/assets/b50f27e9-6349-4e37-ae02-811d28e549fe)

