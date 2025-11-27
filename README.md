# Scroll Doctor (Mouse Scroll Encoder Tester)

**Scroll Doctor** is a specialized, web-based diagnostic tool designed to detect and visualize “scroll jumping”—a common hardware failure in mouse scroll wheel encoders where the scroll signal erratically reverses direction.

## 🎯 Purpose
When a mouse scroll wheel encoder begins to fail (often due to dust, wear, or oxidation), it sends erratic signals. You might be scrolling down, but the page suddenly jumps up for a split second. This tool visualizes those raw signals to confirm if your hardware is at fault.

## ✨ Key Features
- **Real-Time Waveform Graph:** Visualizes every scroll event on a neon, synthwave-style timeline.
  - **Blue/Green Bars:** Represents consistent, clean scrolling.
  - **Red Bars:** Represents detected “glitches” (reverse signals).
- **Smart Trend Detection:** The algorithm locks onto your scrolling direction. If a signal opposes the established trend, it is flagged as a hardware fault.
- **Audio Feedback:**
  - **High Tick:** Clean scroll step.
  - **Low Buzz:** Glitch detected.
- **Stats Dashboard:** Tracks total scroll events, current direction, and a cumulative count of detected glitches.
- **Input Lock:** Disables the right-click context menu to allow uninterrupted testing.

## 🚀 How to Use
1. Open the application in a web browser.
2. **Scroll continuously** in one direction (e.g., maintain a steady downward scroll).
3. Watch the graph and the “Trend” indicator.
4. If you see **Red Bars** or hear the **Error Buzz**, the tool has detected a reverse signal sent by your mouse, indicating a faulty encoder.
5. Click **“RESET TEST”** to clear the data and test the opposite direction.

## 🛠 Technical Details
- **Single-File Architecture:** The entire application (HTML, CSS, JS) is contained within `index.html`.
- **Canvas API:** Uses HTML5 Canvas for high-performance, 60FPS rendering of the signal graph.
- **Web Audio API:** Generates real-time synthesized sound effects (oscillators) without external assets.
- **Event Handling:** Intercepts `wheel` events with `passive: false` to prevent default browser scrolling during the test.

## 🧠 Algorithm Logic
The **“Glitch Hunter”** algorithm works on a confidence system:

1. It monitors the direction of incoming scroll deltas.
2. After 2 consistent ticks in the same direction, it establishes a **Trend Lock**.
3. While locked, any input in the **opposite direction** is immediately flagged as a **Glitch**.
4. If the user stops scrolling for 500ms, the lock is released to allow for intentional direction changes.

*Built with vanilla JavaScript and HTML5 Canvas.*
