# IBM Q 16 Melbourne V1.x.x Version Log

**display_name**: IBM Q 16 Melbourne  
**backend_name**: ibmq\_16\_melbourne

**backend_version**: 1.x.x   
**sample_name**: albatross 

This document is a version log for the IBM Q experience **ibmq\_16\_melbourne** backend for version 1.x.x. 


# 1.0.0

**Date**: September 17, 2018

## Changes


## Device Specifications 

The connectivity map for the CNOTS in this device is
```
coupling_map = [[1,0], [1,2], [2,3], [4,3], [4,11], [5,4], [5,6], [5,10], [6,9], [8,9], [10,9], [10,11], [12,11], [12,3], [12,13], [13,2], [14,1], [14,13]]
```
Where [a,b] means a CNOT with qubit a as control and b as target can be implemented.

The following table shows some of the typical experimental parameters for this device.

| Qubit| &omega;<sup>R</sup><sub>i</sub>/2&pi; (GHz)       | &omega;<sub>i</sub>/2&pi;  (GHz)|
|----|-------------|--------|-------|--------|-------|
| **Q0**  | 6.95518 | 5.1000 | -292.8    | 125 | 345 |
| **Q1**  | 7.05693 | 5.2384 | -291.0    | 153 | 373 |
| **Q2**  | 6.97179 | 5.0328 | -289.2    | 118 | 440 |
| **Q3**  | 7.04784 | 4.8961 | -294.0    | 100 | 345 |
| **Q4**  | 6.94523 | 5.0262 | -290.7    | 81 | 545 |
| **Q5**  | 7.07587 | 5.0670 | -286.0    | 125 | 372 |
| **Q6**  | 6.95297 | 4.9237 | -289.2    | 127 | 413 |
| **Q7**  | 7.06667 | 5.0707 | -298.4    | 128 | 349 |
| **Q8**  | 6.96377 | 4.9744 | -287.6    | 120 | 321 |
| **Q9**  | 7.04930 | 4.7381 | -297.6    | 72 | 299 |
| **Q10**  | 6.96707 | 4.9633 | -291.5   | 83  | 428 |
| **Q11**  | 7.05513 | 4.9450 | -290.7   | 100 | 561 |
| **Q12**  | 6.95492 | 5.0046 | -299.0   | 81  | 550 |
| **Q13**  | 7.06722| 4.7598 | -289.8   | 108 | 398 |
| **Q14**  | 6.94433 | 4.9685 | -296.0   | 78 | 545 |
| **Q15**  | 7.07006 | 5.0025 | -289.8   | 109 | 471 |

Here is the crosstalk matrix, the error bar is less than 1 kHz for all &zeta;<sub>ij</sub> and a dash indicates an interaction strength for that pair < 5 kHz.

| &zeta;<sub>ij</sub>/2&pi; (kHz) | Q0 | Q1 | Q2 | Q3 | Q4 | Q5 | Q6 | Q7 | Q8 | Q9 | Q10 | Q11 | Q12 | Q13 | Q14 | Q15 |
|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|
| **Q0** | | -50 | - | - |	- | - | - | - | - | - | - | - | - | - | - |  |
| **Q1** | -50 | | -89 | - | - | - | - | - | - | - | - | - | - | - | -206 | - |
| **Q2** | - | -90 | | -34 | - | - | - | - | - | - | - | - | - | -147 | - | -|
| **Q3** | - | - | -34 | | -37 | - | - | - | - | - | - | - | -24 | - | - | - |
| **Q4** | - | - | - | -39 | | -8 | - | - | - | - | - | -22 | - | - | - | - |
| **Q5** | - | - | - | - |  | |  | - | - | - |  | - | - | - | - | - |
| **Q6** | - | - | - | - | - | -12 | | -41 | - | -27 | - | - | - | - | - | - |
| **Q7** | - | - | - | - | - | - | -38 | | -23 | - | - | - | - | - | - | - |
| **Q8** | - | - | - | - | - | - | - | -20 | | -58| - | - | - | - | - | - |
| **Q9** | - | - | - | - | - | - | -28 | - | -58 | | -63 | - | - | - | - | - |
| **Q10** | - | - | - | - | - | -8 | - | - | - | -65 | | -28 | - | - | - | - |
| **Q11** | - | - | - | - | -22 | - | - | - | - | - | -26 | | -33 | - | - | - |
| **Q12** | - | - | - | -25 | - | - | - | - | - | - | - | -31 | | -83 | - | - |
| **Q13** | - | - | -148 | - | - | - | - | - | - | - | - | - | -46 | | -52 | - |
| **Q14** | - | -205 | - | - | - | - | - | - | - | - | - | - | - | -53 | |  |
| **Q15** |  | - | - | - | - | - | - | - | - | - | - | - | - | - |  | |


<!--The relaxation (T<sub>1</sub>) and coherence (T<sub>2</sub>) times for each qubit are given in the following table. T<sub>1</sub> is measured with an inversion recovery experiment, and T<sub>2</sub> is measured with a Hahn echo experiment.  These values are averaged over 12 measurements each for T<sub>1</sub> and T<sub>2</sub>, performed over one week. The numbers in parentheses are the standard deviation. 

| Qubit | T<sub>1</sub> (&mu;s) | T<sub>2</sub> (&mu;s)|
|----|----|----|
| **Q0** | 37 (4) | 31 (5) |
| **Q1** | 35 (4) | 58 (10) |
| **Q2** | 48 (6) | 64 (7) |
| **Q3** | 46 (5) | 70 (15) |
| **Q4** |  49 (8) | 74 (24) |
| **Q5** | 49 (4) | 50 (5) |
| **Q6** | 44 (7) | 74 (12) |
| **Q7** | 37 (4) | 49 (7) |
| **Q8** | 49 (7) | 68 (19) |
| **Q9** | 48 (5) | 88 (14) |
| **Q10** | 28 (21) | 49 (36) |
| **Q11** | 45 (7) | 86 (16) |
| **Q12** | 50 (7) | 33 (3) |
| **Q13** | 48 (6) | 82 (12) |
| **Q14** | 36 (3) | 65 (6) |
| **Q15** | 48 (7) | 89 (17) |-->

## Gate Specification

All the GD have a gate time of 100 ns, and the gate times for all GF pulses used in CX gates are given in the table below (rounded to nearest ns). There is an additional buffer of 20 ns after each GD or GF pulse. 

| CX Gate | GF Gate Time (ns) |
|----|----|
| **CX1_0**   | 239 |
| **CX1_2**   | 174 |
| **CX2_3**   | 261 |
| **CX4_3**  | 266 |
| **CX5_4** | 300|
| **CX5_6**   | 300|
| **CX8_9**   | 220 |
| **CX10_9**   | 400 |
|**CX10_11**| 300 |
|**CX12_11**| 261 |
| **CX12_13**  | 217 |
| **CX14_13**  | 300 |
| **CX14_1**   | 652 |
| **CX13_2**   | 1086 |
| **CX12_3** | 286 |
| **CX4_11**  | 261|
| **CX5_10** | 348 |
| **CX6_9**  | 300 |

### Two Qubit Gates

The gate directions are given by the following diagram.  Gates associated with Q7 and Q15 are not calibrated due to frequency instability and crosstalk issues, respectively. 

<img src="../images/melbourne-connections.png? raw=true" height="80">