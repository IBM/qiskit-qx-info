# IBM Q 16 Rueschlikon V1.x.x Version Log

**display_name**: IBM Q 16 Rueschlikon
**backend_name**: ibmqx5  
**backend_version**: 1.x.x   
**sample_name**: albatross 

This document is a version log for the IBM Q experience **ibmqx5** backend for version 1.x.x. 

This device was formally **ibmqx3** for V1.0.0.

# 1.1.0

**Date**: September 28, 2017

## Changes

Device connectivity changed with respect to 1.1.0: CR2\_4 became CR4\_2

## Device Specifications 

The connectivity map for the CNOTS in this device is
```
coupling_map = {1:[0,2], 2:[3], 3:[4, 14], 5:[4], 6:[5,7,11], 7:[10], 8:[7],9:[8, 10], 11:[10], 12:[5, 11, 13], 13:[4, 14], 15:[0, 2, 14]}
```
Where a: [b] means a CNOT with qubit a as control and b as target can be implemented.

The connectivity is provided by total 22 coplanar waveguide (CPW) "bus" resonators, each of which connects two qubits. The connectivity configuration is shown in the figure below; the colored dots indicate qubits, and the colored bars indicate CPW bus resonators. Three different resonant frequencies are used for the bus resonators. The white bars indicate the buses with a resonant frequency of 6.25 GHz, the grey bars 6.45 GHz, and the black bars 6.65 GHz.    

<img src="images/ibmqx3-bus.png?raw=true" width="750">

Each qubit has a dedicated CPW readout resonator attached (labeled as R) for control and readout. The following picture shows the chip layout.

<img src="images/ibmqx3-labeled.png?raw=true" width="320">

The following table shows some of the typical experimental parameters for this device (for V1.1.0).

| Qubit| &omega;<sup>R</sup><sub>i</sub>/2&pi; (GHz)       | &omega;<sub>i</sub>/2&pi;  (GHz)| &delta;<sub>i</sub>/2&pi; (MHz) | &chi;/2&pi; (kHz)| &kappa;/2&pi; (kHz)|
|----|-------------|--------|-------|--------|-------|
| **Q0**  | 6.9745 | 5.2561 | -292.8    | 125 | 345 |
| **Q1**  | 6.8667 | 5.3961 | -291.0    | 153 | 373 |
| **Q2**  | 6.96087 | 5.2756 | -289.2    | 118 | 440 |
| **Q3**  | 6.87813 | 5.0831 | -294.0    | 100 | 345 |
| **Q4**  | 6.95278 | 4.9791 | -290.7    | 81 | 545 |
| **Q5**  | 6.85144 | 5.1513 | -286.0    | 125 | 372 |
| **Q6**  | 6.98235 | 5.3058 | -289.2    | 127 | 413 |
| **Q7**  | 6.85953 | 5.2528 | -298.4    | 128 | 349 |
| **Q8**  | 6.97061 | 5.1153 | -287.6    | 120 | 321 |
| **Q9**  | 6.87244 | 5.1555 | -297.6    | 72 | 299 |
| **Q10**  | 6.95882 | 5.0426 | -291.5   | 83  | 428 |
| **Q11**  | 6.87644 | 5.1107 | -290.7   | 100 | 561 |
| **Q12**  | 6.96631 | 4.9466 | -299.0   | 81  | 550 |
| **Q13**  | 6.86321| 5.0881 | -289.8   | 108 | 398 |
| **Q14**  | 6.97820 | 4.8701 | -296.0   | 78 | 545 |
| **Q15**  | 6.85637 | 5.1095 | -289.8   | 109 | 471 |

where &omega;<sup>R</sup><sub>i</sub> is the resonance frequency of the readout resonator, &omega;<sub>i</sub> = (E<sub>i</sub> - E<sub>0</sub>)/&hbar; is the qubit frequency with i={0...1,0...10,...,01...0,1...0}.  The anharmonicity (&delta;<sub>i</sub>) is the difference between the frequency of the 1-2 transition and the 0-1 transition. That is, it is given by &delta;<sub>i</sub> = (E<sub>2i</sub> - 2E<sub>i</sub>+ E<sub>0</sub> )/&hbar;.  &chi; is the qubit-cavity coupling strength, and and &kappa; is the cavity coupling to the environment (&kappa;).

