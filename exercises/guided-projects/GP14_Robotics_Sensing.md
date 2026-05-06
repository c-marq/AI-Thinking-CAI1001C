# GP14: Reinforcement Learning Exploration

**CAI1001C: Artificial Intelligence (AI) Thinking | Miami Dade College**
**Chapter 14: Robotics, Sensing, and Autonomous Systems**
**Guided Project — Reference Material (Not Graded)**

---

## Activity Overview

In this guided activity, you'll explore reinforcement learning — the third learning paradigm — through a structured thought experiment. Instead of running code, you'll work through a warehouse robot navigation scenario on paper, making decisions about reward design and observing how different reward structures change the robot's behavior.

By the end of this activity, you will be able to:

- Explain how reinforcement learning differs from supervised and unsupervised learning
- Identify the five core RL components: agent, environment, state, action, and reward
- Predict how changing reward values affects an agent's learned behavior
- Connect reinforcement learning concepts to real-world robotics applications

---

## Part 1: The Three Learning Paradigms — Quick Review

Before we dive into reinforcement learning, let's place it alongside the two paradigms you already know.

| Paradigm | How It Learns | Data Needed | Example |
|---|---|---|---|
| **Supervised Learning** (Ch 6–9) | From labeled examples — a "teacher" provides correct answers | Labeled dataset (inputs + correct outputs) | Predicting loan approval from applicant features |
| **Unsupervised Learning** (Ch 6) | From unlabeled data — finds hidden patterns on its own | Unlabeled dataset (inputs only) | Grouping customers into segments by behavior |
| **Reinforcement Learning** (Ch 14) | From trial and error — takes actions, receives rewards/penalties | No dataset — learns by interacting with an environment | A robot learning to navigate a warehouse |

**Key distinction:** In supervised learning, someone tells the model the right answer. In reinforcement learning, no one knows the right answer in advance — the agent discovers it through experience.

### Discussion Prompt

*Prof. Reyes asks: "When you learned to ride a bike, did someone give you a labeled dataset of correct vs. incorrect pedaling motions? Or did you get on, fall, adjust, and eventually figure it out?" Which learning paradigm does bike-riding most resemble?*

---

## Part 2: Meet the Warehouse Robot

Here's your scenario. A small warehouse has a 5×5 grid floor. A mobile robot starts in the bottom-left corner (Position A1) and needs to reach the charging station in the top-right corner (Position E5). The grid looks like this:

```
    1     2     3     4     5
  +-----+-----+-----+-----+-----+
E |     |     |     |     | ⚡  |  ← GOAL (Charging Station)
  +-----+-----+-----+-----+-----+
D |     | ███ |     |     |     |
  +-----+-----+-----+-----+-----+
C |     | ███ |     | ███ |     |
  +-----+-----+-----+-----+-----+
B |     |     |     | ███ |     |
  +-----+-----+-----+-----+-----+
A | 🤖  |     |     |     |     |  ← START
  +-----+-----+-----+-----+-----+
```

