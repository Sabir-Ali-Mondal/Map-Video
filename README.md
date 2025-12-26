# 🌍  Map Video

**A browser-based tool for creating cinematic, narrated map journeys using AI and Leaflet.js.**

## 🎯 Goal

The goal of this project is to democratize high-end map animations. Usually, creating "Vox-style" or "Johnny Harris-style" map videos requires expensive software like After Effects and hours of manual keyframing. 

**Map Video Studio AI** solves this by:
1.  **Automating Movement:** Using code to handle pans, zooms, and flyovers.
2.  **Leveraging AI:** Using ChatGPT or Perplexity to generate complex coordinate data (country borders, historic routes) instantly.
3.  **Built-in Narration:** utilizing the browser's native Text-to-Speech (TTS) engine for immediate voiceovers in any language.

It is designed for educators, content creators, and history enthusiasts who want to tell spatial stories without editing video.

---

## 🚀 How to Run

This application is **single-file** and **client-side**. It requires no server installation, no Node.js, and no Python.

### Prerequisites
*   A modern web browser (Chrome, Edge, or Safari recommended for best TTS voices).
*   An active internet connection (to load Map Tiles and CSS libraries via CDN).

### Steps
1.  **Download:** Create a new file on your computer named `index.html`.
2.  **Paste:** Paste the full source code provided into that file.
3.  **Open:** Double-click `index.html` to open it in your web browser.
4.  **Enjoy:** The application will load immediately.

---

## ⚙️ How It Works

The application operates on a **JSON-driven engine**. The entire video (camera moves, visuals, narration) is defined by a single JSON object.

### The Workflow

1.  **Configuration (The Editor):**
    *   You open the **"Create"** modal.
    *   Select a **Topic** (e.g., "The Roman Empire"), a **Map Style** (Satellite, Dark, etc.), and a **Narrator Voice**.
    *   The tool generates a specialized **Prompt**.

2.  **AI Generation:**
    *   You click "Ask ChatGPT" or "Ask Perplexity".
    *   You paste the prompt. The AI acts as a GIS expert and returns a block of JSON code containing coordinates for polygons, markers, and the script text.

3.  **Rendering (The Engine):**
    *   You paste the JSON back into the tool.
    *   **Parsing:** The tool strips Markdown formatting and identifies the language/voice required.
    *   **Visuals:** It uses **Leaflet.js** to render coordinates. It supports:
        *   `Polygon`: Complex shapes (countries, lakes).
        *   `Line`: Routes or borders.
        *   `Marker`: Professional SVG pins.
        *   `Label`: Cinematic text overlays.
    *   **Audio:** It uses the **Web Speech API** (`window.speechSynthesis`) to speak the text in real-time, synchronized with the map movement.

### The JSON Structure
The core logic relies on this structure:
```json
{
  "title": "My Story",
  "style": "satellite",
  "voice": { "lang": "en-US", "name": "Google US English" },
  "timeline": [
    {
      "type": "pan",
      "location": [latitude, longitude],
      "visual": { "color": "#ff0000" },
      "narration": { "text": "This is where it started..." }
    }
  ]
}
```

---

## ✨ Key Features

*   **4 Map Themes:** Satellite, Dark Matter, Voyager (Clean), and Light Mode.
*   **Smart Voice Selection:**
    *   Automatically detects available browser voices.
    *   Groups voices by language.
    *   **Auto-Lock:** If you load a script made for a Hindi voice, the player automatically switches your TTS engine to Hindi.
*   **Advanced Visuals:**
    *   Supports complex **Polygons** (for highlighting entire countries).
    *   Animated **Pulse Markers** and **Dashed Lines**.
    *   **Auto-Centering:** The camera automatically calculates the best zoom level to fit a shape or route on the screen.
*   **No Alerts:** Uses a sleek "Toast" notification system for a professional UI feel.
*   **Editor Tools:** One-click copy for prompts and one-click paste for JSON code.

---

## 🛠 Tech Stack

*   **HTML5 / CSS3:** Custom "Glassmorphism" UI design.
*   **JavaScript (ES6):** Logic for the state machine, map rendering, and audio synchronization.
*   **Leaflet.js:** Open-source library for interactive maps.
*   **Bootstrap 5:** Modal and layout structure.
*   **Web Speech API:** Native browser text-to-speech.

---

## 📝 Tips for Best Results

1.  **Use Chrome or Edge:** These browsers usually provide high-quality "Google" or "Microsoft" online natural voices.
2.  **AI Prompting:** If the AI gives you a simple square for a country, ask it to "Provide more coordinate points for a detailed border."
3.  **Fullscreen:** Press the Fullscreen icon for an immersive experience before playing the script.