Crosstalk, which we parameterize by &zeta;<sub>ij</sub> = (E<sub>i+j</sub> - E<sub>i</sub> - E<sub>j</sub> + E<sub>0</sub>)/&hbar; is measured using a **J**oint **A**mplification of **ZZ** (JAZZ) experiment, which is a modified **BI**linear **R**otational **D**ecoupling (BIRD) [^fn1]. The standard BIRD sequence used in nuclear magnetic resonance (NMR) is a Ramsey experiment on one qubit, with echo pulses on both the measured qubit (Q<sub>i</sub>) and the coupled qubit (Q<sub>j</sub>).  In the JAZZ experiment, this sequence is performed twice for each initial state of the coupled qubit. Additionally, the phase of the final &pi;/2-rotation is varied in order to detect an oscillating signal. &zeta;<sub>ij</sub> is equal to the frequency difference found between the two experiments.  The JAZZ experiment is shown in the figure below, and the measurements of all &zeta;<sub>ij</sub> are in the following table.  The GD pulse notation is defined below in the Gate Specification section.

[^fn1]: J.R. Garbow, D.P. Weitekamp, A. Pines, Bilinear rotation decoupling of homonuclear scalar interactions, *Chemical Physics Letters*, Volume 93, Issue 5, 1982, Pages 504-509.

<img src="images/zz_sequence.png?raw=true" width="400">

Here is a typical crosstalk matrix (for V1.1.0), the error bar is less than 1 kHz for all &zeta;<sub>ij</sub> and a dash indicates an interaction strength for that pair < 5 kHz.

| &zeta;<sub>ij</sub>/2&pi; (kHz) | Q0 | Q1 | Q2 | Q3 | Q4 | Q5 | Q6 | Q7 | Q8 | Q9 | Q10 | Q11 | Q12 | Q13 | Q14 | Q15 |
|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|
| **Q0** | | -43 | - | - |	- | - | - | - | - | - | - | - | - | - | - | -63 |
| **Q1** | -46 | | -75 | - | - | - | - | - | - | - | - | - | - | - | - | - |
| **Q2** | - | -74 | | -96 | - | - | - | - | - | - | - | - | - | - | - | -53 |
| **Q3** | - | - | -95 | | -37 | - | - | - | - | - | - | - | - | - | -51 | - |
| **Q4** | - | - | - | -38 | | -60 | - | - | - | - | - | - | - | -27 | - | - |
| **Q5** | - | - | - | - | -62 | | -78 | - | - | - | - | - | -54 | - | - | - |
| **Q6** | - | - | - | - | - | -76 | | -55 | - | - | - | -66 | - | - | - | - |
| **Q7** | - | - | - | - | - | - | -60 | | -58 | - | -69 | - | - | - | - | - |
| **Q8** | - | - | - | - | - | - | - | -69 | | -26| - | - | - | - | - | - |
| **Q9** | - | - | - | - | - | - | - | - | -25 | | -40 | - | - | - | - | - |
| **Q10** | - | - | - | - | - | - | - | -71 | - | -43 | | -28 | - | - | - | - |
| **Q11** | - | - | - | - | - | - | -68 | - | - | - | -42 | | -51 | - | - | - |
| **Q12** | - | - | - | - | - | -51 | - | - | - | - | - | -50 | | -43 | - | - |
| **Q13** | - | - | - | - | -27 | - | - | - | - | - | - | - | -46 | | -74 | - |
| **Q14** | - | - | - | -50 | - | - | - | - | - | - | - | - | - | -69 | | -103 |
| **Q15** | -61 | - | -55 | - | - | - | - | - | - | - | - | - | - | - | -106 | 


The relaxation (T<sub>1</sub>) and coherence (T<sub>2</sub>) times for each qubit are given in the following table. T<sub>1</sub> is measured with an inversion recovery experiment, and T<sub>2</sub> is measured with a Hahn echo experiment.  These values are averaged over 12 measurements each for T<sub>1</sub> and T<sub>2</sub>, performed over one week. The numbers in parentheses are the standard deviation. 

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
| **Q15** | 48 (7) | 89 (17) |

## Gate Specification

All the GD have a gate time of 80 ns, and the gate times for all GF pulses used in CX gates are given in the table below (rounded to nearest ns). There is an additional buffer of 10 ns after each GD or GF pulse. 

