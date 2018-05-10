# IBM QX2: Sparrow

This document contains information about the IBM Q experience **ibmqx2** backend. 

## Contributors (alphabetical)
Baleegh Adbo, Lev Bishop, Markus Brink, Jerry Chow, Antonio Córcoles, Andrew Cross, Jay M. Gambetta, Oblesh Jinka, Sami Rosenblatt, Jim Rozen, Maika Takita
"../images/
## Status History 
This device went online January 24th 2017.

## Device Specifications

The connectivity map for the CNOTS in this device is
```
coupling_map = {0: [1, 2], 1: [2], 3: [2, 4], 4: [2]}
```
Where a: [b] means a CNOT with qubit a as control and b as target can be implemented.

The connectivity is provided by two coplanar waveguide (CPW) resonators with resonances around 6.0 GHz (coupling Q2, Q3 and Q4) and 6.5 GHz (coupling Q0, Q1 and Q2). Each qubit has a dedicated CPW for control and readout. The following picture shows the chip layout.


<img src="../images/ibmqx2-labeled.png?raw=true" width="320">


The following tables shows some of the main experimental parameters for this device:

| Qubit| &omega;<sup>R</sup><sub>i</sub>/2&pi; (GHz)       | &omega;<sub>i</sub>/2&pi;  (GHz)| &delta;<sub>i</sub>/2&pi; (MHz) | &chi;/2&pi; (kHz)| &kappa;/2&pi; (kHz)|
|----|-------------|--------|-------|--------|-------|
| **Q0**  | 6.530350 | 5.2723   | -330.3    | 476 | 523
| **Q1**  | 6.481848 | 5.2145   | -331.9    | 395 | 489
| **Q2**  | 6.436229 | 5.0289   | -331.2    | 428 | 415
| **Q3**  | 6.579431 | 5.2971   | -329.4    | 412 | 515
| **Q4**  | 6.530225 | 5.0561   | -335.5    | 339 | 480


where &omega;<sup>R</sup><sub>i</sub> is the resonance frequency of the readout resonator, &omega;<sub>i</sub> = (E<sub>i</sub> - E<sub>0</sub>)/&hbar; is the qubit frequency with i={00001,00010,00100,01000,10000}.  The anharmonicity (&delta;<sub>i</sub>) is the difference between the frequency of the 1-2 transition and the 0-1 transition. That is, it is given by &delta;<sub>i</sub> = (E<sub>2i</sub> - 2E<sub>i</sub>+ E<sub>0</sub> )/&hbar;.  &chi; is the qubit-cavity coupling strength, and and &kappa; is the cavity coupling to the environment (&kappa;).

Crosstalk, which we parameterize by &zeta;<sub>ij</sub> = (E<sub>i+j</sub> - E<sub>i</sub> - E<sub>j</sub> + E<sub>0</sub>)/&hbar; is measured using a **J**oint **A**mplification of **ZZ** (JAZZ) experiment, which is a modified **BI**linear **R**otational **D**ecoupling (BIRD) [^fn1]. The standard BIRD sequence used in nuclear magnetic resonance (NMR) is a Ramsey experiment on one qubit, with echo pulses on both the measured qubit (Q<sub>i</sub>) and the coupled qubit (Q<sub>j</sub>).  In the JAZZ experiment, this sequence is performed twice, for each initial state of the coupled qubit. Additionally, the phase of the final &pi;/2-rotation is varied in order to detect an oscillating signal. &zeta;<sub>ij</sub> is equal to the frequency difference found between the two experiments.  The JAZZ experiment is shown in the figure below, and the measurements of all &zeta;<sub>ij</sub> are in the following table. The GD pulse notation is defined below in the Gate Specification section.  

[^fn1]: J.R. Garbow, D.P. Weitekamp, A. Pines, Bilinear rotation decoupling of homonuclear scalar interactions, Chemical Physics Letters, Volume 93, Issue 5, 1982, Pages 504-509.

<img src="../images/zz_sequence.png?raw=true" width="400">


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

## Experimental Setup
The following cartoon shows a depiction of the device I/O microwave setup:

<img src="../images/Ibmqx2-expsetup.png?raw=true" width="320">

## Gate Specification

 
<img src="../images/gatedef_U1U2U3_CNOT.png?raw=true" width="320">

A frame change (FC) is equivalent to applying a virtual *Z*-gate in software, where *Z*(&theta;)=FC(-&theta;). Gaussian derivative (GD) and Gaussian flattop (GF) pulses are defined with amplitude and angle parameters.

All the GD has a gate time of 83ns and the gate time of GF are {167, 150, 208, 145, 133, 133} ns for {CX0\_1, CX0\_2, CX1\_2, CX3\_2, CX3\_4, CX4\_2} respectively. There is an additional buffer of 7ns after each GD or GF pulse. 


### Two-Qubit Gates
All currently calibrated two-qubit gates and their directions are defined in the coupling map and shown in the device picture below.  Generally, two-qubit gates are possible between neighboring qubits that are connected by a superconducting bus resonator.  The IBM Q experience uses the cross-resonance interaction as the basis for the CX-gate.  This interaction is stronger when choosing the qubit with higher frequency to be the control qubit, and the lower frequency qubit to be the target, so the frequencies of the qubits determines the direction of the gate.  

<img src="../images/ibmqx2-connections.png?raw=true" width="320">

Reported gate errors are measured using simultaneous randomized benchmarking (RB)[^fn2]. RB gives the average error per Clifford gate, which we convert to error per gate according to the set of primitive gates used on QX2.

[^fn2]: Jay M. Gambetta, A. D. Córcoles, S. T. Merkel, B. R. Johnson, John A. Smolin, Jerry M. Chow, Colm A. Ryan, Chad Rigetti, S. Poletto, Thomas A. Ohki, Mark B. Ketchen, and M. Steffen, Characterization of Addressability by Simultaneous Randomized Benchmarking, *Phys. Rev. Lett.* 109, 240504.
