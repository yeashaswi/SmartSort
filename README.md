# SmartSort-
An AI-powered automated waste segregation system designed for homes and source-level sorting of mixed household waste.
# ♻️ SmartSort: AI-Powered Automated Waste Segregation

> **A Compact System Combining Controlled Feeding, Smart Sensing, Computer Vision, and Mechanical Diversion to Sort Mixed Household Waste**[cite: 9]

---

## 🌍 Overview

India generates approximately 62 million tonnes of municipal solid waste annually, with over 70% remaining mixed at source[cite: 9]. Manual sorting is time-consuming, hazardous, inconsistent, and unsuitable for continuous residential or small-scale automation[cite: 9]. 

**SmartSort** provides an automated solution by converting messy mixed waste into controlled, near-single-item inputs for inspection and automated 3-way segregation[cite: 9]. Designed for homes, campuses, apartment complexes, and small institutions, it bridges the gap between expensive industrial sorting infrastructure and unmanaged household waste[cite: 9].

---

## 🚀 Core Solution & Modular Pipeline

The system processes mixed waste streams through a strict 5-stage mechanical and digital workflow[cite: 9]:

1. **Controlled Input:** A 10-paddle Ferris-wheel feeder with 36° indexed movement prevents large piles from dumping into the system at once[cite: 9].
2. **Pre-processing:** A drainage deck removes free liquid, while a vibratory spreader de-clumps and singulates objects[cite: 9].
3. **AI Analysis:** A USB-C webcam captures individual items on the inspection platform, and a cloud Vision Language Model (VLM) via the Google GenAI Python SDK identifies the object and category[cite: 9].
4. **Decision:** The microcontroller tracks object position and selects the correct sorting path[cite: 9].
5. **Mechanical Sort:** Dual hinged inspection platforms and a motorized final sorting pipe redirect items into designated streams (Wet/Compostable, Dry/Recyclable, or Misc/Reject)[cite: 9].

---

## ⚙️ Hardware Components

| Component | Function / Role |
|------------|----------------|
| **Arduino Uno** | Controls the top Ferris-wheel feeding mechanism[cite: 9] |
| **ESP32** | Controls the inspection-platform flaps and final moving pipe[cite: 9] |
| **4 × MG996R Servos** | Actuators for the Ferris wheel (#1), platform sections (#2 & #3), and sorting pipe (#4)[cite: 9] |
| **USB-C Webcam** | Captures individual item images during inspection[cite: 9] |
| **IR Sensors (IR #1 & IR #2)** | Provide feedback loops to confirm item drops and movement events[cite: 9] |

---

## 💻 Software Stack

* **Python & OpenCV:** Handles webcam image capture and frame processing[cite: 9].
* **Google GenAI Python SDK:** Interfaces with the cloud VLM for object recognition and category classification[cite: 9].
* **Microcontroller Firmware:** Written for Arduino Uno and ESP32 to manage mechanical actuation sequences and sensor feedback[cite: 9].

---

## 🔄 Implementation Methodology & Control Flow

The system operates on a strict closed-loop sequence[cite: 9]:

1. Mixed waste enters the V-hopper[cite: 9].
2. Arduino rotates the Ferris wheel by 36°[cite: 9].
3. IR #1 confirms item drop onto the inspection platform[cite: 9].
4. OpenCV captures the webcam image and sends it to the cloud Gemini VLM[cite: 9].
5. VLM returns the object name and category (`WET` / `DRY`)[cite: 9].
6. Laptop transmits the category signal to the Arduino and ESP32[cite: 9].
7. ESP32 sets the sorting angle and opens the two platform sections (~80° inward)[cite: 9].
8. IR #2 confirms sorting/drop completion[cite: 9].
9. A ready signal returns to the Arduino to advance the next 36° feed cycle[cite: 9].

---

## 🧠 AI Decision & Fail-Safe Logic

* **Accepted Categories:** Sorted into Wet/Compostable or Dry/Recyclable streams based on VLM classification output[cite: 9].
* **Confidence Rule & Timeouts:** Planned rules target a >50% confidence threshold; a recognition timeout routes unrecognized or ambiguous items to the Misc/Reject path rather than forcing an incorrect classification[cite: 9].
* **Connectivity:** Current cloud-VLM integration requires internet connectivity, with future roadmap provisions for an edge/offline fallback model[cite: 9].

---

## 🛡️ Challenges & Mitigations

| Challenge | Mitigation Strategy |
|------------|---------------------|
| Irregular or sticky waste affecting single-item feeding | 10-paddle indexed feeding (36° steps) and controlled mechanical movement[cite: 9] |
| Cloud VLM internet dependency | Explicitly acknowledge current cloud limitation and plan future edge/offline model fallback[cite: 9] |
| Lighting and background variations | Stable inspection position and controlled camera setup with consistent capture conditions[cite: 9] |
| Recognition timeout / low confidence | Fallback routing to Misc/Reject if an item is not identified within the allowed window[cite: 9] |

---

## 📊 Impact and Benefits

* **Social & Operational:** Reduces direct manual contact with mixed waste and encourages better source-segregation practices[cite: 9].
* **Environmental:** Improves the separation of dry/recyclable materials, routes organic/wet waste toward composting, and minimizes forced misclassifications via the reject stream[cite: 9].
* **Economic:** Lowers downstream manual sorting efforts and provides an affordable architecture (estimated prototype cost: ₹15,000–₹25,000) suitable for small institutions and residential setups[cite: 9].

---

## 📚 Research References

1. Islam et al. (2025) — *ECCDN-Net: Efficient organic and recyclable waste classification*, Waste Management[cite: 9].
2. Kumar et al. (2026) — *Confidence-aware real-world waste classification*, Scientific Reports[cite: 9].
3. *Intelligent waste sorting for urban sustainability using deep learning*, Scientific Reports (2025)[cite: 9].
4. *Recyclable waste image recognition based on deep learning*, Resources, Conservation & Recycling (2021)[cite: 9].
