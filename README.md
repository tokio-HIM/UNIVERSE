# UNIVERSE

## 1. Product Overview

UNIVERSE is a mobile game that turns time spent away from the smartphone into progress through space.

Core concept:

> Focus in the real world → Rocket travels → Resources are earned → Civilization develops → New planets are unlocked.

The purpose of the product is not simply to provide a focus timer.

The goal is to make users feel:

> "I spent 50 minutes focusing, and my universe actually developed."

UNIVERSE combines:

- Focus / Pomodoro timer
- Space exploration
- Civilization building
- Personal progression
- Competitive rankings

The game should work for both competitive users and users who simply enjoy developing their own universe.

---

# 2. Product Principles

These principles must be respected throughout development.

### 2.1 Real-world focus is the core input

The primary game resource is the user's actual focus time.

Focus time should never feel secondary to game mechanics.

The main loop is:

Focus
↓
Distance + Resources
↓
Explore / Build / Research
↓
Civilization progression
↓
Planet unlock
↓
New planet

---

### 2.2 The app should encourage putting the phone down

The user should NOT need to stare at the app while focusing.

The Focus screen must be minimal.

Once a session starts, the user should be able to:

1. Start the session
2. Lock the phone / leave the app
3. Return later
4. See the completed mission

Do not create unnecessary interactions during a Focus session.

---

### 2.3 Game progression must not be pay-to-win

Competitive rankings should primarily reflect actual Focus Time.

Paid features may provide:

- Cosmetic customization
- Additional statistics
- Convenience
- Optional AI coaching

Paid users should not be able to directly purchase competitive power.

---

### 2.4 Keep the MVP simple

Do NOT implement the following in the initial MVP:

- Real Screen Time API integration
- Social login
- Friends
- Chat
- Push notifications
- AI coach
- Payments
- Ads
- Complex multiplayer
- Complex 3D graphics
- Multiple planets beyond Moon
- Complex resource economy
- Backend authentication

These may be implemented later.

The MVP must first prove that the core game loop is fun.

---

# 3. Target Platform

The application is a smartphone application.

Initial development stack:

- React Native
- Expo
- TypeScript
- Expo Router

The application should be compatible with:

- iOS
- Android

Development should prioritize rapid iteration and cross-platform compatibility.

---

# 4. Technology Stack

## Required

- React Native
- Expo
- TypeScript
- Expo Router

## Local persistence

Use AsyncStorage for the initial MVP.

Persist:

- Focus sessions
- Total focus time
- Today's focus time
- Distance
- Resources
- Civilization level
- Buildings
- Current planet
- User settings

Do not introduce a backend database in the initial MVP.

---

# 5. Application Structure

The initial application has four primary screens.

```text
Home
  ↓
Focus Setup
  ↓
Focus Session
  ↓
Mission Complete
  ↓
Home / Universe

Additional navigation:

Home
 ├── Focus
 ├── Universe
 ├── Ranking
 └── Profile

Ranking and Profile can initially be simple placeholder screens.

The primary playable experience is:

Home → Focus → Mission Complete → Universe
```

# 6. Main Game Modes

UNIVERSE has two modes.

## 6.1 Universe Mode

Main game mode.

The player develops their civilization.

Core loop:

Focus
→ Distance
→ Resources
→ Buildings
→ Civilization
→ Planet unlock

Distance alone does NOT unlock the next planet.

The player must develop the current civilization sufficiently.

## 6.2 Journey Mode

Secondary game mode.

This is a simple focus-distance game.

Focus time directly becomes travel distance.

There is no civilization building.

Example:

25 min Focus
→ +25,000 km

50 min Focus
→ +50,000 km

90 min Focus
→ +90,000 km

Journey Mode is intended for users who want a simple experience.

This mode does not need to be fully implemented in the first MVP.

# 7. Focus System

The initial Focus presets are:

15 minutes
25 minutes
50 minutes
90 minutes
Custom

The primary recommended session is 25 minutes.

Focus Session

When the user starts a session:

FOCUSING

25:00

The timer counts down.

The user may leave the app.

The timer must continue correctly when the application goes into the background.

When the timer reaches zero:

The session is completed.

The user receives rewards.

# 8. Focus Rewards

