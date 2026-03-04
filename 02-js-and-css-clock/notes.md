# 🕒 Day 2: JS + CSS Clock Logic Roadmap

## 1. The Selector Phase

* **Goal:** Grab the three clock hand elements from the DOM (`hour-hand`, `min-hand`, `second-hand`).
* **Why:** You need to apply a CSS `transform` to each of these individually based on the time.

## 2. The Timing Loop

* **Goal:** Create a function (e.g., `setDate`) that runs **every second**.
* **Method:** Use `setInterval(functionName, 1000)`.
* **Why:** If the function only runs once, your clock will stay frozen at the time the page loaded.

## 3. The Data Extraction

* **Goal:** Inside your function, get the current time.
* **Method:** Create a `new Date()` object and use its methods to pull the current seconds, minutes, and hours.

## 4. The Math (The "Aha!" Moment)

* **Goal:** Turn "Seconds" (0-60) into "Degrees" (0-360).
* **The Formula:** $((seconds / 60) * 360) + 90$.
* **Why the +90?** By default, CSS pivots are horizontal. Since clock hands start pointing straight up (12 o'clock), you need to offset the initial 90 degrees you likely applied in your CSS.
* **Repeat:** Do the same logic for Minutes ($/60$) and Hours ($/12$).

## 5. The Application

* **Goal:** Update the rotation of each hand.
* **Method:** Use `.style.transform = `rotate(${degrees}deg)``.
* **Check:** Ensure your CSS has `transform-origin: 100%` (or `right`) so the hands rotate from the center of the clock rather than their own middle.

---

When the seconds hand hits **0**, it might do a weird "glitchy" 360-degree backwards spin.

* **The Logic:** This happens because the degrees reset from 444° back to 90°.
* **The Fix:** (Advanced) You can either temporarily disable the `transition` in JS when seconds are 0, or just keep a running total of degrees so it never resets!
