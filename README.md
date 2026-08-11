# 🍔 Automated Packing System for Food Orders

An end-to-end automated meal-assembly system that takes a customer's order from a touchscreen kiosk to a packed, ready-to-collect tray — no staff required in the loop.

Senior graduation project · Department of Electrical & Computer Engineering, King Abdulaziz University · 2026

![Final-prototype](final-prototype.png)

---

## Overview

Fast-food kitchens lose speed and accuracy to staff shortages and manual packing. This project replaces that manual step with a coordinated hardware + software pipeline: a customer places an order on a web kiosk, the order streams to the hardware in real time, and a conveyor-and-dispenser rig assembles the tray automatically while tracking inventory and texting the customer when it's ready.

**Result on the built prototype:** 93.3% overall system accuracy, 100% dispensing accuracy, and an average assembly time of ~29 seconds — well inside the 5-minute target.

## Key Features

- 🖥️ **Bilingual ordering kiosk** — English/Arabic web interface (RTL support) running in kiosk mode on a Raspberry Pi touchscreen
- ☁️ **Real-time order pipeline** — orders sync instantly from the web front end to the hardware controller via Firebase Realtime Database
- 🤖 **Automated tray handling** — dual linear actuators lift and load trays onto a motorized conveyor
- 🎯 **Precision dispensing** — IR-sensor-counted DC gear motor dispensers stop automatically once the ordered quantity is reached
- 📦 **Live inventory monitoring** — LED/buzzer alerts trigger at a 20% stock threshold so staff can refill before a station runs dry
- 📲 **SMS pickup notifications** — an A9G GSM/GPRS module texts the customer as soon as their order is packed
- 🧩 **Modular, scalable architecture** — adding a menu item means adding a station, not redesigning the system

## System Architecture

A Raspberry Pi acts as the main controller, coordinating two ESP32 sub-controllers over UART for the individual dispensing stations, while Firebase bridges the web front end and the embedded hardware.

![System architecture diagram](system-architecture.png)

## Ordering Interface

![Ordering interface on kiosk touchscreen](ordering-interface.png)

## Tech Stack

| Layer | Technology |
|---|---|
| Front end | HTML, CSS, JavaScript (bilingual EN/AR, RTL support) |
| Back end / sync | Firebase Realtime Database, Firebase Hosting |
| Main controller | Raspberry Pi (Python — `firebase-admin` listener, GPIO control) |
| Station controllers | ESP32 × 2 (serial/UART command protocol: `DISPENSE`, `RESET`, `STATUS`) |
| Motor control | L298N motor drivers, DC gear motors, 12V linear actuators |
| Sensing | IR sensors for tray detection and item counting |
| Notifications | A9G GSM/GPRS module (SMS) |
| Alerts | LED, buzzer, push button (manual refill/reset) |



## Team

- Maram Althubyani
- Rahaf Abonab
- Sarah Samarkandi

**Supervisor:** Dr. Thangam Palaniswamy — Department of Electrical and Computer Engineering, King Abdulaziz University

