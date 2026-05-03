# 🖱️ Virtual Mouse

Control your computer's mouse using just your hand and a webcam. No physical mouse needed — just your hand in front of the camera.

Built with Python, OpenCV, and MediaPipe.

---

## 🤔 What does it do?

This project turns your webcam into a gesture-tracking system. It detects your hand in real time, reads your finger positions, and maps them to your screen — letting you move and control your mouse entirely through hand gestures.

No special hardware, no gloves, nothing fancy. Just a webcam and decent lighting.

---

## ✋ Gestures

The project uses your **index finger** and **middle finger** positions to detect gestures. Here's exactly what to do for each action:

---

### 🖱️ Move Cursor
**Raise your index finger** and keep your thumb close to the base of your index finger.  
Move your hand around — the cursor follows your index fingertip.

```
Index finger : UP 
Middle finger: UP
Thumb        : close to index base
```

---

### Left Click
**Curl your index finger** down while keeping your **middle finger raised**.

```
Index finger : CURLED 
Middle finger: UP 
Thumb        : away from index
```

---

### Right Click
**Curl your middle finger** down while keeping your **index finger raised**.

```
Index finger : UP ☝️
Middle finger: CURLED 🤜
Thumb        : away from index
```

---

### ✌️ Double Click
**Curl both your index and middle fingers** down at the same time.

```
Index finger : CURLED 🤜
Middle finger: CURLED 🤜
Thumb        : away from index
```

---

### 📸 Screenshot
**Curl both index and middle fingers** down AND **bring your thumb close** to your index finger (pinch).  
The screenshot is saved automatically in the project folder as `Screenshot_<number>.png`.

```
Index finger : CURLED 🤜
Middle finger: CURLED 🤜
Thumb        : PINCHED close to index 🤏
```

---


## 📁 Project Structure

```
virtual_mouse/
│
├── virtual_mouse.py   # Main file — run this
├── utils.py           # Helper math functions (angle, distance)
├── requirements.txt   # All dependencies
└── README.md
```

---

## ⚙️ How to run it

### 1. Clone the repo

```bash
git clone https://github.com/your-username/virtual-mouse.git
cd virtual-mouse
```

### 2. Create and activate a virtual environment

```bash
# Create
python3 -m venv venv

# Activate (macOS/Linux)
source venv/bin/activate

# Activate (Windows)
venv\Scripts\activate
```

### 3. Install the requirements

```bash
pip install -r requirements.txt
```

### 4. Run it

```bash
python virtual_mouse.py
```

Allow webcam access when prompted, show your hand to the camera, and you're good to go.

To quit, press **`q`**.

---

## 📦 Requirements

| Library | What it's used for |
|---|---|
| `opencv-python` | Capturing webcam feed and rendering the window |
| `mediapipe` | Detecting and tracking hand landmarks |
| `pynput` | Left and right mouse click control |
| `pyautogui` | Moving cursor, double click, and screenshots |
| `numpy` | Calculating angles and distances between landmarks |

---

## 🧠 How it works under the hood

MediaPipe detects **21 landmarks** on your hand every frame — your fingertips, knuckles, wrist, etc.

The code then:
1. Calculates the **angle** at each finger joint to determine if a finger is extended or curled
2. Calculates the **distance** between your thumb tip and index finger base to detect pinch
3. Combines these checks to identify which gesture you're making
4. Acts accordingly — moves the cursor, clicks, or takes a screenshot

All of this runs ~30 times per second, so it feels smooth and real time.
