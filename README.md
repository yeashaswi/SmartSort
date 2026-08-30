# SmartSort-
An AI-powered automated waste segregation system designed for homes and source-level sorting of mixed household waste.
# ♻️ SmartSort: AI-Powered Automated Waste Segregation

> A compact system combining controlled feeding, smart sensing, computer vision, and mechanical diversion to sort mixed household waste.

---

## 🌍 Overview
* India generates approximately 62 million tonnes of municipal solid waste annually, with over 70% remaining mixed at source.
* Manual sorting is time-consuming, inconsistent, and unsuitable for continuous small-scale automation.
* SmartSort converts messy mixed waste into controlled, near-single-item inputs for automated segregation.

---

## 🚀 Core Pipeline & Workflow
* **Controlled Input:** A 10-paddle Ferris-wheel feeder with 36° indexed movement prevents large piles from entering the system at once.
* **Pre-processing:** A drainage deck removes free liquid, while a vibratory spreader de-clumps and singulates objects.
* **AI Analysis:** A USB-C webcam captures individual items on an inspection platform, and a cloud Vision Language Model (VLM) via the Google GenAI SDK identifies the category.
* **Decision & Sorting:** The microcontroller tracks object position, and dual hinged inspection platforms with a motorized sorting pipe direct items into Wet/Compostable, Dry/Recyclable, or Misc/Reject streams.

---

## ⚙️ Hardware & Tech Stack
* **Microcontrollers:** Arduino Uno (controls the top Ferris wheel) and ESP32 (controls inspection platform flaps and final sorting pipe)[cite: 9].
* **Actuators:** 4 × MG996R heavy-duty servos.
* **Sensors:** USB-C webcam and dual IR sensors for item drop/movement feedback.
* **Software:** Python, OpenCV, and the Google GenAI Python SDK.

---

## 🛡️ Challenges & Mitigations
* **Irregular or sticky waste:** Handled via 10-paddle indexed feeding and controlled mechanical movement.
* **Cloud VLM connectivity:** Internet dependence is explicitly acknowledged with future edge/offline model fallback planned.
* **Lighting and background variations:** Mitigated using a stable inspection position and controlled camera setup.
* **Recognition timeout:** Unrecognized or slow cases are automatically routed to the Misc/Reject path rather than forced into a category.

---

## 📊 Impact and Benefits
* **Social:** Reduces direct handling of mixed waste and encourages better source-segregation practices.
* **Environmental:** Improves the separation of dry/recyclable materials and routes organic waste toward composting.
* **Economic:** Lowers downstream manual sorting efforts with an estimated prototype cost of ₹15,000–₹25,000.
