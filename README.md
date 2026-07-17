# Handoff: PixelPrompt Studio — One-Page Website

## Overview
A dark, animated one-page marketing website for **pixelprompt.studio** — a web design, AI, software development and consultancy studio based in India. Sections: fixed nav, full-viewport hero with animated pixel-field background, scrolling services marquee, 4 service cards, 3-step process, contact block (WhatsApp / call / Instagram), footer.

## About the Design Files
The files in this bundle are **design references created in HTML** (a Design Component prototype). They show the intended look and behavior — they are NOT production code to copy directly. Recreate this design in your target codebase's environment (React, Next.js, Astro, plain HTML/CSS/JS, etc.) using its established patterns. If no environment exists yet, a static site (plain HTML + vanilla JS, or Astro) is the best fit — there is no backend or complex state.

## Fidelity
**High-fidelity (hifi).** Colors, typography, spacing, copy, and animations are final. Recreate pixel-perfectly.

## Design Tokens
### Colors
- Background: `#141416` (near-black)
- Text primary: `#f2f3f5`
- Text secondary: `#a7abb5`
- Text muted / mono labels: `#7c818c`
- Brand blue: `#0a6fd6` (primary CTA), hover `#1683ee`
- Brand cyan: `#3fc6ec` (links, accents)
- Brand orange: `#ff8a3d` (accents, link hover)
- WhatsApp green: `#128c4b`, hover `#16a457`; online dot `#4ade80`
- Borders: `rgba(255,255,255,.06–.1)`; card bg `rgba(255,255,255,.025)`
- Gradient text: `linear-gradient(90deg,#1683ee,#3fc6ec 55%,#ff8a3d)`

### Typography (Google Fonts)
- Headings/body: **Space Grotesk** 400/500/600/700
- Mono accents/labels: **JetBrains Mono** 400/500/700
- Hero H1: 76px / 700 / line-height 1.05 / letter-spacing -0.02em (44px on mobile ≤900px)
- Section H2: 46px / 700 / -0.02em
- Card H3: 26px / 600; process H3: 21px / 600
- Body: 15–19px, line-height 1.6–1.65
- Mono eyebrow labels: 12–13px, letter-spacing .28em, uppercase, prefixed `//`

### Spacing & Shape
- Max content width: 1160px; section padding: 120px top, 24px sides
- Card radius 16px, buttons 8–12px, contact panel 24px
- Grid gaps: 20px (cards), 56px (contact columns)

## Screens / Views (single page)

