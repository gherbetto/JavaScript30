# Day 3 Update CSS Variables

For Day 3 (Update CSS Variables with JS), the core concept is learning how JavaScript can act as a bridge between user input and your stylesheet.

## 1. Identify the "Source of Truth"

Before writing logic, look at the HTML. You have input sliders and a color picker.

* **The Logic:** Notice the `name` attributes on those inputs. They match the CSS variable names defined in your `:root`.
* **The Goal:** You need a way to tell JS which CSS variable corresponds to which input.

## 2. Capture the Inputs

You need to grab all those controls from the DOM.

* **The Logic:** Use a selector that groups them all into one collection (a NodeList) so you can loop through them later rather than writing individual code for every single slider.

## 3. Listen for Interaction

The user needs to move a slider or pick a color for anything to happen.

* **The Logic:** You need to attach an event listener to each input.
* **Crucial Tip:** A `change` event only fires when the user lets go of the mouse. If you want the update to happen in real-time as they slide, you’ll need a second type of event listener.

## 4. Extract the Data

When an event fires, your function needs to figure out three things:

1. **Which** variable am I changing? (Hint: look at the `name` attribute of the element that triggered the event).
2. **What** is the new value?
3. **Does** it need a suffix? (e.g., `px` for spacing/blur, but nothing for color).

* *Tip:* Check the HTML `data-` attributes. They are perfect for storing units like "px".

### 5. Update the Style

Now you have the name, the value, and the suffix.

* **The Logic:** You need to apply these values to the **entire document**. In CSS, variables are usually stored in the `:root` (the `<html>` element).
* **The Action:** Find a method that allows you to set a property on the document's style based on the variable name you extracted.

---

### Summary Checklist

1. **Select** all input elements.
2. **Loop** through them to add listeners.
3. **Define** a function that handles the update.
4. **Extract** the name, value, and sizing unit (if applicable) inside that function.
5. **Set** the CSS variable on the document root using the data you collected.
