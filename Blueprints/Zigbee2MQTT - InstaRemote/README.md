# Zigbee2MQTT – InstaRemote

![Status](https://img.shields.io/badge/Status-Experimental-orange)
![Testing](https://img.shields.io/badge/Testing-NOT_TESTED_YET-red)
![Home%20Assistant](https://img.shields.io/badge/Home%20Assistant-2026.1-blue)
![License](https://img.shields.io/badge/License-MIT-green)
[![Blueprint Import](https://img.shields.io/badge/Blueprint-Import-blue)](https://github.com/PVermeij/home-assistant-blueprints/blob/main/zigbee2mqtt_instaremote.yaml)

ℹ️ **Version 2025.11.14**

> [!CAUTION]  
> This blueprint is **NOT TESTED YET**.  
> Use at your own discretion and verify behavior in your Home Assistant environment before relying on it.

Control your lights using an **InstaRemote** switch paired through **Zigbee2MQTT**.  
The On/Off and Dim Up/Down buttons are pre‑assigned to lighting control, while buttons **1 through 6** can be mapped to any Home Assistant action you choose.

---

## ✨ Features

- Full support for **InstaRemote** Zigbee switches via Zigbee2MQTT  
- Built‑in handling for:
  - **On / Dim Up**
  - **Off / Dim Down**
  - **Brightness stepping**
- Six fully customizable buttons (`recall_0` → `recall_5`)  
- Optional **forced brightness** when turning lights on  
- Clean and predictable automation flow  
- Works with **any light entity** in Home Assistant

---

## 🧩 Requirements

- Home Assistant  
- Zigbee2MQTT integration  
- InstaRemote switch paired through Zigbee2MQTT  
- At least one controllable light entity  

---

## 🛠️ Blueprint Inputs

### **Remote**
Select the InstaRemote device (must come from the MQTT integration).

### **Light(s)**
Choose one or more light entities to control.

### **Force Turn‑On Brightness**
If enabled, pressing the **On** button will always turn on the lights at the configured brightness level.

### **Brightness**
The brightness percentage used when *Force Turn‑On Brightness* is enabled.

### **Button 1–6 Actions**
Assign any Home Assistant action to each of the six numbered buttons.

---

## 🔘 Button Mapping

| Remote Button | Zigbee2MQTT Action | Blueprint ID | Default Behavior |
|---------------|--------------------|--------------|------------------|
| On / Dim Up   | `on`               | `light_on`   | Turn on light (optionally force brightness) |
| Off / Dim Down| `off`              | `light_off`  | Turn off light |
| Dim Up        | `brightness_step_up` | `dim_up`   | Increase brightness by 5% |
| Dim Down      | `brightness_step_down` | `dim_down` | Decrease brightness by 5% |
| Stop Dimming  | `brightness_stop`  | `dim_stop`   | (Not used) |
| Button 1      | `recall_0`         | `select_0`   | Custom action |
| Button 2      | `recall_1`         | `select_1`   | Custom action |
| Button 3      | `recall_2`         | `select_2`   | Custom action |
| Button 4      | `recall_3`         | `select_3`   | Custom action |
| Button 5      | `recall_4`         | `select_4`   | Custom action |
| Button 6      | `recall_5`         | `select_5`   | Custom action |

---

## 📘 How It Works

### 1. **Turning Lights On**
- Pressing the **On** button triggers `light_on`.
- If *Force Brightness* is enabled, the light turns on at the configured brightness.
- Otherwise, the light turns on normally.

### 2. **Turning Lights Off**
- Pressing the **Off** button triggers `light_off`.
- The light turns off immediately.

### 3. **Dimming**
- Holding **Dim Up** increases brightness by 5% steps.
- Holding **Dim Down** decreases brightness by 5% steps.
- Releasing the button sends `brightness_stop` (not used in this blueprint).

### 4. **Custom Buttons (1–6)**
Each button triggers a `recall_x` action and runs the corresponding user‑defined sequence.

---

## 📦 Import This Blueprint

Paste this link into **Settings → Automations & Scenes → Blueprints → Import Blueprint**:

```
https://github.com/PVermeij/home-assistant-blueprints/blob/main/zigbee2mqtt_instaremote.yaml
```

---

## 📝 Changelog

### 2025.11.14
- Initial release  
- Added forced brightness option  
- Added support for six customizable buttons  
- Added dimming support  

---

## 🙋 Support

If you encounter issues or have suggestions, feel free to open an issue in the repository.  
Since this blueprint is **not tested yet**, feedback is especially welcome.
