# IBM Q 5 Tenerife V1.x.x Version Log

**display_name**: IBM Q 5 Tenerife  
**backend_name**: ibmqx4  
**backend_version**: 1.x.x   
**sample_name**: Raven 

This document is a version log for the IBM Q experience **ibmqx4** backend for version 1.x.x. 

# 1.3.0

**Date**: July 5, 2018

## Changes

Device underwent a thermal cycle to room temperature and back to 20 mK.

# 1.2.0

**Date**: April 19, 2018

## Changes

Device connectivity changed with respect to 1.1.0: CR2\_4 became CR4\_2

## Device Specifications

The connectivity map for the CNOTS in this device is
```
coupling_map = [[1,0],[2,0],[2,1],[3,2],[3,4],[4,2]]
```
Where [a,b] means a CNOT with qubit a as control and b as target can be implemented.

## Gate Specification
 
All the GD has a gate time of 60ns and the gate time of GF are {110, 152, 200, 250, 150, 400} ns for {CX1\_0, CX2\_0, CX2\_1, CX3\_2, CX3\_4, CX4\_2} respectively. There is an additional buffer of 10ns after each GD or GF pulse. 

### Two-Qubit Gates

The gate directions are given by the following diagram.  

<img src="../images/ibmqx4-connections_1pt2pt0.png?raw=true" width="320">




# 1.1.0

**Date**: November 12, 2017

## Changes

Warmed up and cooled down. Device connectivity the same as V1.0.0

## Device Specification

The following tables shows some of the main experimental parameters for this device:

| Qubit| &omega;<sup>R</sup><sub>i</sub>/2&pi; (GHz)| &omega;<sub>i</sub>/2&pi;  (GHz)| 
|----|-------------|--------|
| **Q0**  | 6.52396 | 5.2447   | 
| **Q1**  | 6.48078 | 5.3048   | 
| **Q2**  | 6.43875 | 5.3519   | 
| **Q3**  | 6.58041 | 5.4303   | 
| **Q4**  | 6.52698 | 5.1839   | 

The relaxation (T<sub>1</sub>) and coherence (T<sub>2</sub>) times for each qubit are given in the following table. T<sub>2</sub> is measured with a Hahn echo experiment. These values are averaged over 101 measurements performed between November and December 2017. The numbers in parentheses are standard errors of the mean.

| \ |  Q0 |   Q1|  Q2 |Q3   |  Q4 |
|:-:|---|---|---|---|---|
|   T<sub>1</sub> (us) | 48.81 (0.68) |  50.24 (0.66)| 42.52 (0.51)| 40.09 (0.94) |  55.52 (0.96)|
|   T<sub>2</sub> (us)| 28.09 (0.41)  | 60.24 (1.12) | 34.92 (0.51)| 14.24 (0.21) | 27.09 (0.37) |


# 1.0.0

**Date**: September 25, 2017

## Device Specifications

The connectivity map for the CNOTS in this device is
```
coupling_map = [[1,0],[2,0],[2,1],[2,4],[3,2],[3,4]]
```
Where [a,b] means a CNOT with qubit a as control and b as target can be implemented.

The following tables show typical experimental parameters for this device (This particular set was taken for V1.0.0; see the version log for specific parameters):

| Qubit| &omega;<sup>R</sup><sub>i</sub>/2&pi; (GHz)       | &omega;<sub>i</sub>/2&pi;  (GHz)| &delta;<sub>i</sub>/2&pi; (MHz) | &chi;/2&pi; (kHz)| &kappa;/2&pi; (kHz)|
|----|-------------|--------|-------|--------|-------|
| **Q0**  | 6.52396 | 5.2461   | -330.1    | 410 | -
| **Q1**  | 6.48078 | 5.3025   | -329.7    | 512 | -
| **Q2**  | 6.43875 | 5.3562   | -323.0    | 408 | -
| **Q3**  | 6.58036 | 5.4317   | -327.9    | 434 | -
| **Q4**  | 6.52698 | 5.1824   | -332.5    | 458 | -


where &omega;<sup>R</sup><sub>i</sub> is the resonance frequency of the readout resonator, &omega;<sub>i</sub> = (E<sub>i</sub> - E<sub>0</sub>)/&hbar; is the qubit frequency with i={00001,00010,00100,01000,10000}.  The anharmonicity (&delta;<sub>i</sub>) is the difference between the frequency of the 1-2 transition and the 0-1 transition. That is, it is given by &delta;<sub>i</sub> = (E<sub>2i</sub> - 2E<sub>i</sub>+ E<sub>0</sub> )/&hbar;.  &chi; is the qubit-cavity coupling strength, and &kappa; is the cavity coupling to the environment (&kappa;).

In the crosstalk matrix, the error bar is less than 1 kHz for all &zeta;<sub>ij</sub> and a dash indicates an interaction strength for that pair < 25 kHz.


| &zeta;<sub>ij</sub>/2&pi; (kHz)  |  Q0 |   Q1|  Q2 |Q3   |  Q4 |
|:-:|---|---|---|---|---|
|   **Q0**|  X |  -43 | -72  |  - |  - |
|   **Q1**|  -41 |  X | -16  |  - |  - |
|   **Q2**| -73  |  -18 |  X | -52  | -90  |
|   **Q3**|  - |  - |  -51 |  X |  -175 |
|   **Q4**|  - |  - |  -89 |  -176 | X  |
 

The relaxation (T<sub>1</sub>) and coherence (T<sub>2</sub>) times for each qubit are given in the following table. T<sub>2</sub> is measured with a Hahn echo experiment. These values are from single measurement on September 25, 2017. 

| \ |  Q0 |   Q1|  Q2 |Q3   |  Q4 |
|:-:|---|---|---|---|---|
|   T<sub>1</sub> (us) | 35.2 |  57.5 | 36.6 | 43.0 |  49.5|
|   T<sub>2</sub> (us)| 38.1  | 40.5 | 54.8 | 42.1 | 19.2 |

## Gate Specification

All the GD has a gate time of 50ns and the gate time of GF are {110, 110, 135, 160, 125, 100} ns for {CX1\_0, CX2\_0, CX2\_1, CX2\_4, CX3\_2, CX3\_4} respectively. There is an additional buffer of 10ns after each GD or GF pulse. 

### Two-Qubit Gates

The gate directions are given by the following diagram.  

<img src="../images/ibmqx4-connections.png?raw=true" width="320">

