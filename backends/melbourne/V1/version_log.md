# IBM Q 16 Melbourne V1.x.x Version Log

**display_name**: IBM Q 16 Melbourne  
**backend_name**: ibmq\_16\_melbourne

**backend_version**: 1.x.x   
**sample_name**: albatross 

This document is a version log for the IBM Q experience **ibmq\_16\_melbourne** backend for version 1.x.x. 


# 1.0.0

**Date**: September 23, 2018

## Changes


## Device Specifications 

The connectivity map for the CNOTS in this device is
```
coupling_map = [[1,0], [1,2], [2,3], [4,3], [4,10], [5,4], [5,6], [5,9], [6,8], [7,8], [9,8], [9,10], [11,10], [11,3], [11,12], [12,2], [13,1], [13,12]]
```
Where [a,b] means a CNOT with qubit a as control and b as target can be implemented.

The following table shows some of the typical experimental parameters for this device.

| Qubit| &omega;<sup>R</sup><sub>i</sub>/2&pi; (GHz)       | &omega;<sub>i</sub>/2&pi;  (GHz)|
|----|-------------|--------|
| **Q0**  | 6.95518 | 5.1000 | 
| **Q1**  | 7.05693 | 5.2384 | 
| **Q2**  | 6.97179 | 5.0328 | 
| **Q3**  | 7.04784 | 4.8961 | 
| **Q4**  | 6.94523 | 5.0262 | 
| **Q5**  | 7.07587 | 5.0670 | 
| **Q6**  | 6.95297 | 4.9237 | 
| **Q7**  | 6.96377 | 4.9744 | 
| **Q8**  | 7.04930 | 4.7381 | 
| **Q9**  | 6.96707 | 4.9633 | 
| **Q10**  | 7.05513 | 4.9450 | 
| **Q11**  | 6.95492 | 5.0046 |
| **Q12**  | 7.06722| 4.7598 | 
| **Q13**  | 6.94433 | 4.9685 | 

Here is the crosstalk matrix, the error bar is less than 1 kHz for all &zeta;<sub>ij</sub> and a dash indicates an interaction strength for that pair < 5 kHz.

| &zeta;<sub>ij</sub>/2&pi; (kHz) | Q0 | Q1 | Q2 | Q3 | Q4 | Q5 | Q6 | Q7 | Q8 | Q9 | Q10 | Q11 | Q12 | Q13 |
|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|
| **Q0** | | -50 | - | - |	- | - | - | - | - | - | - | - | - | - |
| **Q1** | -50 | | -89 | - | - | - | - | - | - | - | - | - | - | -206 |
| **Q2** | - | -90 | | -34 | - | -  | - | - | - | - | - | - | -147 | - |
| **Q3** | - | - | -34 | | -37 | - | - | - | - | - | - | -24 | - | - |
| **Q4** | - | - | - | -39 | | -8 | - | - | - | - | -22 | - | - | - |
| **Q5** | - | - | - | - |  | |  | -  | - |  | - | - | - | - |
| **Q6** | - | - | - | - | - | -12 |  | - | -27 | - | - | - | - | - |
| **Q7** | - | - | - | - | - | - | -  | | -58| - | - | - | - | - |
| **Q8** | - | - | - | - | - | - | -28 | -58 | | -63 | - | - | - | - |
| **Q9** | - | - | - | - | - | -8 | -  | - | -65 | | -28 | - | - | - |
| **Q10** | - | - | - | - | -22 | - | -  | - | - | -26 | | -33 | - | - |
| **Q11** | - | - | - | -25 | - | - | -  | - | - | - | -31 | | -83 | - |
| **Q12** | - | - | -148 | - | - | - | - | - | - | - | - | -46 | | -52 |
| **Q13** | - | -205 | - | - | - | - | - | - | - | - | - | - | -53 | 


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
| **CX7_8**   | 220 |
| **CX9_8**   | 400 |
|**CX9_10**| 300 |
|**CX11_10**| 261 |
| **CX11_12**  | 217 |
| **CX13_12**  | 300 |
| **CX13_1**   | 652 |
| **CX12_2**   | 1086 |
| **CX11_3** | 286 |
| **CX4_10**  | 261|
| **CX5_9** | 348 |
| **CX6_8**  | 300 |

### Two Qubit Gates

The gate directions are given by the following diagram.  

<img src="../images/melbourne-connections.png? raw=true" height="80">