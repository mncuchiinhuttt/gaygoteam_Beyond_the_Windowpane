# Beyond the Window Frame – Project Report

## 1. Introduction
Beyond the Window Frame is a narrative-driven, single-page web experience designed during the RMIT Hackathon 2025. The project responds to the event’s challenge of using technology to spotlight social issues while remaining accessible to broad audiences. Our team chose to focus on youth mental health, building an introspective story around Nguyen Tuan An, an 11th-grade student coping with expectations, isolation, and the path to healing. The report captures the intent, design reasoning, technical execution, and lessons learned while creating the interactive prototype.

Mental well-being remains a pressing concern for high-school students across Vietnam and beyond. Academic competition, family expectations, and the stigma surrounding mental illness routinely silence those who need help. By simulating An’s journey through a branching narrative, the experience aims to foster empathy, illustrate how seemingly small interactions can escalate or relieve distress, and encourage conversations about support systems.

## 2. Game Overview
Beyond the Window Frame blends visual novel storytelling with educational content. Users begin at an atmospheric landing page that invites them to “Begin Journey,” explore an “Understanding” compendium of symptoms, or read the “Credits.” Selecting the journey launches a gradual typing introduction that segues into a branching story. Choices direct players through Chapters 2A, 2B, or 2C and, eventually, to three alternative Chapter 3 scenarios and endings. Each outcome—Sunlight on the Sill, The Unending Grey, and The Shattered Glass—mirrors real-world trajectories shaped by support, silence, or systemic failure.

In parallel, the Understanding page reframes the narrative as a set of thematic cards describing An’s symptoms—anhedonia, fatigue, social withdrawal, cognitive fog, and more. The page serves as a micro-resource, translating in-game depictions into concise explanations for players unfamiliar with mental health terminology. The combined experience balances storytelling with educational grounding, ensuring visitors leave with both emotional and informational insights.

## 3. Game Mechanics and Design
### Branching Narrative Structure
The narrative is organized into a simple state-machine style structure. Chapter 1 establishes the conflict and culminates in Choice Point 1. Each decision reveals a unique Chapter 2 branch (The Grind, The Ripple, The Bubble), each containing the next choice set tailored to An’s emotional state. Chapter 3 variants deliver narrative consequences and direct the user to an appropriate ending. Buttons with `data-target` attributes trigger transitions between chapter sections, allowing seamless navigation without reloading the page.

### Interaction and Feedback
All decisions employ minimalist pill-shaped buttons with hover and focus states derived from Tailwind utility classes. On selection, the currently visible chapter fades out before the next one fades in, maintaining the meditative pacing. The endings provide explicit labels (e.g., “Continue to Ending 2”) so players understand narrative causality. Restart buttons send users back to Chapter 1, encouraging exploration of alternative routes.

### Visual Tone and Accessibility
The interface leans on glassmorphism panels, muted lavender accents, and large negative space to evoke quiet introspection. Particles floating over a desaturated photographic background (a windowpane at dusk) reinforce the theme of fog and distance. Text is set in Inter, with narrative passages in `text-white/70` to soften contrast while still meeting accessibility concerns for medium-dark backgrounds. Focus rings and sufficient color contrast ensure keyboard navigability and readability.

## 4. Technical Implementation
### Front-End Stack
The experience is built entirely in static HTML files located under `game_submission/game_app/`. Tailwind CSS 4’s experimental browser build hydrates utility classes on the fly via CDN, removing the need for a compilation step. JavaScript is handcrafted and embedded in `<script>` tags within each page.

Key files include:
- `index.html`: Landing menu with navigation cards.
- `journey/begin.html`: Combined introduction, all chapters, endings, and transition logic.
- `understanding.html`: Symptom cards in a responsive grid.
- `credits.html`: Credits with staggered fade-ins.
- `journey/chapter1.html`: Lightweight redirect to maintain back-compatibility with earlier prototypes.

### Animation and State Management
The typing effect in the introduction uses a recursive `setTimeout` loop that modulates speed based on punctuation. Chapter transitions rely on CSS classes (`hidden`, `opacity-0`) toggled inside event listeners. Each button reads its `data-target` value to locate the next chapter div, supporting easy expansion by adding new IDs. The `scrollIntoView` call ensures long chapters remain centered on screen even after multiple transitions.

