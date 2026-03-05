# fulcrum
Below is a **hackathon-optimized technical outline** designed for:

* **Fast build (24–48 hours)**
* **Minimal external dependencies**
* **Mostly stubbed data**
* **A visually impressive demo**

The goal is to make judges **feel like they’re watching a market simulation**, not a survey tool.

---

# Project Architecture Outline

**Project Codename:** Preflight (Synthetic Audience Simulator)

Goal:

> Simulate how a representative audience reacts to an ad, landing page, or product before launch.

Focus areas:

* visually impressive simulation
* agent personalities
* aggregated insights
* quick run time

---

# System Overview

```
                ┌─────────────────────┐
                │      Frontend       │
                │  Next.js + Tailwind │
                └──────────┬──────────┘
                           │
                           │
                ┌──────────▼──────────┐
                │   Simulation API    │
                │     FastAPI / TS    │
                └──────────┬──────────┘
                           │
        ┌──────────────────┼──────────────────┐
        │                  │                  │
        ▼                  ▼                  ▼
 Persona Generator   Agent Simulator    Result Aggregator
 (stub dataset)        (LLM or mock)       (analytics)

```

Most pieces can run **locally with mocked data**.

---

# Key Components

## 1. Persona Generator

Generates synthetic agents using **stratified sampling**.

### Input

```
target_location: USA
age_range: 18-35
gender_split: 50/50
income_range: 30k-80k
interests: fitness, tech
sample_size: 500
```

### Output

List of personas.

Example:

```
{
  id: 104,
  name: "Jordan",
  age: 24,
  gender: "female",
  location: "Austin",
  income: 52000,
  interests: ["fitness", "instagram"],
  personality: "impulse buyer",
  media_habits: ["TikTok", "Instagram"]
}
```

### Implementation (fast)

Use **JSON persona templates**.

Example:

```
personas/
  genz_female_fitness.json
  gamer_male_genz.json
  millennial_professional.json
```

Sampling logic:

```
agents = []

for segment in segments:
    agents += random.sample(template_pool, segment_size)
```

No external API required.

---

# 2. Ad / Campaign Input

Allow user to upload:

* image
* short video
* headline
* landing page screenshot

For hackathon simplicity:

```
Upload image
+ enter headline
+ enter CTA
```

Stored locally.

---

# 3. Agent Reaction Simulator

Core of the system.

Each persona evaluates the ad.

Prompt style:

```
You are:

Age: 23
Occupation: student
Location: Texas
Income: 30k
Interests: gym, TikTok

You see the following ad:

HEADLINE:
"Run faster with X shoes"

CTA:
"Buy now"

Answer:

1. Would you stop scrolling (1-10)
2. Would you click (yes/no)
3. Would you buy (yes/no)
4. One sentence reaction
```

---

## For Hackathon Speed

Use **hybrid approach**:

### Option A (better demo)

Run **20–30 real LLM calls**
Clone results to simulate 500 users.

```
30 agents → generate responses
then probabilistically expand to 500
```

---

### Option B (instant simulation)

Use **probabilistic scoring**.

Example:

```
fitness_interest → +3 click probability
high_income → +2 purchase probability
genz → +1 scroll_stop
```

Then generate response text using templates.

Example output:

```
"I’d probably click because I like running gear."
```

This runs **instantly**.

---

# 4. Agent Simulation Visualization (Important)

The demo moment.

Display **agents processing the ad** in real time.

UI idea:

Grid of avatars.

```
🙂 😐 😍 😑 😡
🙂 🙂 😐 😍 😑
```

As simulation runs:

Agents flip to reactions:

* 👍 click
* ❌ ignore
* 🛒 purchase
* 😕 confused

Animated.

---

# 5. Aggregation Engine

Collect results:

```
scroll_stop_score
click_rate
purchase_rate
sentiment
```

Example calculation:

```
CTR = clicks / total_agents
conversion = purchases / clicks
```

Segment analysis:

```
Gen Z: CTR 4.2%
Millennials: CTR 1.8%
Parents: CTR 0.9%
```

---

# 6. Insights Generator

Use LLM **once** to summarize feedback.

Input:

```
300 short user reactions
```

Output:

```
Top positive themes
Top complaints
Suggested improvements
```

Example:

```
Users like the humor but think the price is too high.
Gen Z responds strongly to the visuals.
Parents prefer clearer value messaging.
```

---

# 7. Dashboard

This is what makes the demo impressive.

### Metrics

Display:

* predicted CTR
* predicted conversion
* sentiment score
* demographic heatmap

---

### Charts

Use:

* Recharts
* Tremor
* Chart.js

Example:

```
CTR by demographic
Sentiment distribution
Purchase probability curve
```

---

### Persona Explorer

Click any agent.

Shows:

```
Agent #142
Age: 22
Location: LA
Reaction: "Looks cool but expensive"
Clicked: Yes
Purchased: No
```

This makes it **feel real**.

---

# Frontend Structure

```
/pages

index.tsx
upload.tsx
simulate.tsx
results.tsx
persona/[id].tsx
```

---

# Backend Structure

```
backend/

main.py
routes/
    simulate.py
    personas.py
    results.py

services/
    persona_generator.py
    agent_simulator.py
    analytics.py
```

---

# Example Simulation Flow

User flow:

### 1 Upload Ad

```
image
headline
CTA
```

---

### 2 Choose Audience

Sliders:

```
Age: 18-35
Gender: balanced
Income: 30k-80k
Location: US
Sample size: 500
```

---

### 3 Run Simulation

Loading screen:

```
Generating audience...
Running simulation...
Analyzing reactions...
```

Agents animate.

---

### 4 Results

Dashboard shows:

```
Predicted CTR: 2.7%
Conversion: 0.6%
Sentiment: 63% positive
```

Plus insights.

---

# Tech Stack (Hackathon Friendly)

-- using uv for fast package management

Frontend:

* **Next.js**
* **Tailwind**
* **Framer Motion**
* **Recharts**

Backend:

* **FastAPI** or **Node Express**

LLM:

* OpenAI
* Claude
* or even **mocked**

State:

* Local JSON
* No DB required

---

# Fake Dataset (Recommended)

Create:

```
demographics.json
interests.json
occupations.json
locations.json
```

Combine randomly to produce agents.

---

# Demo Script (Critical)

Demo should take **under 90 seconds**.

1️⃣ Upload Nike ad
2️⃣ Select Gen Z audience
3️⃣ Generate **500 agents**

Animation shows agents reacting.

4️⃣ Dashboard appears:

```
CTR: 3.2%
Top complaint: price
Top audience: Gen Z runners
```

5️⃣ Click one persona reaction.

Feels like **a synthetic focus group**.

---

# Stretch Features (If Time)

### Agent Debate

Simulate conversation:

```
Agent A: The price is crazy
Agent B: It's cheaper than Nike
```

Looks impressive.

---

### Auto Optimization

```
Suggested headline:
"Run Faster for Less"
```

---

### Multi Ad A/B

Upload **2 ads**.

Simulation picks winner.

---

# Hackathon Winning Angle

Position it as:

> **"Monte Carlo Simulation for Marketing."**

Instead of:

"AI personas".

---

If you'd like, I can also show you **the single most impressive UI feature you can add (that takes only ~40 lines of code but will absolutely blow judges away).**