- **🤖** = Robot (starts at A1)
- **⚡** = Charging station / Goal (at E5)
- **███** = Shelving units (obstacles — the robot can't pass through these)

The robot can move **up, down, left, or right** — one square at a time. It cannot move diagonally. It cannot move through obstacles or off the grid.

---

## Part 3: Round 1 — Random Exploration

**Scenario:** The robot has NO reward function. It moves randomly — picking up, down, left, or right with equal probability at each step. If it tries to move into an obstacle or off the grid, it stays in place and picks again.

### Your Turn

1. Starting at A1, trace a plausible random path on the grid. Use arrows or list coordinates (e.g., A1 → A2 → B2 → B3...). Your path should be at least 15 moves long.

2. Did your random robot reach the goal? How many moves did it take?

3. If you ran 100 random simulations, roughly what percentage do you think would reach the goal within 50 moves? (Estimate — there's no exact right answer here.)

### Class Discussion

*Why is random exploration inefficient? What information is the robot missing that would help it make better decisions?*

**Key takeaway:** Without feedback, the robot has no way to learn from its mistakes. It might wander back and forth forever. This is why reinforcement learning adds a reward signal — it gives the agent a reason to prefer some actions over others.

---

## Part 4: Round 2 — Adding Rewards

Now we give the robot a reward function. After every action, it receives a numerical score:

| Event | Reward |
|---|---|
| Reach the charging station (goal) | **+10** |
| Each step taken | **-1** |
| Hit an obstacle or grid edge | **-5** |

### How This Changes Behavior

With these rewards, the robot's objective is to **maximize total reward**. That means:

- Getting to the goal quickly (each step costs -1, so fewer steps = higher total reward)
- Avoiding obstacles (each collision costs -5)
- Not wandering aimlessly (every step without progress costs -1)

### Your Turn

1. Given this reward structure, what's the **optimal path** from A1 to E5? Trace it on the grid. Count the total steps.

2. Calculate the total reward for the optimal path:
   - Steps taken: ___
   - Step penalties: ___ × (-1) = ___
   - Goal reward: +10
   - **Total reward:** ___

3. Now calculate the total reward for a path that takes 20 steps and hits 2 obstacles:
   - Step penalties: 20 × (-1) = -20
   - Obstacle penalties: 2 × (-5) = -10
   - Goal reward: +10
   - **Total reward:** ___

4. Which path does the RL agent prefer? Why?

### Class Discussion

*The agent doesn't know the optimal path on its first attempt. It discovers it over many episodes — trying different routes, receiving rewards, and gradually favoring paths with higher total reward. This is what "learning" means in RL.*

---

## Part 5: Round 3 — Changing the Reward Structure

This is where reinforcement learning gets interesting. **The reward function defines what the agent values.** Change the rewards, and the agent learns completely different behavior.

### Scenario A: Safety-First Rewards

| Event | Reward |
|---|---|
| Reach the goal | **+10** |
| Each step taken | **-1** |
| Hit an obstacle | **-50** |

**Predict:** How will the robot's behavior change with a much harsher obstacle penalty? Will it take the shortest path or a longer, safer path that stays far from obstacles?

### Scenario B: Speed-First Rewards

| Event | Reward |
|---|---|
| Reach the goal | **+100** |
| Each step taken | **-5** |
| Hit an obstacle | **-2** |

**Predict:** With a huge goal reward and a small obstacle penalty, what kind of path will the agent prefer? Will it avoid obstacles carefully or risk clipping them to reach the goal faster?

### Scenario C: Exploration Bonus

| Event | Reward |
|---|---|
| Reach the goal | **+10** |
| Each step taken | **-1** |
| Hit an obstacle | **-5** |
| Visit a new square for the first time | **+2** |

**Predict:** With a bonus for visiting new squares, will the robot go straight to the goal or explore the warehouse first? When might this reward structure be useful? (Hint: think about SLAM from the chapter.)

### Your Turn

For each scenario (A, B, C):
1. Predict the type of path the robot would learn (shortest, safest, most exploratory)
2. Describe one real-world robotics situation where that reward structure would make sense

### Class Discussion

*Prof. Reyes asks: "A self-driving car's reward function encodes moral values — 'avoid pedestrians' has a higher penalty than 'avoid traffic cones.' Who should design these reward functions? Engineers? Ethicists? The public? Lawmakers?"*

---

## Part 6: Connecting RL to Autonomous Vehicles

The warehouse robot scenario is simple — a 5×5 grid with a handful of obstacles. Now scale it up:

- The "grid" is every road in Miami
- The "obstacles" include other cars, pedestrians, cyclists, traffic signals, construction zones, and potholes
- The "actions" include accelerate, brake, turn, change lanes, stop, and merge
- The "state" updates dozens of times per second from cameras, lidar, and radar
- The "reward function" includes hundreds of values: stay in lane (+), run a red light (-1000), arrive at destination (+), hit a pedestrian (-∞)

### Your Turn

1. List 5 events that should receive **positive rewards** in a self-driving car's RL system.

2. List 5 events that should receive **negative rewards (penalties)**.

3. Rank your 5 penalties from least severe to most severe. What does this ranking reveal about your values?

4. If two engineers design different reward functions — one prioritizes passenger safety above all else, the other prioritizes minimizing harm to pedestrians — the same car would learn different driving behaviors. Is there a "right" answer? Who should decide?

### Class Discussion

*This connects directly to the Ethics in Focus section. The trolley problem isn't just philosophy — it's a design decision embedded in the reward function.*

---

## Closing: What We Built Today

In this activity, you explored reinforcement learning by:

- Comparing RL to supervised and unsupervised learning (the three paradigms)
- Identifying the five core RL components in a warehouse scenario
- Observing how random exploration without rewards is inefficient
- Designing reward functions and predicting how they change agent behavior
- Connecting RL reward design to autonomous vehicle ethics

**Key insight:** In reinforcement learning, the reward function IS the teacher. It defines what the agent values, what it avoids, and what "success" means. Designing good reward functions is one of the most important — and most ethically loaded — tasks in modern AI.

**Looking ahead:** Your Group Lab will apply the concepts from this entire chapter — sensing, manipulation, HRI, navigation, RL, and autonomy — to real robotics systems through video analysis. Your Homework assignment will deepen that analysis for a single application and connect it to the NG13 case study.