### Ambient Visuals
Ambient motion comes from tsParticles v3, which renders a slow-moving dust effect. Configuration is scoped per page to maintain consistent particle density, color palette, and movement speed. The particles layer sits between the background image and the semi-opaque overlay, giving depth without overwhelming text legibility.

### Deployment Considerations
Because all dependencies are loaded from CDNs, the application can run locally or on static hosts (e.g., GitHub Pages, Netlify) without additional tooling. The only asset requirement is that `assets/background.jpg` remains in the relative path expected by the HTML documents. The design is responsive across desktop and modern mobile browsers.

## 5. AI Integration and Development Process
AI tools played a central role in accelerating ideation and implementation:
- **Prompt-driven workflow:** The `/prompts` directory captures iterative instructions used to generate UI concepts, narrative refinements, and asset suggestions. These prompts guided Copilot and other AI assists while ensuring the final output aligned with the artistic direction.
- **Pair-programming with Copilot:** GitHub Copilot generated Tailwind configurations, refined HTML structures, and produced initial JavaScript scaffolding. Human review ensured semantic structure, accessibility, and emotional tone matched the project’s goals.
- **Narrative iteration:** AI models helped outline branching outcomes and adjust tone, after which the writing team edited for cohesion and cultural authenticity. The branching logic remained human-curated to preserve intentional emotional beats.
- **Quality control:** Automated suggestions were continuously audited against design guidelines, leading to manual adjustments (e.g., color contrast tweaks, replacement of smart quotes with ASCII) to maintain consistency.

The hybrid workflow balanced AI efficiency with human oversight, allowing the team to deliver a polished prototype within hackathon constraints while retaining narrative nuance.

## 6. Impact and Relevance
Beyond the Window Frame aims to normalize conversations about mental health in high-pressure academic settings. By letting players inhabit An’s internal monologue, the experience illustrates how parental expectations, social isolation, and inadequate institutional support compound distress. The branching endings underscore that empathy and accessible resources can redirect trajectories—from perpetual grey to glimpses of sunlight.

In educational contexts, the Understanding page functions as a discussion aid. Teachers or counselors can use it to introduce symptoms of depression and anxiety, prompting students to share experiences or identify support structures. The project also demonstrates how low-barrier web technologies can deliver emotionally resonant storytelling without advanced hardware, making it suitable for school computer labs or mobile devices.

## 7. Reflection and Future Work
### What Worked
- A unified `begin.html` file simplified navigation and avoided page reloads, keeping players immersed.
- The art direction successfully communicated mood with minimal assets, relying on typography, color, and motion rather than heavy graphics.
- Branching choices meaningfully altered outcomes, encouraging replay and discussion about mental health coping strategies.

### Challenges
- Crafting culturally sensitive narrative content required multiple review cycles; AI drafts occasionally leaned on generic tropes that needed rework.
- Tailwind’s experimental browser build limited advanced theming options; some utility classes required manual fallbacks.
- Without a persistent save system, users must manually explore alternate paths, which is acceptable for a short experience but could be enhanced.

### Future Enhancements
1. **Audio design:** Introduce ambient soundscapes or subtle musical cues that shift with An’s emotional state.
2. **Analytics & reflection prompts:** Allow educators to capture anonymous feedback or encourage players to journal after each ending.
3. **Localization:** Provide Vietnamese and English text toggles to broaden reach.
4. **Resource hub integration:** Link to hotlines or counseling services for players seeking help beyond the story.
5. **Expanded branching:** Add Chapter 4 epilogues that explore recovery journeys or systemic reforms to reinforce hopeful narratives.

## 8. References
- World Health Organization. (2021). *World mental health report: Transforming mental health for all*. https://www.who.int/publications/i/item/9789240053860
- UNICEF East Asia & Pacific. (2021). *Situation analysis of children’s mental health in Viet Nam*. https://www.unicef.org/eap/reports/si-mental-health-viet-nam
- Vietnam Ministry of Education and Training. (2022). *Summary of student mental health initiatives*. (Internal policy brief).
- National Academies of Sciences, Engineering, and Medicine. (2021). *Supporting students’ college success: The role of assessment of intrapersonal and interpersonal competencies*. Washington, DC: The National Academies Press.
