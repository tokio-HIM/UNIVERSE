# UNIVERSE - Agent Instructions

## Role

You are the primary software engineer for the UNIVERSE mobile application.

Read README.md before making implementation decisions.

The product owner will provide the product requirements and approve changes to the core game design.

---

## Current Priority

The current milestone is:

MILESTONE 1 — Playable Focus Loop

Implement only:

Home
→ Focus Setup
→ Focus Timer
→ Mission Complete
→ Home

Do not implement future roadmap features unless explicitly requested.

---

## Technical Requirements

Use:

- React Native
- Expo
- TypeScript
- Expo Router
- AsyncStorage

Prioritize cross-platform compatibility.

---

## Implementation Rules

1. Inspect the existing project before modifying files.

2. Do not create unnecessary files.

3. Do not add dependencies unless necessary.

4. If a dependency is required, explain its purpose before installing it.

5. Use TypeScript.

6. Avoid `any` unless unavoidable.

7. Keep business logic separate from UI components where practical.

8. Keep the timer logic independent from UI rendering.

9. The timer must use timestamps as its source of truth.

10. The timer must continue correctly when the app is backgrounded.

11. Rewards must be granted exactly once per completed session.

12. Persist important state using AsyncStorage.

13. The only backend is Supabase, used for Planet Arrival / Flags (approved). Do not add other online features without approval.

14. Use Supabase anonymous sign-in only. Do not add account login (email, social) yet.

15. Do not implement Screen Time APIs yet.

16. Do not implement AI yet.

17. Do not implement payments yet.

18. Do not implement multiplayer yet (friends, chat, PvP, rankings). Viewing other players' flags is allowed.

---

## Before Finishing a Task

After implementation:

1. Run TypeScript checks.
2. Run the application.
3. Check for runtime errors.
4. Verify the relevant screen manually if possible.
5. Fix errors.
6. Summarize what changed.

Do not claim that a feature works if it has not been tested.

---

## Product Constraints

The core loop is:

Focus
→ Flight (current location → next destination)
→ Arrival
→ Flag
→ Next destination
→ Focus

Route: Earth → Moon → Mars → Jupiter → Saturn → Deep Space → Unknown Civilization (the end).
Resources, planet levels, development, buildings and completion are removed. Do not reintroduce them.

Distance and speed (single source of truth: `ROUTES` in `src/game/flight.ts`):

- Every route keeps its real distance. Do not change these distances.
- Every route has its own fixed speed, derived from its distance and the focus hours allotted to it:
  km per focus minute = distance / (focus hours × 60). Later routes are faster.
- Earth → Unknown Civilization takes 1,000 focus hours in total (2,400 focuses of 25 minutes).
- The speed of a focus is fixed when it starts (its route is fixed for the session) and never changes
  with time inside a focus. It only changes when the route changes after an arrival.
- A destination is reached once the focus time spent on its route reaches the route's allotted time
  (distance travelled = route distance). Progress on a route is stored as focus minutes
  (`progress.legFocusMinutes`) and carries over between focuses.

| Route | Distance | Focus hours | km / focus minute |
|---|---|---|---|
| Earth → Moon | 384,400 km | 6 | ≈ 1,067.8 |
| Moon → Mars | 78,340,000 km | 40 | ≈ 32,641.7 |
| Mars → Jupiter | 550,630,000 km | 110 | ≈ 83,428.8 |
| Jupiter → Saturn | 654,960,000 km | 70 | ≈ 155,942.9 |
| Saturn → Deep Space | 16,518,000,000 km | 274 | ≈ 1,004,744.5 |
| Deep Space → Unknown Civilization | 40,160,000,000,000 km | 500 | ≈ 1,338,666,666.7 |

The ship's position always follows effective focus time → progress → distance → position; animations
never decide it. Focus Flight and the Universe Map read the same focus session.

Do not change these values or rules without explicit approval.

---

## UI Direction

UNIVERSE should feel like a futuristic space game.

Prioritize:

- Dark space environment
- Clean typography
- Strong visual hierarchy
- Subtle animation
- Mobile-first layouts
- Large touch targets

Avoid:

- Generic productivity-dashboard UI
- Excessive cards
- Excessive neon
- Excessive animation
- Desktop-first layouts

---

## Communication

When requirements are ambiguous:

Do not silently invent major product behavior.

For small implementation details, choose the simplest reasonable solution.

For major product decisions, ask before implementing.

When reporting progress, include:

- Files changed
- Features implemented
- Tests/checks performed
- Remaining issues
