# URM37 Ultrasonic Sensor Library for Arduino 🚀

A robust, easy-to-use Arduino library for the URM37 ultrasonic distance sensor series. This library enables precise distance measurements using sound waves through a simple PWM interface. Think of it like a bat using echolocation! 🦇

## Features ✨

- Simple PWM-based distance measurements 📏
- Compatible with multiple URM37 versions (v3.2, v4.0, v4.1, v5.0) 🔄
- Configurable measurement units (centimeters/inches) 📊
- Error handling and diagnostics 🔍
- Minimal pin requirements (single digital pin) 🔌
- Comprehensive documentation and examples 📚

## Hardware Requirements 🛠️

- Arduino board (Any model) 🎛️
- URM37 ultrasonic sensor (v3.2 or later) 📡
- 3 jumper wires 🔋
- Power supply (3.3V or 5V, sensor-dependent) ⚡

## Installation 💻

### Using Arduino Library Manager (Recommended) ⭐

1. Open Arduino IDE
2. Navigate to `Tools` → `Manage Libraries...`
3. Search for "URM37"
4. Click "Install"

### Manual Installation 📥

1. Download this repository as a ZIP file
2. In Arduino IDE: `Sketch` → `Include Library` → `Add .ZIP Library...`
3. Select the downloaded ZIP file
4. Restart Arduino IDE

## Wiring 🔌

Connect your URM37 sensor to Arduino using these pins:

| URM37 Pin | Arduino Pin | Notes |
|-----------|-------------|-------|
| VCC | 5V/3.3V | Check sensor specifications |
| GND | GND | |
| PWM/TRIG | Any Digital Pin | Specified in code |
| COMP/TX | Not Connected | Used for UART mode only |
| ECHO/RX | Not Connected | Used for UART mode only |

## Quick Start 🚦

```cpp
#include <URM37.h>

const int SENSOR_PIN = 9;
URM37 sensor(SENSOR_PIN);

void setup() {
  Serial.begin(9600);
}

void loop() {
  float distance = sensor.getDistance();
  
  if (sensor.isValidReading()) {
    Serial.print("Distance: ");
    Serial.print(distance);
    Serial.println(" cm");
  } else {
    Serial.println("Error: Invalid reading");
  }
  
  delay(100);
}
```

## Advanced Usage 🎯

### Temperature Compensation 🌡️

```cpp
// Enable temperature compensation
sensor.enableTemperatureCompensation();

// Get temperature-compensated distance
float distance = sensor.getDistanceCompensated();
```

### Change Measurement Units 📐

```cpp
// Switch to inches
sensor.setUnit(URM37::INCHES);

// Switch back to centimeters
sensor.setUnit(URM37::CENTIMETERS);
```

## Troubleshooting 🔧

### No Readings or Incorrect Values ❌

1. **Check Wiring** 🔌
   - Verify all connections are secure
   - Ensure correct voltage (5V or 3.3V)
   - Try different digital pins

2. **Environmental Factors** 🌍
   - Clear any obstacles in sensor's path
   - Avoid soft/sound-absorbing surfaces
   - Keep sensor away from strong EMI sources

3. **Code Issues** 💻
   - Verify pin number matches wiring
   - Ensure proper delay between readings
   - Check Serial Monitor baud rate

### Known Limitations 📋

- Minimum distance: 2cm
- Maximum distance: 500cm
- Update rate: Maximum 20Hz
- Surface angle: Best results at 90°
- Surface texture: Works best with solid, flat surfaces

## Contributing 🤝

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

Please include:
- Clear commit messages
- Documentation updates
- Test cases for new features

## License 📜

MIT License - See [LICENSE](LICENSE) file for details
