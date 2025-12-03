# Mixed Traffic Flow Simulation Platform based on CARLA

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.7](https://img.shields.io/badge/python-3.7-blue.svg)](https://www.python.org/)
[![CARLA](https://img.shields.io/badge/CARLA-Simulator-green.svg)](https://carla.org/)

## 📖 Overview

With the development of Connected Automated Vehicle (CAV) technology, mixed traffic consisting of Human-Driven Vehicles (HDVs) and CAVs will exist for a long time. Mixed traffic simulation is crucial for autonomous driving testing, microscopic characteristic analysis, and traffic management strategy evaluation.

This project develops a high-fidelity **mixed traffic simulation platform** driven by microscopic traffic flow models and coupled with platoon-based cooperative control strategies, built upon the **CARLA simulator**.

### Key Features
* **Microscopic Modeling:**
    * **HDVs:** Implemented using the **IDM** (Intelligent Driver Model) for car-following and **MOBIL** for lane-changing.
    * **CAVs:** Implemented using **ACC** (Adaptive Cruise Control) and **CACC** (Cooperative ACC) models depending on the preceding vehicle type.
* **Advanced Lane Change Logic:**
    * **DLC (Discretionary Lane-Change):** A model for CAVs that considers the differences in desired time gaps when following different vehicle types.
    * **MLC (Mandatory Lane-Change):** A model optimized for off-ramp scenarios integrating safety and timeliness.
* **Cooperative Control:** A longitudinal **platoon control strategy** using linear feedback control for CAVs on Dedicated Lanes (DLs).
* **Comprehensive Evaluation:** Multidimensional evaluation metrics including Safety (MTTC, DRAC), Efficiency (Throughput, Speed), and Environmental Impact (Fuel, Emissions).

---

## 🏗️ Simulation Structure
![Platform Structure](DCAVL/Platform_structure.png)

As shown in the figure above, the simulation platform consists of three core modules:

1.  **Traffic Generator:** Generates mixed traffic flow with customizable parameters such as Market Penetration Rate (MPR), flow volume, and destination distribution.
2.  **Mixed Traffic Flow Operation:**
    * **Self-Driving System:** Adopts a perception-planning-control architecture.
    * **Platoon-Based Cooperative Control:** Manages platoon formation, merging, splitting, and cooperative longitudinal control on Dedicated Lanes.
    * **Vehicle Register:** Records real-time trajectories and states of all vehicles.
3.  **Traffic Evaluation:** A post-processing module that assesses the traffic performance based on the recorded data from multiple dimensions (Safety, Efficiency, Environment).

---

## 🚗 Simulation Scenario: A Case Study
![Simulation Scenario](DCAVL/Simulation_scenario.png)

To validate the models and strategies, we constructed a **one-way three-lane highway scenario** with an off-ramp in CARLA:

* **Lane Configuration:**
    * **Lane 1 (Innermost):** Designated as the **Dedicated Lane (DL)** for CAVs (when the DL policy is active).
    * **Lane 2 & 3:** Shared lanes for both HDVs and CAVs.
* **Zonal Analysis:** The road segment is divided into three regions to analyze traffic behavior in detail:
    * **Region 1:** Upstream free-flow area.
    * **Region 2 (Influence Zone):** The critical area (-500m to 500m) where vehicles perform mandatory lane changes to exit via the off-ramp.
    * **Region 3:** Downstream area.
* **Traffic Generation:** Vehicles are spawned at -3000m and stabilize their flow by -2000m. The simulation covers a 4km stretch of highway operations.

---

## 📝 Citation

If you find this code or paper useful for your research, please cite our paper:

```bibtex
@article{xiong2025modelling,
  title={Modelling and simulation of mixed traffic flow with dedicated lanes for connected automated vehicles},
  author={Xiong, Zhuozhi and Hu, Pei and Li, Ni and Chen, Xu and Chen, Wang and Wang, Hao and Xie, Ning and Li, Ye and Dong, Changyin},
  journal={Expert Systems with Applications},
  volume={274},
  pages={127027},
  year={2025},
  publisher={Elsevier},
  doi={10.1016/j.eswa.2025.127027}
}