### 1. Fixed Nav
- `position:fixed`, full width, padding 18px 40px, `rgba(20,20,22,.72)` + `backdrop-filter:blur(14px)`, 1px bottom border rgba(255,255,255,.06)
- Left: logo mark (30px tall) + wordmark "pixelprompt**.studio**" (".studio" in cyan), 17px/700
- Right (hidden ≤900px): anchor links Services / Process / Contact (14px, #c8cbd2, white on hover) + blue CTA button "Let's talk →" linking to WhatsApp

### 2. Hero (min-height 100vh, centered text)
- Logo mark 180px wide, floating animation (translateY 0→-14px, 6s ease-in-out infinite), cyan drop-shadow glow
- Eyebrow: "WEB DESIGN · AI · SOFTWARE · CONSULTANCY" (mono, cyan)
- H1: "From pixel to prompt, we build what's **next**_" — "next" in gradient text, trailing "_" orange with blink animation (1.1s step-end)
- Paragraph (19px, #a7abb5, max 620px)
- Buttons: "Chat on WhatsApp" (blue, green dot, pulsing glow shadow) + "Instagram" (outlined, orange hover); both lift -2px on hover

### 3. Marquee strip
- Full-width, 1px top/bottom borders, mono 14px uppercase #7c818c
- Content duplicated 2× inside a flex row, `translateX(0 → -50%)` 26s linear infinite
- Text: "Web Design ■ AI Solutions ■ Software Development ■ Tech Consultancy ■ UI/UX ■ Automation ■" (■ alternate orange/blue/cyan)

### 4. Services (#services) — 2×2 grid (1 col mobile)
Each card: 36px padding, 3 pixel squares (12px, staggered opacity-pulse 2.4s), mono number, title, description. Hover: cyan border, faint cyan bg, translateY(-4px).
1. **01 Web Design** — "Pixel-perfect, blazing-fast websites that convert. From landing pages to full brand experiences — designed to look stunning on every screen."
2. **02 AI Solutions** — "Chatbots, automation, and AI-powered products built on modern LLMs. We turn prompts into production — practical AI that saves real hours."
3. **03 Software Development** — "Web apps, dashboards, APIs and integrations — clean architecture, modern stacks, and code your future team will thank you for."
4. **04 Consultancy** — "Not sure what to build, or how? We audit, plan and de-risk your tech decisions so every rupee of your budget works harder."

### 5. Process (#process) — 3 columns (1 col mobile), centered header "Simple, sharp, shipped."
Cards with 52px gradient mono number:
1. **Discover** — "A quick call or WhatsApp chat to understand your goals, users and constraints. No jargon, no 40-page briefs."
2. **Design & Build** — "Rapid iterations you can see and react to. You watch the product take shape instead of waiting for a big reveal."
3. **Ship & Support** — "We launch, measure and stay close. Tweaks, training and support so the product keeps earning after day one."

### 6. Contact (#contact)
- Panel: 2 columns (1.2fr/1fr), 64px/56px padding, radius 24px, bg `linear-gradient(135deg,rgba(10,111,214,.12),rgba(255,138,61,.06))`
- Left: eyebrow "// Start a project", H2 "Have an idea? Let's make it real.", supporting copy
- Right, stacked full-width row buttons (label left, mono detail right):
  - **WhatsApp us** → https://wa.me/919460074404 (green bg) — "+91 94600 74404"
  - **Call us** → tel:+919460074404 (outlined, cyan hover)
  - **Follow the work** → https://www.instagram.com/pixelprompt.studio/ (outlined, orange hover) — "@pixelprompt.studio"

### 7. Footer
Logo (22px, 80% opacity) + "© 2026 PixelPrompt Studio" left; mono tagline "pixelprompt.studio — design · code · intelligence" right.

## Interactions & Behavior
- **Pixel-field background**: fixed full-viewport `<canvas>` behind all content (z-index 0, pointer-events none). ~55 squares (3–12px), brand colors, drifting slowly upward, each with sine-wave opacity pulse (alpha 0.06–0.26), slight scroll parallax (offset by scrollY × 0.06 × size factor), wrap around vertically, respawn at bottom. requestAnimationFrame loop; rebuild on resize.
- **Scroll reveals**: elements start opacity 0 / translateY(28px), transition .7s ease. Reveal via IntersectionObserver (threshold 0.12) PLUS a scroll-listener fallback (reveal when rect.top < 1.05×viewport) PLUS a 2.5s safety timeout that reveals everything — content must never stay invisible.
- Smooth scrolling for anchor nav (`scroll-behavior:smooth`).
- All hover states listed above; external links open in new tab with rel="noopener".
- Responsive ≤900px: nav links hidden, H1 44px, all grids collapse to 1 column.

## State Management
None required — fully static. Only runtime state is the canvas particle array and reveal flags.

## Assets
- `assets/logo-mark.png` — white PixelPrompt "P + chevron" pixel mark on transparent background (932×672). Derived from client-supplied logo. Original color/branded variants are in the client's possession (blue/orange gradient versions exist).
- Fonts loaded from Google Fonts CDN.

## Contact Data (canonical)
- WhatsApp & phone: **+91 9460074404** → wa.me/919460074404, tel:+919460074404
- Instagram: https://www.instagram.com/pixelprompt.studio/
- Only social link on the site is Instagram (per client requirement).

## Files
- `index.html` — **standalone, deployable website** (plain HTML/CSS/JS, all animations self-contained). Open directly in a browser or host as-is; needs `assets/logo-mark.png` beside it.
- `PixelPrompt Studio.dc.html` — the full design prototype (template markup + logic). Inline styles throughout; @keyframes and body resets in the head style block.
- `assets/logo-mark.png` — logo asset.
