# ⚡ Wumpus Logic Agent

> Student: Ahmad


## 🧠 Overview

A web-based Knowledge-Based Agent that navigates a **Wumpus World** grid using **Propositional Logic** and **Resolution Refutation** to deduce safe cells before moving.

## 🔗 Live Demo
(https://wumpus-agent-d6jzv74m3-ahmadshakeel917s-projects.vercel.app)

## 🚀 Features

| Feature | Description |
|---------|-------------|
| Dynamic Grid | Configurable rows × cols (3–8) |
| Random Hazards | Pits & Wumpus randomly placed each game |
| CNF Knowledge Base | Agent TELLs KB percept rules in CNF format |
| Resolution Refutation | Agent ASKs KB via propositional resolution (proves ¬PIT ∧ ¬WUMPUS) |
| Real-Time Metrics | Inference steps, safe cells confirmed, active percepts |
| Auto-Run Mode | Agent runs autonomously step by step |
| Game Over Overlay | Win/Lose detection with replay |


## 🤖 How the Agent Works

### 1. TELL — Adding Percept Rules to KB (CNF)

When the agent visits cell `(r,c)`:

```
No Breeze → ¬PIT(r±1,c) ∧ ¬PIT(r,c±1)   [unit clauses]
Breeze    → PIT(r-1,c) ∨ PIT(r+1,c) ∨ PIT(r,c-1) ∨ PIT(r,c+1)
No Stench → ¬WUMPUS(neighbors)
Stench    → WUMPUS(r-1,c) ∨ ...
Visited   → ¬PIT(r,c) ∧ ¬WUMPUS(r,c)
```

### 2. ASK — Resolution Refutation

To prove cell `(nr,nc)` is safe, the agent:
1. Negates the goal: assumes `PIT_nr_nc = True`
2. Adds it to KB as a unit clause
3. Resolves clause pairs until **⊥ (empty clause)** is derived
4. Contradiction found → `¬PIT_nr_nc` is proven ✓
5. Same process for `¬WUMPUS_nr_nc`

### 3. Move Strategy

```
Priority 1: Move to KB-proven-safe unvisited neighbor
Priority 2: Revisit safe visited neighbor (greedy toward gold)
Priority 3: Stuck → game ends
```

---

## 📁 Project Structure

```
wumpus-agent/
├── index.html      # Complete app (UI + KB + Resolution Engine)
├── vercel.json     # Vercel deployment config
└── README.md       # This file
```

---

## 🛠 Deploy on Vercel

```bash
# 1. Push to GitHub
git init
git add .
git commit -m "feat: Wumpus Logic Agent - AI2002 Assignment 6"
git remote add origin https://github.com/YOUR_USERNAME/wumpus-agent.git
git push -u origin main

# 2. Go to vercel.com → Import Project → Select repo → Deploy
```

---

## 📚 Topics Demonstrated

- Knowledge-Based Agents
- Propositional Logic (Syntax & Semantics)
- Conjunctive Normal Form (CNF)
- Resolution Refutation Algorithm
- Entailment via Model Checking
- Inference Rules (Modus Ponens, Unit Resolution)

---
