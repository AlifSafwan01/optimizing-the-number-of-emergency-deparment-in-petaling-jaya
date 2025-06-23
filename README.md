# Optimizing the Number of Hospital's Emergency Department in Petaling Jaya using Set Covering Problem Analysis

This file is a summary of my Mathematical Science project. For full article and citation, please visit Journal of Applied Mathematics and Computational Intelligence or click link [here](https://ejournal.unimap.edu.my/index.php/amci/article/view/1501/1283)

## Abstract

The emergency department (ED) has become a crucial frontline service for unscheduled patients who arrive at the hospital and need urgent attention. However, the emergency departments  is struggling to provide the service and ensure all potential demand are efficiently covered. This is proved by the previous research that, if the demand too far from the emergency department, the mortality rate will increase. Therefore, the main goal of this project is to find the least number of emergency departments needed to cover all potential demand within a certain distance.

## Project Objectives

1. Optimal Emergency Departments : Determine the optimal number of emergency departments in Petaling Jaya and its vicinity, formulating coverage for all potential demands within duration limitations.
2. Identification of Uncovered Areas : Identify areas of potential demand lacking coverage by any emergency department.
3. To analyze the behavior of the set of optimum solutions based on Maximal Covering Location Problem (MCLP) model and Maximum Expectation Covering Location Problem (MEXCLP) model.

## Methodology

Based on set covering location problems, there is three important information as follow :-
1. Emergency Department Location
2. Potential Demand Points Location
3. Travel Distance and Duration Metrics from each emergency department to each potential demands.

### Potential Demand Points and Emergency Departments Location

In total of 470 demand points collected in Petaling Jaya consist of 308 residentials, 45 industry area, 110 education area and 7 medical area.

As for hospitals that provide emergency departments, there is 14 potential hospitals that potentially cover demands in Petaling Jayaas follow :-

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

### Maximal Covering Location Problem Model Formulation
Sets,
| Set | Description |
| --- | --- |
| $H$ | Set of emergency department within and around Petaling Jaya |
| $i$ | Index of set $H$, $i = 1,...,14$ |
| $H_i$ | The $i$-th element of $H$ |
| $D$ | Set of potential demand in Petaling Jaya |
| $j$ | Index of set $D$, $j = 1,...,470$ |
| $D_j$| The $j$-th element of D |

Parameters,
| Parameter | Description |
| --- | --- |
| $d_j$| The associated population demand value at $D_j$ |
| $m$ | The number of emergency department to be located |
| $l$ | The associated travel duration |
| $T_{j,i}$ | Duration taken from $H_i$ node to $D_j$ node |

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
1 & \text{, if at least one emergency can cover demand } j \\
0 & \text{, otherwise}
\end{cases}
\end{equation}
$$

$$
\begin{equation}
H_i = \begin{cases}
1 & \text{, if the emergency department } i \text{ is chose as demand coverage} \\
0 & \text{, otherwise}
\end{cases}
\end{equation}
$$

Objective Function,

$$
Max\text{ }F = \sum_{j=1}^{470} d_jD_j
$$

Constraint,

$$
\sum_{i=1}^{14} t_{j,i} H_i \geq D_j,\ \forall j = 1,\dots,470
$$

$$
\sum_{i=1}^{14} H_i = m
$$

### Maximum Expected Covering Location Problem Model Formulation
In this model incorporates an additional parameter denoted as the probability of the emergency departments not working, $p$. In this model also aasumed that all emergency departments share the same probability of not functioning simultaneously.

Decision Variables,

$$
\begin{equation}
D_{ij} = \begin{cases}
1 & \text{ , if at least } i \text{ emergency department cover demand at node }j \\
0 & \text{ , if less} i \text{emergency department cover demand at node }j
\end{cases}
\end{equation}
$$

$$
\begin{equation}
H_i = \begin{cases}
1 & \text{, if the emergency department } i \text{ is chose as demand coverage} \\
0 & \text{, otherwise}
\end{cases}
\end{equation}
$$

Objective Function,

$$
Max G = \sum_{j=1}^{470} \sum_{i=1}^{14} \left(1-p\right)p^{i-1}d_jD_{ij}
$$

Constraint,

$$
\sum_{i=1}^{14} t_{j,i}H_i \geq \sum_{i=1}^{14} D_{ij} \text{ , } \forall j = 1, \dots, 470
$$

$$
\sum_{i=1}^{14} H_i = m
$$

## The Summary
![Alt Image](Optimizing-The-Number-of-Hospitals-Emergency-Department-in-Petaling-Jaya-Using-Set-Covering-Problem-Analysis.jpg)
