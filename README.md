
# Grind Converter

A lightweight, browser-based utility for specialty coffee enthusiasts to translate grind settings between different high-end grinders. By focusing on **vertical burr travel (microns)**, this tool provides a mechanical baseline for "dialing in" recipes across different hardware platforms.

## Features

-   **Cross-Platform Translation:** Move between industry leaders like Comandante, 1Zpresso, Lagom, and Turin.
    
-   **Raw Micron Input:** Use the "Gap (μm)" mode to find the exact dial setting for a specific theoretical particle size.
    
-   **Zero-Latency Logic:** Instant calculations using pure JavaScript.
    
-   **Persistence:** Your "To Grinder" preference and last-used settings are saved to your browser's local storage automatically.
    
-   **Mobile Friendly:** Clean, responsive UI designed for use next to your brew station.
    

## How to Use

1.  **Select your source:** Choose the grinder you are coming from (or select "Gap (μm)").
    
2.  **Enter the value:** Type in the clicks, dial number, or micron value.
    
3.  **Select your target:** Choose the grinder you want to set.
    
4.  **View Result:** The large accent-colored number is your target setting. The sub-text shows the total physical gap in microns.
    

----------

## The Prompt Section (How to Extend)

One of the core strengths of this project is its modular configuration. You can easily add more grinders (like the Fellow Ode, Mazzer, or other 1Zpresso models) by using the following AI prompt.

### How to use the prompt:

1.  **Identify your data:** Look up the "microns per click" or "thread pitch" for the grinder you want to add (often found on the manufacturer's website or enthusiast forums).
    
2.  **Copy the prompt below:** Replace the bracketed information with your grinder's specific data.
    
3.  **Paste into Gemini:** Use the code output provided by the AI to replace the `const configs` section in your `index.html`.
    

### The Extension Prompt

> "I am using a custom Coffee Grinder Converter web app. I need to add a new grinder to the `configs` object in the JavaScript.
> 
> **Grinder Name:** [Insert Name, e.g., Fellow Ode Gen 2] **Microns per Step:** [Insert Value, e.g., 12.5] **Decimal Places:** [Insert 0 for clicks, or 1 for dials]
> 
> Please provide the updated `const configs` code block and the new `<option>` HTML tag to be added to both the 'From' and 'To' dropdown menus. Ensure the logic maintains the vertical burr travel calculation used in the current app."

----------

## Technical Details

The converter operates on a **Micron-to-Unit** ratio.

-   **Clicks:** Usually represented as whole integers (Decimal: 0).
    
-   **Dials:** Usually represented as floats (Decimal: 1).
    
-   **Internal Reference:** The app uses a linear mapping where Setting×MicronsPerClick=TotalGap.
    

> [!TIP] **Note on the ZP6:** The ZP6 configuration includes a "Clarity Offset." Because it produces so few fines, the app maps its 4.5 setting to the 600μm reference point, whereas a C40 maps 20 clicks to the same point. This ensures the brew _time_ remains consistent between grinders.

