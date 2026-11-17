# Softshell TouchDesigner mapping (plan)

Input from the device (serial):

| Value | Range | Use |
|---|---|---|
| R | [0, 1] | not used directly; mainly for debugging |
| U | [0, 1] | can map to noise / blur amount |
| S | [0, 1] | visual stability: 0 = chaos, 1 = order |
| T | [0.6, 2.0] | breathing frequency (Hz) |

In TouchDesigner:
- **T controls**
  - LFO frequency of the scale CHOP on the main sphere / field
  - ripple expansion speed
- **S controls**
  - noise amplitude / displacement amount
  - glow / blur level (higher S → cleaner, less noise)

Later:
- **U** could drive
  - randomness of flicker
  - small phase jitter
