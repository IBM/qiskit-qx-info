# IBM QX2 V1.x.x Version Log

**backend_name**: ibmqx2  
**backend_version**: 1.x.x   
**sample_name**: sparrow 

This document is a version log for the IBM Q experience **ibmqx2** backend for version 1.x.x. 

# 1.1.1

**Date**: April 25, 2018 9:00 AM

## Changes

Improved readout fidelity for Q2. All other specifications the same as V1.1.0

# 1.1.0

**Date**: December 12, 2017

## Changes

Warmed up and cooled down. Device connectivity the same as V1.0.0

## Device Specification

The following tables shows some of the main experimental parameters for this device:

| Qubit| &omega;<sup>R</sup><sub>i</sub>/2&pi; (GHz)| &omega;<sub>i</sub>/2&pi;  (GHz)| 
|----|-------------|--------|
| **Q0**  | 6.53051 | 5.2760   | 
| **Q1**  | 6.48165 | 5.2122   | 
| **Q2**  | 6.43617 | 5.0154   | 
| **Q3**  | 6.57952 | 5.2805   | 
| **Q4**  | 6.53023 | 5.0711   | 

The relaxation (T<sub>1</sub>) and coherence (T<sub>2</sub>) times for each qubit are given in the following table. T<sub>2</sub> is measured with a Hahn echo experiment. These values are averaged over 75 measurements performed between December 2017 and May 2018. The numbers in parentheses are standard errors of the mean.

| \ |  Q0 |   Q1|  Q2 |Q3   |  Q4 |
|:-:|---|---|---|---|---|
|   T<sub>1</sub> (us) | 47.17 (1.20) |  44.93 (1.15)| 56.15 (0.70)| 50.20 (0.71) |  64.48 (1.20)|
|   T<sub>2</sub> (us)| 39.71 (1.50)  | 37.71 (1.75) | 53.33 (0.91)| 52.61 (1.45) | 39.12 (1.18) |

## Gate Specification
 
All the GD has a gate time of 83ns and the gate time of GF are {190, 170, 230, 170, ,150, 240} ns for {CX0\_1, CX0\_2, CX1\_2, CX3\_2, CX3\_4, CX4\_2} respectively. There is an additional buffer of 7ns after each GD or GF pulse. 

# 1.0.0

**Date**: January 24, 2017

## Device Specifications

The connectivity map for the CNOTS in this device is
```
coupling_map = [[0,1],[0,2],[1,2],[3,2],[3,4],[4,2]]
```
Where a: [b] means a CNOT with qubit a as control and b as target can be implemented.

The following tables show typical experimental parameters for this device (This particular set was taken for V1.0.0; see the version log for specific parameters):

| Qubit| &omega;<sup>R</sup><sub>i</sub>/2&pi; (GHz)       | &omega;<sub>i</sub>/2&pi;  (GHz)| &delta;<sub>i</sub>/2&pi; (MHz) | &chi;/2&pi; (kHz)| &kappa;/2&pi; (kHz)|
|----|-------------|--------|-------|--------|-------|
| **Q0**  | 6.530350 | 5.2723   | -330.3    | 476 | 523
| **Q1**  | 6.481848 | 5.2145   | -331.9    | 395 | 489
| **Q2**  | 6.436229 | 5.0289   | -331.2    | 428 | 415
| **Q3**  | 6.579431 | 5.2971   | -329.4    | 412 | 515
| **Q4**  | 6.530225 | 5.0561   | -335.5    | 339 | 480


where &omega;<sup>R</sup><sub>i</sub> is the resonance frequency of the readout resonator, &omega;<sub>i</sub> = (E<sub>i</sub> - E<sub>0</sub>)/&hbar; is the qubit frequency with i={00001,00010,00100,01000,10000}.  The anharmonicity (&delta;<sub>i</sub>) is the difference between the frequency of the 1-2 transition and the 0-1 transition. That is, it is given by &delta;<sub>i</sub> = (E<sub>2i</sub> - 2E<sub>i</sub>+ E<sub>0</sub> )/&hbar;.  &chi; is the qubit-cavity coupling strength, and and &kappa; is the cavity coupling to the environment (&kappa;).

In the crosstalk matrix, the error bar is less than 1 kHz for all &zeta;<sub>ij</sub> and a dash indicates an interaction strength for that pair < 25 kHz.


| &zeta;<sub>ij</sub>/2&pi; (kHz)  |  Q0 |   Q1|  Q2 |Q3   |  Q4 |
|:-:|---|---|---|---|---|
|   **Q0**|  X |  -43 | -83  |  - |  - |
|   **Q1**|  -45 |  X | -25  |  - |  - |
|   **Q2**| -83  |  -27 |  X | -127  | -38  |
|   **Q3**|  - |  - |  -127 |  X |  -97 |
|   **Q4**|  - |  - |  -34 |  -97 | X  |
 

The relaxation (T<sub>1</sub>) and coherence (T<sub>2</sub>) times for each qubit are given in the following table. T<sub>2</sub> is measured with a Hahn echo experiment. These values are averaged over 100 measurements each, spaced approximately by 12 hours, and performed between March and May 2017. The numbers in parentheses are standard errors of the mean.

| \ |  Q0 |   Q1|  Q2 |Q3   |  Q4 |
|:-:|---|---|---|---|---|
|   T<sub>1</sub> (us) | 53.04 (0.64) |  63.94 (1.06)| 52.08 (0.58) | 51.78 (0.55) |  55.80 (0.95)|
|   T<sub>2</sub> (us)| 48.50 (2.63)  | 35.07 (0.59) | 89.73 (1.82) | 60.93 (1.09) | 84.18 (2.41) |

## Gate Specification

All the GD has a gate time of 83ns and the gate time of GF are {167, 150, 208, 145, 133, 133} ns for {CX0\_1, CX0\_2, CX1\_2, CX3\_2, CX3\_4, CX4\_2} respectively. There is an additional buffer of 7ns after each GD or GF pulse. 



