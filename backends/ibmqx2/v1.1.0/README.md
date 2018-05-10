# ibm5Q_1.1.0 [ibmqx2]: Sparrow

This document contains information about the IBM Q experience **ibm5Q_1.1.0** backend. 

## Contributors (alphabetical)
Baleegh Adbo, Lev Bishop, Markus Brink, Jerry Chow, Antonio Córcoles, Andrew Cross, Jay M. Gambetta, Oblesh Jinka, Abhinav Kandala, Sami Rosenblatt, Jim Rozen, Maika Takita

## Status History 
This device went online December 12th 2017.

## Device Specifications

The connectivity map for the CNOTS in this device is
```
coupling_map = {0: [1, 2], 1: [2], 3: [2, 4], 4: [2]}
```
Where a: [b] means a CNOT with qubit a as control and b as target can be implemented.

The connectivity is provided by two coplanar waveguide (CPW) resonators with resonances around 6.0 GHz (coupling Q2, Q3 and Q4) and 6.5 GHz (coupling Q0, Q1 and Q2). Each qubit has a dedicated CPW for control and readout. The following picture shows the chip layout.


<img src="../images/ibmqx2-labeled.png?raw=true" width="320">


The following tables shows some of the main experimental parameters for this device:

| Qubit| &omega;<sup>R</sup><sub>i</sub>/2&pi; (GHz)       | &omega;<sub>i</sub>/2&pi;  (GHz)| 
|----|-------------|--------|-------|--------|-------|
| **Q0**  | 6.53051 | 5.2760   | 
| **Q1**  | 6.48165 | 5.2122   | 
| **Q2**  | 6.43617 | 5.0154   | 
| **Q3**  | 6.57952 | 5.2805   | 
| **Q4**  | 6.53023 | 5.0711   | 


where &omega;<sup>R</sup><sub>i</sub> is the resonance frequency of the readout resonator, &omega;<sub>i</sub> = (E<sub>i</sub> - E<sub>0</sub>)/&hbar; is the qubit frequency with i={00001,00010,00100,01000,10000}.  The anharmonicity (&delta;<sub>i</sub>) is the difference between the frequency of the 1-2 transition and the 0-1 transition. That is, it is given by &delta;<sub>i</sub> = (E<sub>2i</sub> - 2E<sub>i</sub>+ E<sub>0</sub> )/&hbar;. The anharmonicity of the qubits is ~ 330 MHz. 


The relaxation (T<sub>1</sub>) and coherence (T<sub>2</sub>) times for each qubit are given in the following table. T<sub>2</sub> is measured with a Hahn echo experiment. These values are averaged over 75 measurements performed between December 2017 and May 2018. The numbers in parentheses are standard errors of the mean.

| \ |  Q0 |   Q1|  Q2 |Q3   |  Q4 |
|:-:|---|---|---|---|---|
|   T<sub>1</sub> (us) | 47.17 (1.20) |  44.93 (1.15)| 56.15 (0.70)| 50.20 (0.71) |  64.48 (1.20)|
|   T<sub>2</sub> (us)| 39.71 (1.50)  | 37.71 (1.75) | 53.33 (0.91)| 52.61 (1.45) | 39.12 (1.18) |

## Experimental Setup
The following cartoon shows a depiction of the device I/O microwave setup:

<img src="../images/Ibmqx2-expsetup.png?raw=true" width="320">

## Gate Specification

 
<img src="../images/gatedef_U1U2U3_CNOT.png?raw=true" width="320">

A frame change (FC) is equivalent to applying a virtual *Z*-gate in software, where *Z*(&theta;)=FC(-&theta;). Gaussian derivative (GD) and Gaussian flattop (GF) pulses are defined with amplitude and angle parameters.

All the GD has a gate time of 83ns and the gate time of GF are {190, 170, 230, 170, ,150, 240} ns for {CX0\_1, CX0\_2, CX1\_2, CX3\_2, CX3\_4, CX4\_2} respectively. There is an additional buffer of 7ns after each GD or GF pulse. 


### Two-Qubit Gates
All currently calibrated two-qubit gates and their directions are defined in the coupling map and shown in the device picture below.  Generally, two-qubit gates are possible between neighboring qubits that are connected by a superconducting bus resonator.  The IBM Q experience uses the cross-resonance interaction as the basis for the CX-gate.  This interaction is stronger when choosing the qubit with higher frequency to be the control qubit, and the lower frequency qubit to be the target, so the frequencies of the qubits determines the direction of the gate.  

<img src="../images/ibmqx2-connections.png?raw=true" width="320">

Reported gate errors are measured using simultaneous randomized benchmarking (RB)[^fn2]. RB gives the average error per Clifford gate, which we convert to error per gate according to the set of primitive gates used on QX2.

[^fn2]: Jay M. Gambetta, A. D. Córcoles, S. T. Merkel, B. R. Johnson, John A. Smolin, Jerry M. Chow, Colm A. Ryan, Chad Rigetti, S. Poletto, Thomas A. Ohki, Mark B. Ketchen, and M. Steffen, Characterization of Addressability by Simultaneous Randomized Benchmarking, *Phys. Rev. Lett.* 109, 240504.
