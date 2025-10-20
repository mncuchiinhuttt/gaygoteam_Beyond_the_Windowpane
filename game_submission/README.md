# Beyond the Window Frame

## Overview

Beyond the Window Frame is a single-page, browser-based narrative experience created for the RMIT Hackathon. The project explores the quiet struggles of Nguyen Tuan An, an 11th-grade student navigating academic pressure, self-worth, and the slow journey toward healing. The experience delivers a minimalist, atmospheric presentation with gentle motion, sparse UI, and a branching story that highlights how everyday choices ripple outward.

All application logic is implemented in plain HTML, CSS (via Tailwind utility classes), and vanilla JavaScript, with every screen delivered as static markup. External dependencies are loaded through CDNs so the project can run anywhere without a build step.

## Key Features

- **Atmospheric landing menu:** Glassmorphism card layout with subtle particles, guiding players toward Begin Journey, Understanding, and Credits views.
- **Interactive branching narrative:** Typing introduction flows directly into a multi-path story with three endings, all presented inside one file for seamless transitions.
- **Empathetic educational content:** Understanding page reframes An's symptoms through accessible cards to encourage mental health literacy.
- **Cinematic credits:** Staggered fade-ins acknowledge the team and institutional support while maintaining the overall mood.
- **Zero-install footprint:** Runs from a single `index.html` with preconfigured Tailwind v4 browser build, Google Fonts (Inter), and tsParticles from CDN.

## Experience Flow

1. **Menu (`game_app/index.html`):** Choose between starting the narrative, reading about mental health, or viewing credits.
2. **Begin Journey (`game_app/journey/begin.html`):** A typing introduction transitions into Chapter 1 with multiple decision points leading to Chapters 2 and 3 variants and three distinct endings.
3. **Understanding (`game_app/understanding.html`):** Responsive grid of symptom cards outlining An's emotional landscape.
4. **Credits (`game_app/credits.html`):** Cinematic recognition of the gaygoteam members and RMIT University.

## Tech Stack

- **Core:** HTML5, Tailwind CSS 4 (browser build), vanilla JavaScript.
- **Visuals:** Google Fonts (Inter), `assets/background.jpg`, tsParticles 3 for ambient dust.
- **Tooling:** Entire experience is static; no bundlers, frameworks, or build tools required.

## Getting Started

1. Clone or download the repository.
2. Open `game_submission/game_app/index.html` in any modern desktop or mobile browser.
3. Navigate using the on-screen buttons to explore each part of the project.

> Tip: Because all assets are local files, double-check that `assets/background.jpg` stays alongside the HTML when moving or hosting the project.

## Project Structure

```
game_submission/
├── README.md
├── game_app/
│   ├── index.html
│   ├── credits.html
│   ├── understanding.html
│   ├── assets/
│   │   └── background.jpg
│   └── journey/
│       ├── begin.html
│       └── chapter1.html (redirect helper)
├── prompts/
│   ├── asset_generation_prompts.txt
│   ├── code_generation_prompts.txt
│   ├── concept_prompts.txt
│   └── refinement_prompts.txt
├── screenshots/
│   ├── scr1.png
│   ├── scr2.png
│   ├── scr3.png
│   ├── scr4.png
│   └── scr5.png
├── youtube_link.txt
└── project_report.pdf
```

## Customization Notes

- **Styling:** Tailwind utility classes are defined in `<script>` config blocks in each page. Adjust colors, fonts, or animations there.
- **Particles:** tsParticles configuration lives at the bottom of each HTML file; tweak density, speed, or palette as needed.
- **Narrative:** All chapters and endings reside in `journey/begin.html`. Each choice button uses a `data-target` attribute that points to the next section. Update text or add new paths by duplicating the chapter blocks and wiring new IDs.
- **Accessibility:** Buttons include focus outlines and all narrative text maintains high contrast against the tinted background overlay.

## Team

- **gaygoteam**
  - Vo Minh Long
  - Le Dang Quynh Anh
  - Tran Minh Quan
  - Pham Gia Bao

## License

No explicit license has been provided. Please contact the team before reusing assets or narrative content.
