# Distributed AI: Multi-Agent Crowd Evacuation Dynamics

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![NetLogo](https://img.shields.io/badge/NetLogo-7.0.2-orange.svg)](https://ccl.northwestern.edu/netlogo/)

An advanced Agent-Based Model (ABM) developed to simulate high-density pedestrian flow using **Distributed Artificial Intelligence (DAI)** principles. This project moves away from simple reactive steering, implementing a sophisticated **Iterative Negotiation & Reservation Protocol** for spatial conflict resolution.

## 🔬 Core Engineering Principles

The system is built upon three pillars of Distributed Intelligence:

1. **Iterative Reservation Protocol:** A distributed coordination mechanism where agents negotiate patch occupancy in real-time. It uses an asynchronous "lock" system (`reserved-by`) to prevent collisions and ensure fluid motion.
2. **Game Theoretic Conflict Resolution:** A hierarchical priority system coupled with a greedy tie-breaking strategy.
   * **Hierarchy:** High-priority agents (e.g., instructors) override standard requests.
   * **Distance-based Optimization:** When hierarchies match, the agent with the lowest cost-to-goal wins the reservation, prioritizing the front of the queue.
3. **Dynamic Pathfinding (Dijkstra-based):** A pre-calculated topological cost map using a Flood Fill/Dijkstra algorithm. This allows agents to navigate complex architectural barriers (non-Euclidean paths) with 100% reliability.

## 🛠 Technical Implementation

### Predictive Flow Logic
Agents utilize a **Short-term Intent Analysis**. Before attempting a move, an agent checks if a target patch will be vacated in the same tick by its current occupant. This "look-ahead" behavior eliminates the classic "stop-and-go" waves found in simpler simulations.

### Anti-Deadlock Mechanism
Implements a passive back-off protocol with a **Reservation Blacklist**. If an agent loses a negotiation, it temporarily blacklists the contested resource to explore alternative paths or wait for a more optimal state, preventing local oscillations.

## 🚀 Experimental Scenarios & Benchmarking

The model's coordination resilience and emergent behaviors were evaluated across 5 distinct environmental configurations.

### 🏆 Featured: Main System Demonstration
The **Main Demo** showcases the baseline performance of the Iterative Reservation Protocol under balanced, symmetric exit conditions.

https://github.com/blaigene/Distributed-AI-Crowd-Dynamics/media/main_demo.mp4

---

### 📂 Stress Test Gallery
Below is a comparative breakdown of the specific coordination challenges addressed in each specialized environment:

| **Blocking Wall** (Pathfinding) | **Single Bottleneck** (Queuing) |
| :---: | :---: |
| ![Wall](media/blocking_wall_scenario.mp4) | ![Bottleneck](media/single_bottleneck_scenario.mp4) |
| **Complex Navigation:** Tests Dijkstra accuracy through architectural barriers. | **Crowd Pressure:** Analyzes emergent single-file formation under high density. |

| **Asymmetric Capacity** | **External Symmetric** |
| :---: | :---: |
| ![Asymmetric](media/asymmetric_capacity_scenario.mp4) | ![External](media/external_symmetric_exits_scenario.mp4) |
| **Resource Disparity:** Studies agent decision-making with 1-vs-3 exit friction. | **Flow Distribution:** Evaluates long-distance cost-map consistency. |

> [!NOTE]
> All simulations were recorded using a standardized agent density to ensure comparable metrics across different topological constraints.

## 📊 Analytical Metrics
The system outputs a detailed performance report upon completion:
* **Evacuation Efficiency:** Total ticks to zero-agent state.
* **Congestion Peaks:** Maximum concurrent queue size per exit.
* **Coordination Friction:** Total count of resolved deadlocks/conflicts.

## 💻 Setup
1. Open `Distributed_AI_Evacuation.nlogo` in **NetLogo 7.0.2+**.
2. Run `setup`.
3. Select an experiment scenario in the code (Exits Setup section).
4. Run `go`.

---
**Author:** Blai Gené Mora  
*Developed at Università degli Studi di Modena e Reggio Emilia (Unimore)*
