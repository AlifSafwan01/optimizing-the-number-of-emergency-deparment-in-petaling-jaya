# Optimizing the Number of Hospital Emergency Departments in Petaling Jaya using Set Covering Problem Analysis

This repository contains a summary of a Mathematical Science project. For the full article and citation, please visit the *Journal of Applied Mathematics and Computational Intelligence* or click the link [here](https://ejournal.unimap.edu.my/index.php/amci/article/view/1501/1283)

## Abstract
<p align="justify">
Emergency departments (EDs) has become a crucial frontline service for unscheduled patients who arrive at the hospital and need urgent attention. However, the emergency departments  is struggling to provide the service and ensure all potential demand are efficiently covered. This is proved by the previous research that, if the demand too far from the emergency department, the mortality rate will increase. Therefore, the main goal of this project is to find the least number of emergency departments needed to cover all potential demand within a certain distance.</p>

## Project Objectives

1. **Determine the Optimal Number of Emergency Departments** : Identify the minimum number of EDs in Petaling Jaya and surrounding areas to ensure full coverage within specified time limits.
2. **Identify Uncovered Areas** : Locate demand points that are not covered by any ED.
3. **Analyze Optimal Solution Behavior** : Evaluate solution behavior using,
   -Maximal Covering Location Problem (MCLP)
   -Maximum Expected Covering Location Problem (MEXCLP)

## Methodology

The project uses the **Set Covering Location Problem**, requiring:
1. Locations of Emergency Departments
2. Locations of Demand Points
3. Travel Distance and Duration between EDs and Demand Points

### Potential Demand Points and Emergency Departments Location

**470 Demand Point in Petaling Jaya**:
- 308 Residential Areas
- 45 Industrial Areas
- 110 Educational Institutions
- 7 Medical Facilities

**14 Potential Emergence Departments**:

| Hospital | City Address |
| --- | --- |
| Assunta Hospital | Petaling Jaya |
| KPJ Damansara Specialist Hospital | Petaling Jaya |
| Columbia Asia Hospital | Petaling Jaya |
| Thomson Hospital | Petaling Jaya |
| Beacon International Specialist Centre | Petaling Jaya |
| KMI Kelana Jaya Medical Centre | Petaling Jaya |
| Park City Medical Centre | Kuala Lumpur |
| University of Malaya Medical Centre | Kuala Lumpur |
| KPJ Damansara Specialist Hospital 2 | Kuala Lumpur |
| MSU Medical Centre | Shah Alam |
| Ara Damansara Medical Centre | Shah Alam |
| Subang Jaya Medical Centre | Subang Jaya |
| Sunway Medical Centre | Subang Jaya |
| Sungai Buloh Hospital | Sungai Buloh |

### MCLP Model
Sets,
| Symbol | Description |
| --- | --- |
| $H$ | Set of ED |
| $i$ | Index of $H$, $i = 1,...,14$ |
| $H_i$ | The $i$-th eED |
| $D$ | Set of demand points |
| $j$ | Index of $D$, $j = 1,...,470$ |
| $D_j$| The $j$-th demand point |

Parameters,
| Symbol | Description |
| --- | --- |
| $d_j$| Population demand at $D_j$ |
| $m$ | Number of ED to be located |
| $l$ | Travel time threshold |
| $T_{j,i}$ | Travel time from $H_i$ to $D_j$ |

Decision Variables,

$$
\begin{equation}
t_{j,i} = \begin{cases}
1 & \text{, }T_{j,i} \leq l \\
0 & \text{, otherwise}
\end{cases}
\end{equation}
$$

$$
\begin{equation}
D_j = \begin{cases}
1 & \text{, if at least one ED cover } j \\
0 & \text{, otherwise}
\end{cases}
\end{equation}
$$

$$
\begin{equation}
H_i = \begin{cases}
1 & \text{, if ED } i \text{ is selected} \\
0 & \text{, otherwise}
\end{cases}
\end{equation}
$$

Objective Function,

$$
Max\text{ }F = \sum_{j=1}^{470} d_jD_j
$$

Constraints,

$$
\sum_{i=1}^{14} t_{j,i} H_i \geq D_j,\ \forall j = 1,\dots,470
$$

$$
\sum_{i=1}^{14} H_i = m
$$

### MEXCLP Model
This model introduces probability $p$,the chance that an emergency department us unavailable.

Decision Variables,

$$
\begin{equation}
D_{ij} = \begin{cases}
1 & \text{ , if at least } i \text{ ED cover demand }j \\
0 & \text{ , if less} i \text{ ED cover demand }j
\end{cases}
\end{equation}
$$

$$
\begin{equation}
H_i = \begin{cases}
1 & \text{, if ED } i \text{ is selected} \\
0 & \text{, otherwise}
\end{cases}
\end{equation}
$$

Objective Function,

$$
Max G = \sum_{j=1}^{470} \sum_{i=1}^{14} \left(1-p\right)p^{i-1}d_jD_{ij}
$$

Constraints,

$$
\sum_{i=1}^{14} t_{j,i}H_i \geq \sum_{i=1}^{14} D_{ij} \text{ , } \forall j = 1, \dots, 470
$$

$$
\sum_{i=1}^{14} H_i = m
$$

## The Summary
![Alt Image](Optimizing-The-Number-of-Hospitals-Emergency-Department-in-Petaling-Jaya-Using-Set-Covering-Problem-Analysis.jpg)
