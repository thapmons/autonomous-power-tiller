# 🚜 Autonomous Power Tiller: Physical AI for Small-Scale Farming

> **Status: Conceptual / Research Phase**
> An initiative to bridge the gap between "Bits and Atoms" by automating the single-axle tractors (Power Tillers) essential to South Asian agriculture.

---

## The Mission
In South Asia, the two-wheeler tractor is the primary tool for millions of farmers. However, operating them—especially during the "puddling" phase in wet rice paddies—is physically grueling and dangerous.

**This project explores a Physical AI framework to:**
1. **Reduce Human Drudgery:** Automate steering and throttle in high-heat and muddy conditions.
2. **Increase Precision:** Use AI-driven spatial awareness for consistent seed placement and tilling.
3. **Democratize Tech:** Focus on low-cost, retrofittable kits rather than expensive new machinery.

---

## Planned Tech Stack
*These are the tools I am currently researching and learning to implement this vision.*

![ROS2](https://img.shields.io/badge/ros2-%230A0FF9.svg?style=for-the-badge&logo=ros&logoColor=white)
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![C++](https://img.shields.io/badge/c++-%2300599C.svg?style=for-the-badge&logo=c%2B%2B&logoColor=white)
![NVIDIA](https://img.shields.io/badge/NVIDIA-76B900?style=for-the-badge&logo=nvidia&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)

---

## Proposed System Architecture
This pipeline represents how the AI "Brain" interacts with the tractor "Body."

```mermaid
graph TD
    subgraph "Perception (The Senses)"
        A[RGB Camera / Ultrasonic] -->|Visual Data| B(Furrow/Edge Detection)
        C[IMU + Wheel Encoders] -->|Spatial Data| D(Odometry)
    end

    subgraph "Decision (The Brain)"
        B --> E{Navigation Logic}
        D --> E
        E -->|Control Signals| F[PID Controller]
    end

    subgraph "Action (The Body)"
        F -->|Steer| G[Linear Actuators]
        F -->|Throttle| H[Servo Motors]
    end
    
    G --> I[Physical Movement]
    H --> I
    I -.->|Sensor Feedback| A