Initial game balance:

1 Focus Minute = 1,000 km

Therefore:

| Focus | Distance |
| --- | --- |
| 5 min | 5,000 km |
| 15 min | 15,000 km |
| 25 min | 25,000 km |
| 50 min | 50,000 km |
| 90 min | 90,000 km |
| 120 min | 120,000 km |

These values are game values, not real astronomical distances.

# 9. Resources

The initial MVP uses only three resources.

Materials

Used primarily for construction.

Energy

Used primarily for technological development and space development.

Research

Used to unlock research and advanced civilization levels.

Do NOT add additional resource types unless explicitly required.

Avoid creating:

Food
Water
Fuel
Metal
Oxygen
Credits
Population

in the initial MVP.

# 10. Resource Rewards

Initial reward system:

For every Focus Minute:

Distance: +1,000 km
Energy: +1

For every 25-minute completed session:

Materials: +10
Research: +5

Therefore a 25-minute session gives:

+25,000 km
+25 Energy
+10 Materials
+5 Research

A 50-minute session gives:

+50,000 km
+50 Energy
+20 Materials
+10 Research

A 90-minute session gives:

+90,000 km
+90 Energy
+30 Materials
+15 Research

Materials and Research should scale by completed 25-minute blocks.

Do not overcomplicate the formula.

# 11. Pomodoro

The application supports common focus durations.

Recommended presets:

15 min — Quick Focus
25 min — Classic
50 min — Deep Focus
90 min — Long Expedition

The 25-minute session is the primary MVP experience.

Future Pomodoro support may include:

25 Focus
5 Break
25 Focus
5 Break
25 Focus
5 Break
25 Focus
15 Long Break

Do not implement automatic Pomodoro cycles in the initial MVP unless simple to add.

# 12. Mission Complete

After a successful Focus session, show a clear completion screen.

Example:

MISSION COMPLETE

🚀 +25,000 km

🪨 +10 Materials
⚡ +25 Energy
🔬 +5 Research

EARTH
125,000 km explored

[CONTINUE]

The completion screen should feel rewarding.

However, avoid excessive animations in the initial implementation.

# 13. Universe Mode

The starting planet is:

Earth

The player develops Earth civilization before traveling to the Moon.

Core concept:

Earth
 ↓
Scout Station
 ↓
Research Base
 ↓
Mining Facility
 ↓
Advanced City
 ↓
Space Center
 ↓
Moon

# 14. Earth Civilization

Earth has five civilization levels.

| Level | Civilization | Focus Equivalent |
| --- | --- | --- |
| 0 | Undeveloped | 0 min |
| 1 | Scout Station | 25 min |
| 2 | Small Base | 75 min |
| 3 | Settlement | 150 min |
| 4 | Advanced City | 300 min |
| 5 | Space Center | 500 min |

These values represent cumulative Focus time.

# 15. Earth Buildings

Level 1
Scout Station

Cost:

Materials: 10
Energy: 25

Unlock condition:

25 Focus Minutes

Level 2
Research Base

Cost:

Materials: 20
Energy: 50
Research: 10

Unlock condition:

75 cumulative Focus Minutes

Level 3
Mining Facility

Cost:

Materials: 40
Energy: 100
Research: 20

Unlock condition:

150 cumulative Focus Minutes

Level 4
Advanced City

Cost:

Materials: 80
Energy: 150
Research: 40

Unlock condition:

300 cumulative Focus Minutes

Level 5
Space Center

Cost:

Materials: 120
Energy: 250
Research: 75

Unlock condition:

500 cumulative Focus Minutes

The exact economy can be tuned later.

The important concept is:

Focus generates resources → resources construct civilization.

# 16. Planet Unlock

The Moon must NOT unlock simply because the player accumulated distance.

The player must satisfy civilization requirements.

Moon unlock requirements:

Earth Civilization Level: 5
Space Center: Built
Explore: Sufficient distance

The initial game distance for the Moon is:

384,400 km

This number is based on the approximate Earth-Moon distance but is used as a game milestone.

Once the requirements are satisfied:

MOON EXPEDITION AVAILABLE

appears.

The user can then launch the expedition.

# 17. Distance Progress

Distance is separate from civilization progression.

