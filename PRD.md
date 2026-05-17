# Product Requirements Document — Dog Breed Exploration (v1)

> Scope note: This document covers **product requirements only**. System design and
> technical decisions are intentionally excluded and will be authored separately in a
> future `SYSTEM_DESIGN.md`.

## 1. Vision

A personal, private **"DogDex"**: the user browses dog breeds presented as collectible
cards, finds a breed by **speaking its name** or by **filtering on physical traits**, and
**ticks breeds off as "collected"** when they spot one in real life — earning more reward
for rarer breeds. It should feel like collecting Pokémon cards, but for real dog breeds.

## 2. Target Users

Dog enthusiasts, casual "breed spotters," and families/kids who enjoy collection
mechanics. Single-user; no social or multi-user features in v1.

## 3. v1 Goals (Scope)

1. Browse a catalog of dog breeds as collectible cards.
2. Voice search: speak a breed name to find its card.
3. Attribute filter / breed identifier: narrow breeds by physical traits.
4. Mark a breed as **seen/collected** with one reversible toggle.
5. Light gamification: completion %, points by rarity, badges/milestones.

## 4. Non-Goals / Deferred (not in v1)

- AI photo recognition of breeds.
- Photo upload / attaching user images to a breed.
- A per-sighting log (date, notes, multiple sightings of the same breed).
- Heat map / location clustering / GPS.
- Cats (v1 is **dogs only**).
- Social, sharing, accounts, multi-device sync, community data.
- A polished dedicated web experience (mobile-first for v1; web refinement comes later).

## 5. Feature Requirements

### F1 — Breed Catalog ("DogDex")
- A grid of breed cards. Uncollected breeds appear **locked** (greyed/silhouette);
  collected breeds appear **unlocked** (full color, with a rarity treatment).
- Tapping a card opens a **breed detail view** with the breed's information and a
  Collected / Not-collected toggle.
- A search bar (text and voice) and sorting (e.g., by name, rarity, collected status).

### F2 — Voice Search (must-have)
- The user taps a mic control and speaks a breed name; the app finds and shows the
  matching breed card(s).
- Tolerant of mispronunciation/near-matches; falls back to text search when voice is
  unavailable.

### F3 — Attribute Filter / Breed Identifier
- The user describes a dog they saw by selecting physical traits: **size, coat color,
  coat type, coat length, ear shape, tail shape, build**.
- The app returns a **shortlist of candidate breeds** (never a single forced answer) so
  the user can confirm visually by photo. They can mark a breed collected from results.
- A clear "reset filters" action.

### F4 — Collection (Seen/Collected)
- One per-breed toggle: **Collected ↔ Not collected**. The user's progress is private to
  them and persists between sessions.
- Trivially reversible (a wrong guess can be undone). No photo or sighting log required.

### F5 — Gamification (Cards + Light)
- **Completion %**: collected breeds ÷ total breeds in the catalog.
- **Score**: each breed is worth points based on its rarity; **rarer breeds award more
  points**. Total score is shown to the user.
- **Rarity tiers**: every breed has a tier (e.g., Common / Uncommon / Rare / Legendary),
  shown visually on its card.
- **Badges / milestones**: e.g., First Catch; 10 / 25 / 50 / 100 breeds collected; "All
  toy breeds"; "First Legendary"; 100% completion.
- A progress/achievements view summarizing completion %, score, and earned badges.

## 6. Information Shown for Each Breed (card content)

Each breed card/detail presents, at minimum: breed name, a photo, country/region of
origin, size category, typical temperament, breed group, typical life span, the physical
traits used by the identifier (coat, ears, tail, build), its rarity tier, and its point
value.

## 7. Screens / User Flows

1. **Home / Dashboard** — completion %, total score, recent badges, quick actions.
2. **DogDex grid** — breed cards, text + voice search, sort/filter.
3. **Breed detail** — full information, rarity, collect toggle.
4. **Identify** — trait pickers and the candidate-breed shortlist.
5. **Achievements** — badges and milestones.

## 8. Product Constraints (user-decided)

- **Dogs only** in v1.
- The catalog is a **fixed, curated set of ~120 popular dog breeds** (final count
  flexible).
- The experience must work **without an account/sign-up** and **without an internet
  connection**; a user's collection is **private and kept only for that user**.
- **Mobile-first**; usable in a browser, with a refined web experience after v1.
- Logging a breed is a **single seen/collected toggle** — not a detailed sighting log.

## 9. Limitations Acknowledged (from Idea.txt)

- *The user can't always photograph a dog they see* → logging is a quick toggle; no photo
  is required.
- *The user may misjudge a breed* → the identifier returns a confirm-by-photo shortlist,
  and the collected toggle is easily reversible.
- *Mixed breeds are hard to categorize* → the identifier offers candidate matches, never
  a forced single answer, with no penalty for guessing. (An "unknown/mixed" note is a
  deferred idea.)

## 10. Success Criteria (v1 Acceptance)

A user can browse all breeds, find a breed by voice, narrow breeds with the attribute
filter, mark/unmark a breed as collected, and see their completion %, score, and at least
one earned badge — all privately, with no account and no internet connection.

## 11. Out of Scope for This Document

System design and technical decisions (platform/tech approach, data storage, offline
mechanism, voice technology, breed-data sourcing and structure) are intentionally **not**
covered here. They will be addressed separately in a future `SYSTEM_DESIGN.md`.
