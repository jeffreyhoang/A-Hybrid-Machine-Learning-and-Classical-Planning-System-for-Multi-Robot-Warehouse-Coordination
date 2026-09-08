# A Hybrid Machine-Learning and Classical-Planning System for Multi-Robot Warehouse Coordination
> A hybrid coordination system combining classical multi-agent path planning with learned conflict-resolution policies for autonomous warehouse management


## Team Members
- Jeffrey Hoang

---

## Abstract
Autonomous warehouses rely on multiple mobile robots to transport packages efficiently, but independently planned routes can conflict at shared aisles, intersections, and narrow passages. This project proposes a hybrid coordination system that combines independent A* path planning with machine-learning-based conflict resolution. Each robot will first generate a route while considering static warehouse obstacles. When predicted conflicts occur, a lightweight ML model will assign priority scores to the affected robots and determine which robot should retain its route while others yield or replan. A time-aware A* planner will then generate alternative paths, and a deterministic safety validator will verify that the final routes contain no vertex or edge collisions before execution. The system will be evaluated in POGEMA and procedurally generated warehouse simulations. Performance will be compared with path-length priority, fixed prioritized planning, and classical conflict-based replanning using safety, efficiency, and machine learning metrics. The goal is to determine whether learned conflict resolution can reduce waiting, deadlocks, and delivery time while maintaining collision-free operation.

---

## Selected Track
Algorithm Track

---

## AI Novelty & Feasibility Audit

### Overall Assessment
The project is feasible and technically meaningful for a class project, but its broad research area has significant “red ocean” risk. Multi-agent pathfinding, A*, prioritized planning, Conflict-Based Search, learned policies, and hybrid classical-learning systems are all well-established research areas. A recent survey reviewed more than 200 classical, learning-based, and hybrid MAPF papers, demonstrating that the general topic is highly active and competitive.

The project should not claim to introduce a completely new multi-robot path-planning algorithm. Its potential contribution is narrower: using supervised learning to select conflict priorities after independently generated A* paths produce a predicted conflict, while using time-aware A* and deterministic validation to preserve safety.

### Novelty and Red-Ocean Risks
The main red-ocean risks are:
- Classical MAPF algorithms are heavily studied. A*, prioritized planning, and CBS have been used extensively for multi-robot coordination.
- Hybrid ML-classical planning is not new. Existing work has already combined learned local policies with classical heuristic search methods such as PIBT and LaCAM. Improving Learnt - - Local MAPF Policies with Heuristic Search
- Warehouse robot coordination is also well established. Recent research has applied prioritized planning to realistic warehouse tasks, including interdependent deliveries and robot dynamics. Multi-Agent Path Finding with Real Robot Dynamics and Interdependent Tasks for Automated Warehouses
- Benchmarking is becoming standardized. POGEMA was specifically developed to compare classical, learning-based, and hybrid multi-agent pathfinding methods fairly.

Because of this existing work, the project would have low novelty if described generally as “using machine learning to improve multi-robot path planning.”

### Defensible Project Contribution
The project can be positioned as a focused investigation into whether a learned conflict-resolution policy can outperform simple priority heuristics in specific congested scenarios. The ML model will not generate complete paths. Instead, it will analyze conflict features and select which robot should retain priority or replan. Candidate decisions will be labeled through counterfactual simulation by comparing their resulting makespan, waiting time, path cost, and downstream conflicts.

This gives the project a narrower and more defensible contribution:

Evaluating whether learned, state-dependent conflict prioritization provides measurable efficiency improvements over fixed path-length and predetermined priority rules while classical time-aware A* maintains collision-free execution.

The project’s originality will depend on the experimental design rather than on inventing a new planner. It should test difficult scenarios where simple rules may fail, such as narrow bottlenecks, unequal alternative routes, simultaneous conflicts, high congestion, and different task urgencies.

### Feasibility Assessment

The project has high implementation feasibility because:
- POGEMA and custom grid simulations can generate large amounts of training data.
- The ML model uses structured features rather than images or sensor data.
- A small MLP or Random Forest can run on a standard laptop CPU.
- A* and time-aware A* are implementable for small warehouse scenarios.
- The safety validator prevents the ML model from directly executing unsafe paths.
- CBS can serve as a comparison method or fallback for difficult cases.

The primary technical risk is that the ML model may simply learn the path-length rule and fail to outperform it. To address this, all methods should use the same A* replanner and safety validator, with only the priority-selection method changing. Performance should also be evaluated on unseen procedural layouts and external warehouse benchmarks.

### Final Audit Conclusion
The project has moderate applied novelty and strong feasibility, but low novelty at the frontier of MAPF research. It is appropriate for the Algorithm Track if presented as an empirical study of ML-guided conflict prioritization rather than as a new general-purpose pathfinding algorithm. The project should openly report cases where ML performs the same as or worse than classical heuristics, since demonstrating when machine learning is unnecessary is also a meaningful result.
