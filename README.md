# 🪟 Dynamic Ventilation (Edge-Triggered, AH-Based)

This [Home Assistant](https://www.home-assistant.io/) blueprint recommends window ventilation when the **indoor absolute humidity (AH)** exceeds outdoor AH by a configurable threshold.  
It only sends **one notification when conditions change** (OK → Ventilate or Ventilate → OK), so you won’t get spammed.

<img width="1170" height="397" alt="image" src="https://github.com/user-attachments/assets/97d22647-fa95-4ff4-b1cd-39d08733688a" />

## 📋 Features

- Calculates **Absolute Humidity** (g/m³) indoors and outdoors from temperature + relative humidity.
- Uses the **Magnus formula** for [Saturation vapor pressure of water — Wikipedia](https://en.wikipedia.org/wiki/Humidity#Saturation_vapor_pressure_of_water).
- Notifies via:
  - Push notifications (e.g. `notify.mobile_app_*`)
  - Optional TTS announcements (Alexa, Google, etc.) **<-- currently unsupported**
- Edge-triggered: sends a single notification only when state changes.
- Clear emoji titles:
  - 🪟 **Open window to ventilate**
  - 🪟 **Close window**


## 🚀 Import into Home Assistant

In Home Assistant:

1. Go to **Settings → Automations & Scenes → Blueprints → Import Blueprint**.
2. Paste this URL:

```
https://raw.githubusercontent.com/adamcornforth/ha-open-window-blueprint/main/blueprints/automation/ha-open-window-blueprint/dynamic_ventilation_edge.yaml
```

## ⚙️ Inputs

- Indoor/Outdoor **temperature** and **humidity** sensors
- An `input_boolean` helper (used internally to remember the current state)
- Push notification service (required)
- Optional TTS service (currently unsupported - sorry!)
- Room name
- Threshold (default 3 g/m³)
- Customizable message templates for **ventilate** and **close**

<img width="1414" height="1600" alt="image" src="https://github.com/user-attachments/assets/7bd22b99-487a-4d6b-aa2e-76fd3d0e6dac" />

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
