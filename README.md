# Mega CV - Gabriel Marín 🕹️

An interactive, retro-inspired 2D platformer game that doubles as a professional resume portfolio. Defeat the data challenges of the past and unlock Gabriel's engineering skill set!

---

## 🎯 Purpose & Why it was Created

This project was created to redefine the traditional resume. Rather than presenting a static PDF, **Mega CV** turns my career history into an engaging retro gameplay experience. 

Recruiters and hiring managers play as **M-Gabo**, picking any stage from a Mega Man-style stage-select menu and fighting through different eras of my career from 2013 to the present. Each stage features a unique boss and a themed background representing a real-world system or data challenge I've tackled over the years. Defeating a boss unlocks the specific technical skills and tools acquired during that role, leading to a final summary stage with direct links to my professional profile.

---

## 🛠️ Technology Stack

The project is built entirely with vanilla web technologies, optimized to run directly in any browser with **zero installation, zero dependencies, and lightning-fast loading speeds**:

1. **HTML5 Canvas API:** Used to render the entire game engine, including the player sprite, retro boss sprites, bullet physics, collision detection, screen-shaking, and particle effects.
2. **Vanilla JavaScript (ES6+):** Powers the core game loop (`requestAnimationFrame`), physics engine, player control input, and individual boss AI state machines.
3. **Vanilla CSS3:** Handles structural layout, centering, glassmorphic glows, retro CRT border styling, and responsive design adjustments.
4. **Mobile Virtual Gamepad:** Built-in touch-friendly D-pad and action buttons that automatically display on mobile devices.

---

## 🎮 Game Controls

### 💻 Desktop (Keyboard)
- **[A] / [D]** or **[◀] / [▶]**: Move Left / Right (in the Stage Select menu, cycles through stages)
- **[J]**: Jump
- **[W] / [SPACE]**: Shoot Buster (in the Stage Select menu, confirms selection)
- **[ENTER]**: Confirm / Next / Continue (after defeating a boss, returns to Stage Select)

### 📱 Mobile (Touch Screen)
- **◀ / ▶**: Move Left / Right (in the Stage Select menu, cycles through stages)
- **[J]**: Jump
- **[W]**: Shoot (in the Stage Select menu, confirms selection)
- **[NEXT]**: Confirm / Next / Continue (after defeating a boss, returns to Stage Select)

---

## 👾 Boss Guide & Inspirations

Each boss is a custom-coded pixel-art recreation inspired by Capcom's classic *Mega Man X* series, set against a background themed to that role (a telecom NOC room, a futuristic supermarket, a cloud data center, an abandoned factory, an MDM lab, and a hotel-tech lobby):

*   **Stage 1: Revenue Assurance** (Inspired by *Blizzard Buffalo - MMX3*)
    *   *Representing:* Fraud & anomaly-detection rules for Telco and Retail at WeDo Technologies (2013-2015).
    *   *Mechanics:* Foot stomping, charging, and shooting ice shards.
*   **Stage 2: Queued Orders** (Inspired by *Magma Dragoon - MMX4*)
    *   *Representing:* IBM Sterling OMS cloud migration and e-commerce performance testing at Liverpool/Walmart (2015-2019).
    *   *Mechanics:* Flaming Shoryuken jump punches and throwing fiery Hadouken fireballs.
*   **Stage 3: Invoice Backlog** (Inspired by *Storm Eagle - MMX*)
    *   *Representing:* OMS migration to GCP (Docker/K8s) and monitoring modernization at Nordstrom (2019-2020).
    *   *Mechanics:* Flapping wings to blow the player back and swooping down in a diagonal dive bomb.
*   **Stage 4: Legacy Data Ocean** (Inspired by *Vile - MMX*)
    *   *Representing:* Building a Snowflake data platform and enterprise governance at Philip Morris Mexico (2020-2025).
    *   *Mechanics:* Rapid shoulder plasma bursts and knee bombs that detonate into vertical fire pillars.
*   **Stage 5: Data Quality for Customer's MDM** (Inspired by *Sigma - MMX2*)
    *   *Representing:* Customer MDM governance and a custom Data Quality framework at Danone (2025-2026).
    *   *Mechanics:* Shooting floating electrical spheres and dashing across the screen with glowing energy claws.
*   **Stage 6: Schema Drift Sentinel** (an original design, drone/server-inspired)
    *   *Representing:* AI-accelerated data quality & governance at Coforge (client: Choice Hotels/SkyTouch), 2026-Current.
    *   *Mechanics:* Firing twin data-burst projectiles and charging across the screen when it detects "drift."

---

## 🚀 How to Run Locally

Since the game is completely self-contained in a single page, you can run it instantly:

1. Clone or download the repository.
2. Double-click the `index.html` file to open it directly in any modern web browser.

## ⚠️ Disclaimer 
This is a non-profit project developed exclusively for educational purposes and as a professional portfolio 💼 The mechanics and visual aesthetics are inspired by 16-bit platform games. No interactive elements, registered trademarks, code, or proprietary resources from Capcom Co., Ltd. are used. All rights to the original characters belong to their respective owners.
