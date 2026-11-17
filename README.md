# Verdelo — Household Finance Dashboard

[![Live Demo](https://img.shields.io/badge/Live%20Demo-GitHub%20Pages-blue?style=for-the-badge&logo=github)](https://mrchandrayee.github.io/verdelo-household-finance/)
[![HTML](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)](https://developer.mozilla.org) [![CSS](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)](https://developer.mozilla.org) [![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)](https://developer.mozilla.org)
[![License: MIT](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](./LICENSE)

Runnable, responsive HTML/CSS/JavaScript reconstruction of the uploaded **5.07-second** video (720 × 1280, 30 fps).

## Run
1. Extract `verdelo-household-finance.zip`.
2. Open `index.html` in a modern browser.
3. No npm install, build tools, API keys or backend required.

Optional local server:
```bash
python3 -m http.server 8000
```
Open `http://localhost:8000`.

## What is visible in the source video

The application is branded **Verdelo** and the household/account label reads **Oliver-Lindqvist home**. The main account user shown is **Ines Okafor**. The UI uses a dark forest-green palette, mint highlights, rounded financial cards, a left navigation rail and a compact top search/action bar.

### Overview
- Greeting: “Good morning, Ines”
- Reminder: “Ines is paid in 3 days. Four bills go out before then”
- Cards stack with Everyday debit card, card carousel controls and Freeze action
- Joint balance for Everyday account ending 0457
- Balance chart with Balance, Forecast, Payday and Bill markers
- Money in & out chart with Quarter / 6 months / Year controls
- Safe to spend today: $67
- Recent activity and upcoming bills

The visible balance is dynamic in the recording; an early frame shows **$23,223.28**.

### Cards
The recording navigates to **Cards**. It shows three cards on one account and a November spend summary. The selected Everyday card detail panel shows:
- Spent in November: $1,393.11
- Left this month: $1,806.89
- Freeze card
- Online payments
- Payments abroad
- Contactless
- Monthly limit: $3,200
- Hold to see PIN

### Insights
The recording opens **Insights**, with tabs **In & out**, **Spending**, and **Merchants**.

The Spending tab shows category bars such as Home, Groceries, Shopping, Eating out, Utilities, Kids, Health, Transport and Subscriptions, alongside:
- Needs and wants (85% needs)
- Who spent it (Ines, Jonas, Ada)
- Spending by day

### Other navigation items visible
- Payments
- Budgets
- Goals
- Household
- Settings
- Help

The video shows the Overview, Cards and Insights pages in motion. Additional navigation pages are included as reasonable frontend reconstructions based on their visible labels, not as fully observed source screens.

## Readable code fragment visible in the video

The bottom code preview is legible enough to transcribe a TypeScript function named `slidePill`. It calculates a pill's clipping rectangle relative to a target element, determines the leading/trailing edge based on direction, then animates the clipping geometry with GSAP.

```ts
export function slidePill(pill: HTMLElement, target: HTMLElement) {
  const box = pill.parentElement!;
  const to = {
    l: target.offsetLeft, t: target.offsetTop,
    r: box.offsetWidth - (target.offsetLeft + target.offsetWidth),
    b: box.offsetHeight - (target.offsetTop + target.offsetHeight),
  };
  const clip = (e: Edges) =>
    `inset(${e.t}px ${e.r}px ${e.b}px ${e.l}px round 14px)`;
  const st = host.__st, fwd = to.t > st.t || to.l > st.l;
  // The leading edge goes first, the trailing edge catches up
  const [lead, trail] = fwd ? ['b', 't'] : ['t', 'b'];
  const paint = () => gsap.set(pill, { clipPath: clip(st) });
  gsap.to(st, { [lead]: to[lead], duration: 0.36, onUpdate: paint });
  gsap.to(st, { [trail]: to[trail], duration: 0.55, onUpdate: paint });
}
```

The video does not expose the original `Edges` type, `host` declaration, imports or complete app source. The function above is transcribed from the readable on-screen fragment; the runnable project below is a standalone reconstruction and uses CSS transitions rather than requiring GSAP.

## Implemented interactions
- Navigate Overview, Cards, Payments, Insights, Budgets, Goals, Household, Settings and Help.
- Overview card carousel and flip-to-back effect.
- Freeze / unfreeze card control.
- Show / hide joint balance.
- Send money form and local demo ledger update.
- Download a CSV statement.
- Cards page switches, card freeze toggles, virtual card creation demo, monthly limit slider and hold-to-see-PIN interaction.
- Insights tabs: In & out, Spending and Merchants.
- Create budget and savings goal demo.
- Household invitation demo.
- Search payments and open quick actions.
- Dark / light theme toggle.
- Responsive layout.

## Files
- `index.html` — all views and markup.
- `styles.css` — Verdelo visual system, card stack, charts, page layouts and responsive behavior.
- `app.js` — navigation, demo account data, forms, chart drawing and interactions.
- `README.md` — run instructions and video-derived observations.

## Accuracy and limitations
The screen recording is a UI demonstration, not a full source repository. Only the `slidePill` TypeScript fragment at the bottom is readable enough to transcribe; it is preserved above in the README. The rest of the app is reconstructed from visible screens, labels, values and interactions. Amounts and activity are illustrative frontend demo data. There is no real bank connection, payment processing, authentication, account ledger, card issuer integration or persistence. Sending money, adding payments, budgets, goals, invites and virtual card actions are simulations only.

## 👨‍💻 Author

**mrchandrayee** · [GitHub](https://github.com/mrchandrayee)

## 📄 License

[MIT License](./LICENSE)
