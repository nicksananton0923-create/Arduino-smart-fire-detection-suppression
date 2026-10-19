# Arduino-Based Smart Fire Detection and Alarm Prototype

An educational Arduino project exploring flame and smoke/gas sensor inputs, alarm-state logic, audible and visual alerts, and a simulated suppression indicator.

> **CRITICAL SAFETY NOTICE:** This project is not a certified fire alarm, life-safety system, or fire-suppression system. Do not rely on it to protect people or property. The default suppression output is a simulated indicator, not a verified fire-extinguishing mechanism.

 🎯 Project Objective

Demonstrate embedded-system concepts used in a simple sensor-monitoring and alarm workflow:

- Read analog sensor signals.
- Filter measurements and debounce detection conditions.
- Evaluate sensor conditions using configurable thresholds.
- Transition between normal, pre-alarm, latched-alarm, and fault states.
- Provide LED, buzzer, and Serial Monitor indications.
- Exercise selected logic through software simulation commands.

The repository describes a proposed educational configuration. The exact physical hardware, sensor models, and wiring must be confirmed before any physical build is attempted.

 ✨ Features Described in the Source Code

- Flame-sensor and MQ-2 analog inputs.
- Eight-sample moving-average filters.
- Configurable detection thresholds and hysteresis.
- A warm-up interval and baseline measurement for the MQ-2 channel.
- Normal, pre-alarm, latched-alarm, and fault states.
- LED and buzzer status patterns.
- Serial diagnostics and simulation commands.
- A configurable, simulated suppression output.
- Optional LCD and servo features controlled by compile-time settings.

These are source-code features, not proof that the prototype has passed testing or meets any fire-safety requirement.

 🧰 Proposed Hardware

| Component | Intended role |
|---|---|
| Arduino Uno | Main controller |
| Flame sensor module with analog output | Light/IR-responsive sensor input |
| MQ-2 module with analog output | Smoke/gas-responsive sensor input |
| Green and red LEDs with resistors | Status and alarm indication |
| Amber/blue LED with resistor | Simulated suppression indication |
| Active buzzer driven through an NPN transistor | Audible demonstration alert |
| Reset push button | Manual alarm-reset input |
| Optional 16×2 I²C LCD | Status display |
| Optional servo | Visual demonstration only |

This is a proposed component configuration, not a confirmed inventory of the original hardware.

 🔌 Proposed Pin Connections

| Function | Arduino Uno pin |
|---|---|
| Flame sensor analog output | A0 |
| MQ-2 analog output | A1 |
| Green LED through resistor | D4 |
| Red LED through resistor | D5 |
| Simulated suppression indicator | D6 |
| Reset button to GND | D7 |
| Buzzer driver transistor base through a resistor | D8 |
| Optional servo signal | D9 |
| Optional LCD SDA / SCL | A4 / A5 |

These assignments are labelled as proposed in the source. Verify the exact module pin labels, supply requirements, output voltages, and logic levels before connecting power.

 💻 Source Code and Operation

The Arduino sketch is stored in [`Code`](<Code>).

The default configuration does not require third-party libraries. The optional LCD feature requires a compatible `LiquidCrystal_I2C` library; the optional servo feature uses the Arduino `Servo` library.

The Serial Monitor uses **9600 baud**. The sketch recognises these single-character commands:

| Command | Purpose |
|---|---|
| `h` | Show command help |
| `s` | Print current status and diagnostics |
| `r` | Request reset of a latched alarm |
| `f` | Toggle simulated flame condition |
| `m` | Toggle simulated smoke condition |

Simulation commands exercise software logic only. They do not verify sensor performance or the ability to detect a real fire.

 🔄 State-Machine Concept

The code includes these states:

- **NORMAL:** normal-status indication.
- **PRE-ALARM:** warning indication while a sensor condition is present.
- **ALARM-LATCHED:** persistent alarm state requiring a reset request when conditions are clear.
- **FAULT:** an indication for selected sensor readings that remain outside configured limits.

The thresholds, timing, sensor characteristics, and fault-detection logic require validation. A software state machine alone does not make a fire-protection system reliable or compliant.

 📚 Existing Project Documentation

- [Bill of Materials](<Bill of Materials (BOM)>)
- [Project review](<Project Review>)
- [Proposed wiring](<Wiring>)
- [System diagrams](<System Diagrams>)
- [Testing plan and results template](<Testing Plan and Results Template>)
- [Troubleshooting guide](<Troubleshooting Guide>)
- [Questions and answers](<Questions and Answers>)
- [GitHub setup guide](<GitHub Setup Guide>)
- [Wiring and logic image](<wiring and logics.jpg>)

These links preserve the existing paths in the repository.

 🧪 Safe Testing and Verification

The repository includes a testing template with blank observed-result fields. Record only tests that have actually been performed, including the hardware models, supply, environment, observed behaviour, and date.

For initial software checks:

1. Review the sketch and proposed wiring.
2. Compile the default configuration in the Arduino IDE.
3. Use the `f` and `m` simulation commands to examine software state transitions.
4. Check the diagnostic output and reset behaviour.
5. Record observed results separately from expected results.

Do not create a real fire to test the prototype. Do not connect the simulated output to pumps, valves, pressurized equipment, extinguishing agents, mains-powered equipment, or any hazardous load. Physical sensor testing must follow suitable component guidance and an appropriately controlled, safe test procedure.

 ⚠️ Safety and Limitations

- This project is for education and software demonstrations only.
- It is not certified or suitable as a substitute for approved fire-detection, alarm, or suppression equipment.
- The simulated suppression output does not extinguish fire.
- Do not connect real suppression equipment to the sketch.
- Sensor thresholds and simple fault heuristics may miss faults or produce false alarms.
- The alarm latch is held in RAM and is not retained through power loss.
- The optional servo can move during the startup output test when enabled; keep it disconnected from any hazardous mechanism.
- Real fire-protection installations require appropriately qualified professionals, certified equipment, and applicable standards and regulations.

 📈 Future Improvements

- Review and validate the state machine and fault-handling logic.
- Add repeatable, documented software simulation tests.
- Record source versions and actual test results.
- Improve sensor supervision and recovery behaviour.
- Add event logging only after the underlying sensing and control behaviour is validated.
- Keep any physical suppression system outside this educational prototype unless it is independently designed, reviewed, and verified by qualified professionals.

 📄 Project Status

**Educational source code and documentation are available. Hardware verification, sensor reliability, and fire-protection performance are not established. The prototype must not be used as a real fire-safety system.**