| CX Gate | GF Gate Time (ns) |
|----|----|
| **CX1_0**   | 391 |
| **CX1_2**   | 260 |
| **CX2_3**   | 230 |
| **CX3_4**  | 252 |
| **CX3_14** | 326|
| **CX5_4**   | 267|
| **CX6_5**   | 261 |
| **CX6_7**   | 170 |
|**CX6_11**| 174 |
|**CX7_10**| 289 |
| **CX8_7**  | 265 |
| **CX9_8**  | 174 |
| **CX9_10**   | 209 |
| **CX11_10**   | 196 |
| **CX12_5** | 339 |
| **CX12_11**  | 213|
| **CX12_13** | 244 |
| **CX13_4**  | 240 |
| **CX13_14**  | 205 |
| **CX15_0** | 361 |
| **CX15_2**  | 270 |
| **CX15_14** | 196 |

## Two Qubit Gates

All currently calibrated two-qubit gates and their directions are defined in the coupling map, and are shown in the device picture below.  

<img src="images/IBMQX5_connections_full.png? raw=true" height="200">

# 1.0.0

**Date**: June, 2017

## Changes

Initial device online. In this version the device was backend **ibmqx3**

## Device Specifications

The connectivity map for the CNOTS in this device is
```
coupling_map = {0:[1], 1: [2], 2: [3], 3: [14], 4: [3, 5], 6: [7, 11], 7: [10], 8: [7], 9: [8, 10], 11: [10], 12: [5, 11, 13], 13: [4, 14], 15: [0, 14]}
```
Where a: [b] means a CNOT with qubit a as control and b as target can be implemented.

The following table shows some of the main experimental parameters for this device.

| Qubit| &omega;<sup>R</sup><sub>i</sub>/2&pi; (GHz)       | &omega;<sub>i</sub>/2&pi;  (GHz)| &delta;<sub>i</sub>/2&pi; (MHz) | &chi;/2&pi; (kHz)| &kappa;/2&pi; (kHz)|
|----|-------------|--------|-------|--------|-------|
| **Q0**  | 6.97422 | 5.2488 | -292.8    | 130 | 360 |
| **Q1**  | 6.86632 | 5.3795 | -291.0    | 155 | 520 |
| **Q2**  | 6.96126 | 5.2683 | -289.2    | 115 | 470 |
| **Q3**  | 6.87780 | 5.0665 | -294.0    | 100 | 410 |
| **Q4**  | 6.95389 | 4.9725 | -290.7    | 90  | 430 |
| **Q5**  | 6.85116 | 5.1427 | -286.0    | 100 | 520 |
| **Q6**  | 6.98277 | 5.2956 | -289.2    | 105 | 410 |
| **Q7**  | 6.85933 | 5.2490 | -298.4    | 135 | 540 |
| **Q8**  | 6.97074 | 5.0967 | -287.6    | 120 | 450 |
| **Q9**  | 6.87252 | 5.1463 | -297.6    | 135 | 480 |
| **Q10**  | 6.95874 | 5.0301 | -291.5   | 95  | 530 |
| **Q11**  | 6.87590 | 5.1068 | -290.7   | 105 | 620 |
| **Q12**  | 6.96597 | 4.9383 | -299.0   | 95  | 450 |
| **Q13**  | 6.86325 | 5.0807 | -289.8   | 115 | 480 |
| **Q14**  | 6.97800 | 4.8442 | -296.0   | 80  | 390 |
| **Q15**  | 6.85608 | 5.0842 | -289.8   | 135 | 430 |

The crosstalk matrix, the error bar is less than 1 kHz for all &zeta;<sub>ij</sub> and a dash indicates an interaction strength for that pair < 5 kHz.

