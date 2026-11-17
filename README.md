# Softshell Device

**A soft, pressure-sensitive object that "breathes" back at you through vibration, calming down when you touch it gently and getting restless when you squeeze it erratically.**

Part of the **Softshell** series → see also [softshell-v5](https://github.com/lileinsteinbrain/softshell-v5) (screen-based version).

## The idea
Most interfaces treat touch as a command: press → something happens. Softshell treats touch as a *conversation over time*. The device keeps an internal "mood" that drifts toward calm on its own, is pushed up by irregular, jittery touch and settled by steady pressure. You don't control it so much as co-regulate with it.

## How it works
```
 FSR pressure sensor ──► R  (how much / how steady you press)
                     └─► U  (how irregular the pressure is)
                                 │
                 S  "entropy" of the system:  dS/dt = k_in·U − k_out·R − k_relax·(S − S0)
                 T  "tempo" follows S (more order → slower, calmer)
                                 │
 DRV2605 haptic driver ◄─────────┘  continuous breathing-like vibration at tempo T
```
- **Input:** one force-sensitive resistor read by an ESP32
- **State:** two smoothed values, entropy S and tempo T, with inertia so nothing changes abruptly
- **Output:** real-time vibration via an Adafruit DRV2605 haptic driver; a TouchDesigner sketch visualises the state

## What's in this repo
| Path | What it is |
|---|---|
| `Softshell_Device/softshell_device/softshell_device.ino` | ESP32 firmware: sensing, state model, haptic output |
| `Softshell_Device/softshell visual.toe` | TouchDesigner visualisation |
| `Softshell_Device/notes_mapping.md` | How the device values map to the TouchDesigner visuals |

## Status
Early research prototype.
- ✅ Responds continuously to touch; gentle, steady contact leads to a calmer state
- 🔲 The entropy model is heuristic and not yet validated with users
- 🔲 Long-term interaction has not been studied