Every Focus Minute:

+1,000 km

Distance represents exploration.

Civilization represents development.

Therefore:

Distance = Where you have traveled

Civilization = What you have built

This distinction is fundamental.

# 18. Exploration Milestones

The Earth journey may have discoveries.

Example:

50,000 km
→ First Deep Space Signal

100,000 km
→ Unknown Object

200,000 km
→ Lunar Signal

300,000 km
→ Moon Visible

384,400 km
→ Moon Reached

These are game milestones.

They do not need to correspond to real astronomical events.

# 19. Discovery System

Completed Focus sessions may trigger discoveries.

Base rewards should always be guaranteed.

Discoveries are bonus rewards.

Example:

MISSION COMPLETE

+25,000 km
+10 Materials
+25 Energy
+5 Research

NEW DISCOVERY

"An unknown mineral was detected."

Bonus:
+5 Materials

Do not make the core economy depend on random rewards.

Randomness should be an additional bonus.

# 20. Home Screen

The Home screen is the most important screen.

It should display:

UNIVERSE

🌍 EARTH

Civilization Lv. 3
Settlement

125,000 km explored

Today's Focus
75 min

🔥 4 day streak

[ FOCUS ]

------------------

Civilization
████████░░ 75%

Next:
Advanced City

150 / 300 min

The primary CTA must be:

FOCUS

Do not clutter the Home screen.

# 21. Focus Setup Screen

Display:

START EXPEDITION

Choose duration

[15 min]
[25 min]
[50 min]
[90 min]

[Custom]

Mission:
Study

[START]

The category selector is optional in the initial MVP.

# 22. Focus Screen

The Focus screen should be extremely minimal.

Example:

🚀

EARTH → MOON

24:37

FOCUSING...

Put your phone down.
Your rocket is traveling.

Do not show many game statistics during Focus.

The goal is to encourage the user to stop looking at the phone.

# 23. Universe Screen

The Universe screen should visualize civilization progression.

Example:

🌌 MY UNIVERSE

🌍 EARTH

Civilization Lv. 3

[Scout Station] ✓
[Research Base] ✓
[Mining Facility] ✓
[Advanced City] 🔒
[Space Center] 🔒

Resources

🪨 42
⚡ 180
🔬 32

Explored
125,000 km

[BUILD]

A visual representation of the planet is preferred over a purely numerical UI.

For the MVP, 2D graphics are sufficient.

Do NOT build a complex 3D engine.

# 24. Ranking Screen

The initial Ranking screen can use mock/local data.

Tabs:

Friends
League
World

The actual backend ranking system is not required for the MVP.

The primary ranking metric should be:

Weekly Focus Time

Example:

WEEKLY LEAGUE

1. Alex      8h 42m
2. User      7h 35m
3. Mike      6h 58m

Do not rank users based on purchasable game resources.

# 25. Profile Screen

Display:

PROFILE

Total Focus
42h 18m

Current Streak
7 days

Total Distance
2,430,000 km

Planets Discovered
2

Best Week
8h 42m

Achievements
🏆 First Mission
🌙 Reached Moon
🔥 7 Day Streak

# 26. Navigation

Use a bottom tab navigation.

Initial tabs:

Home
Universe
Ranking
Profile

Focus should be accessed primarily through the Home screen.

Do not put Focus as a permanent bottom tab unless UX testing shows it is necessary.

# 27. Data Model

Initial local data structure can be approximately:

```ts
type UserProgress = {
  totalFocusMinutes: number;
  todayFocusMinutes: number;
  currentStreak: number;

  distanceKm: number;

  materials: number;
  energy: number;
  research: number;

  civilizationLevel: number;

  buildings: string[];

  currentPlanet: "earth" | "moon";

  discoveredItems: string[];
};
```

Focus session:

```ts
type FocusSession = {
  id: string;
  durationMinutes: number;
  startedAt: string;
  completedAt: string;
  completed: boolean;
};
```

The exact implementation can differ if there is a clear technical reason.

# 28. State Management

Keep state management simple.

For the initial MVP:

React state
Context if necessary
AsyncStorage for persistence

Do NOT introduce Redux or another complex state-management library unless there is a clear need.

# 29. Timer Requirements

