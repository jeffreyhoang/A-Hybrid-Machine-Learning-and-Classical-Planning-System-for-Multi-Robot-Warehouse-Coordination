# A Hybrid Machine-Learning and Classical-Planning System for Multi-Robot Warehouse Coordination
> A hybrid coordination system combining classical multi-agent path planning with learned conflict-resolution policies for autonomous warehouse management


## Team Members
- Jeffrey Hoang


## Abstract
Autonomous warehouses rely on multiple mobile robots to transport packages efficiently, but independently planned routes can conflict at shared aisles, intersections, and narrow passages. This project proposes a hybrid coordination system that combines independent A* path planning with machine-learning-based conflict resolution. Each robot will first generate a route while considering static warehouse obstacles. When predicted conflicts occur, a lightweight ML model will assign priority scores to the affected robots and determine which robot should retain its route while others yield or replan. A time-aware A* planner will then generate alternative paths, and a deterministic safety validator will verify that the final routes contain no vertex or edge collisions before execution. The system will be evaluated in POGEMA and procedurally generated warehouse simulations. Performance will be compared with path-length priority, fixed prioritized planning, and classical conflict-based replanning using safety, efficiency, and machine learning metrics. The goal is to determine whether learned conflict resolution can reduce waiting, deadlocks, and delivery time while maintaining collision-free operation.

## Selected Track
Algorithm Track
