# 🪟 Dynamic Ventilation (Edge-Triggered, AH-Based)

This [Home Assistant](https://www.home-assistant.io/) blueprint recommends window ventilation when the **indoor absolute humidity (AH)** exceeds outdoor AH by a configurable threshold. It runs every 5 minutes, but only sends **one notification when conditions change** (OK → Ventilate or Ventilate → OK).

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fraw.githubusercontent.com%2Fadamcornforth%2Fha-open-window-blueprint%2Frefs%2Fheads%2Fmain%2Fblueprints%2Fautomation%2Fadamcornforth%2Fdynamic_ventilation_edge.yaml)

## 🚀 Import into Home Assistant

Use the "import blueprint to HA" button above, or:

In Home Assistant:

1. Go to **Settings → Automations & Scenes → Blueprints → Import Blueprint**.
2. Paste this URL: `https://raw.githubusercontent.com/adamcornforth/ha-open-window-blueprint/refs/heads/main/blueprints/automation/adamcornforth/dynamic_ventilation_edge.yaml`

## 📋 Features

<img width="500" alt="image" src="https://github.com/user-attachments/assets/9a2a0f02-2419-46b5-89d3-5e3546366659" />

- Calculates **Absolute Humidity** (g/m³) indoors and outdoors from temperature + relative humidity.
- Uses the **Magnus formula** for [saturation vapor pressure of water](https://en.wikipedia.org/wiki/Humidity#Saturation_vapor_pressure_of_water).
- Notifies via:
  - Push notifications (e.g. `notify.mobile_app_*`)
  - Optional TTS announcements (Alexa, Google, etc.) **<-- currently unsupported**
- Edge-triggered: sends a single notification only when state changes.
- Clear emoji titles:
  - 🪟 **Open window to ventilate**
  - 🪟 **Close window**

## ⚙️ Inputs

- Indoor/Outdoor **temperature** and **humidity** sensors
- An `input_boolean` helper (used internally to remember the current state)
- Push notification service (required)
- Optional TTS service (currently unsupported - sorry!)
- Room name
- Threshold (default 3 g/m³)
- Customizable message templates for **ventilate** and **close**

<img width="900" alt="image" src="https://github.com/user-attachments/assets/7bd22b99-487a-4d6b-aa2e-76fd3d0e6dac" />

---

## 🧪 Example Notification

**Title:** 🪟 Open window to ventilate — Dining Room  
**Message:**
```
Dining Room should be ventilated.
Indoor 72%, 12.7 g/m³ — 20.1°C
Outdoor 80%, 12.9 g/m³ — 18.6°C
ΔRH = -8%, ΔAH = -0.2 g/m³ (thr 3.0)
```

---

## 🙌 Credits

- Inspired by the original “Open window recommendation (AH-based)” blueprint from the Home Assistant community.
- https://community.home-assistant.io/t/open-window-recommendation-absolute-humidity-based-blueprint/897695 