The timer must be based on timestamps, not simply decrementing state every second.

Do NOT rely on:

```ts
setInterval(() => {
  time -= 1;
}, 1000);
```

as the source of truth.

The app may go into the background.

Instead:

startTimestamp
endTimestamp
currentTimestamp

should determine remaining time.

When the application resumes:

remaining = endTimestamp - currentTimestamp

This ensures the timer remains accurate when the app is backgrounded.

# 30. UI Design Direction

Visual identity:

Minimal futuristic space game.

Desired feeling:

Dark space background
Clean typography
Strong contrast
Subtle gradients
Planet / rocket imagery
Minimal UI clutter
Premium but playful

Avoid:

Generic productivity-app appearance
Excessive neon
Excessive gradients
Too many cards
Corporate dashboard aesthetics

The app should feel like a game, not a task manager.

# 31. Animation

Animations should be subtle and purposeful.

Useful animations:

Rocket movement
Distance counter
Resource increase
Building construction
Civilization level-up
Planet unlock

Do not add animations everywhere.

Performance is more important than visual complexity.

# 32. Error Handling

The application should gracefully handle:

App being backgrounded
App being closed during Focus
Device restart
Invalid stored data
Timer completion
Duplicate reward claims

A completed Focus session must not accidentally reward the user twice.

# 33. MVP Definition of Done

The MVP is considered complete when a user can:

Open the app
See Earth
Select a Focus duration
Start a Focus session
Leave the application
Return to the app
Complete the session
Receive distance and resources
See their distance increase
See their civilization progress
Build Earth buildings
Reach Space Center
Unlock the Moon
View their profile statistics

The entire loop must work without a backend.

# 34. Development Rules for AI Agents

When modifying this project:

Rule 1

Do not implement features that are not specified in the current task.

Rule 2

Do not introduce unnecessary dependencies.

Rule 3

Do not rewrite working parts of the application without a reason.

Rule 4

Keep components modular.

Rule 5

Use TypeScript strictly.

Avoid unnecessary any.

Rule 6

Before adding a new library, explain why it is necessary.

Rule 7

After making significant changes:

Run the project
Check for TypeScript errors
Check for runtime errors
Fix errors before finishing
Rule 8

Prioritize mobile usability.

The primary target is a smartphone screen.

Rule 9

Do not implement backend infrastructure until explicitly requested.

Rule 10

Do not change core game rules without explicit approval.

# 35. Development Philosophy

The project is being developed iteratively.

The priority order is:

1. Core gameplay
2. Usability
3. Visual quality
4. Game balance
5. Social features
6. Backend
7. Monetization
8. AI features

Do not optimize future architecture at the expense of rapid MVP development.

The first goal is:

Make one person want to complete another Focus session because they want to see their universe grow.

# 36. Current Development Target

The first implementation milestone is:

MILESTONE 1 — Playable Focus Loop

Implement only:

Home
 ↓
Focus Setup
 ↓
25-minute Focus Timer
 ↓
Mission Complete
 ↓
Home

The timer must work correctly when the application is backgrounded.

After completion:

Distance +25,000 km
Materials +10
Energy +25
Research +5
Focus Time +25 min

must be persisted locally.

Do not implement the full civilization system until this loop works reliably.

# 37. Future Roadmap

Phase 1 — Core MVP
Focus timer
Rewards
Earth
Civilization
Local persistence
Phase 2 — Game
Better Earth visual
Buildings
Discoveries
Moon
Journey Mode
Achievements
Streaks
Phase 3 — Social
Account
Friends
Weekly League
World ranking
University ranking
Phase 4 — Advanced
Screen Time integration
Notifications
AI coach
Personal analytics
Seasonal events
Ship customization
Phase 5 — Monetization
Cosmetic customization
Premium statistics
AI coaching
University / company challenges
Other premium features

# 38. Important Product Definition

UNIVERSE is NOT:

A Pomodoro timer with a rocket animation.

UNIVERSE is:

A game where real-world focus time becomes the engine of a persistent personal universe.

The rocket is the immediate feedback.

The civilization is the long-term progression.

The planet is the milestone.

The ranking is the social layer.

Focus is the underlying real-world behavior.

Keep this distinction in mind when designing and implementing every feature.