| &zeta;<sub>ij</sub>/2&pi; (kHz) | Q0 | Q1 | Q2 | Q3 | Q4 | Q5 | Q6 | Q7 | Q8 | Q9 | Q10 | Q11 | Q12 | Q13 | Q14 | Q15 |
|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|
| **Q0** | | -46 | - | - |	- | - | - | - | - | - | - | - | - | - | - | -62 |
| **Q1** | -46 | | -70 | - | - | - | - | - | - | - | - | - | - | - | - | - |
| **Q2** | - | -74 | | -101 | - | - | - | - | - | - | - | - | - | - | - | -52 |
| **Q3** | - | - | -98 | | -31 | - | - | - | - | - | - | - | - | - | -57 | - |
| **Q4** | - | - | - | -34 | | -59 | - | - | - | - | - | - | - | -25 | - | - |
| **Q5** | - | - | - | - | -62 | | -75 | - | - | - | - | - | -53 | - | - | - |
| **Q6** | - | - | - | - | - | -74 | | -60 | - | - | - | -63 | - | - | - | - |
| **Q7** | - | - | - | - | - | - | -60 | | -64 | - | -78 | - | - | - | - | - |
| **Q8** | - | - | - | - | - | - | - | -65 | | -22 | - | - | - | - | - | - |
| **Q9** | - | - | - | - | - | - | - | - | -22 | | -39 | - | - | - | - | - |
| **Q10** | - | - | - | - | - | - | - | -77 | - | -37 | | -43 | - | - | - | - |
| **Q11** | - | - | - | - | - | - | -63 | - | - | - | -41 | | -53 | - | - | - |
| **Q12** | - | - | - | - | - | -55 | - | - | - | - | - | -53 | | -46 | - | - |
| **Q13** | - | - | - | - | -26 | - | - | - | - | - | - | - | -46 | | -96 | - |
| **Q14** | - | - | - | -58 | - | - | - | - | - | - | - | - | - | -95 | | -109 |
| **Q15** | -66 | - | -53 | - | - | - | - | - | - | - | - | - | - | - | -111 | 


The relaxation (T<sub>1</sub>) and coherence (T<sub>2</sub>) times for each qubit are given in the following table. T<sub>1</sub> is measured with an inversion recovery experiment, and T<sub>2</sub> is measured with a Hahn echo experiment.  These values are averaged over 50 measurements each for T<sub>1</sub> and 30 measurements for T<sub>2</sub>, performed over one week. The numbers in parentheses are standard errors of the mean.

| Qubit | T<sub>1</sub> (&mu;s) | T<sub>2</sub> (&mu;s)|
|----|----|----|
| **Q0** | 39.85 (0.69) | 34.97 (0.55) |
| **Q1** | 33.03 (0.31) | 60.63 (1.61) |
| **Q2** | 44.58 (0.76) | 48.79 (1.05) |
| **Q3** | 52.9 (0.66) | 77.8 (2.05) |
| **Q4** | 42.44 (0.48) | 78.74 (1.18) |
| **Q5** | 46.4 (0.91) | 76.89 (2.07) |
| **Q6** | 42.8 (0.7) | 28.96 (0.46) |
| **Q7** | 33.07 (0.54) | 50.53 (1.16) |
| **Q8** | 45.99 (0.67) | 72.51 (1.41) |
| **Q9** | 43.59 (0.61) | 69.14 (1.59) |
| **Q10** | 51.7 (0.99) | 70.93 (2.4) |
| **Q11** | 47.52 (0.69) | 54.33 (1.02) |
| **Q12** | 25.24 (0.31) | 32.63 (1.09) |
| **Q13** | 45.94 (0.49) | 61.26 (0.99) |
| **Q14** | 49.78 (0.79) | 43.04 (0.94) |
| **Q15** | 36.93 (1.81) | 45.72 (1.86) |


## Gate Specification

All the GD have a gate time of 80 ns, and the gate times for all GF pulses used in CX gates are given in the table below. There is an additional buffer of 10 ns after each GD or GF pulse. 

| CX Gate | GF Gate Time (ns) |
|----|----|
| **CX0_1**   | 209 |
| **CX1_2**   | 260 |
| **CX2_3**   | 230 |
| **CX3_14**  | 348 |
| **CX4_3**   | 304 |
| **CX4_5**   | 310 |
| **CX6_7**   | 170 |
| **CX6_11**  | 174 |
| **CX7_10**  | 187 |
| **CX8_7**   | 265 |
| **CX9_8**   | 239 |
| **CX9_10**  | 283 |
| **CX11_10** | 196 |
| **CX12_5**  | 270 |
| **CX12_11** | 183 |
| **CX12_13** | 191 |
| **CX13_4**  | 240 |
| **CX13_14** | 205 |
| **CX15_0**  | 348 |
| **CX15_14** | 183 |


### Two-Qubit Gates

The gate directions are given by the following diagram.  

<img src="images/ibmqx3-connections.png?raw=true" height="600">



