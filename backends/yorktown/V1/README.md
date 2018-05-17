# IBM Q 5 Yorktown V1.x.x

**display_name**: IBM Q 5 Yorktown  
**backend_name**: ibmqx2  
**backend_version**: 1.x.x   
**sample_name**: sparrow 

This document contains information about the IBM Q experience **ibmqx2** backend for version 1.x.x. 

## Contributors (alphabetical)
Baleegh Adbo, Lev Bishop, Markus Brink, Jerry Chow, Antonio Córcoles, Andrew Cross, Jay M. Gambetta, Oblesh Jinka, Abhinav Kandala, Sami Rosenblatt, Jim Rozen, Maika Takita

## Device Specifications

The connectivity is provided by two coplanar waveguide (CPW) resonators with resonances around 6.0 GHz (coupling Q2, Q3 and Q4) and 6.5 GHz (coupling Q0, Q1 and Q2). Each qubit has a dedicated CPW for control and readout. The following picture shows the chip layout.


<img src="../images/ibmqx2-labeled.png?raw=true" width="320">


The following tables show typical experimental parameters for this device (This particular set was taken for V1.0.0; see the version log for specific parameters):

| Qubit| &omega;<sup>R</sup><sub>i</sub>/2&pi; (GHz)       | &omega;<sub>i</sub>/2&pi;  (GHz)| &delta;<sub>i</sub>/2&pi; (MHz) | &chi;/2&pi; (kHz)| &kappa;/2&pi; (kHz)|
|----|-------------|--------|-------|--------|-------|
| **Q0**  | 6.530350 | 5.2723   | -330.3    | 476 | 523
| **Q1**  | 6.481848 | 5.2145   | -331.9    | 395 | 489
| **Q2**  | 6.436229 | 5.0289   | -331.2    | 428 | 415
| **Q3**  | 6.579431 | 5.2971   | -329.4    | 412 | 515
| **Q4**  | 6.530225 | 5.0561   | -335.5    | 339 | 480


where &omega;<sup>R</sup><sub>i</sub> is the resonance frequency of the readout resonator, &omega;<sub>i</sub> = (E<sub>i</sub> - E<sub>0</sub>)/&hbar; is the qubit frequency with i={00001,00010,00100,01000,10000}.  The anharmonicity (&delta;<sub>i</sub>) is the difference between the frequency of the 1-2 transition and the 0-1 transition. That is, it is given by &delta;<sub>i</sub> = (E<sub>2i</sub> - 2E<sub>i</sub>+ E<sub>0</sub> )/&hbar;.  &chi; is the qubit-cavity coupling strength, and &kappa; is the cavity coupling to the environment (&kappa;).

Crosstalk, which we parameterize by &zeta;<sub>ij</sub> = (E<sub>i+j</sub> - E<sub>i</sub> - E<sub>j</sub> + E<sub>0</sub>)/&hbar; is measured using a **J**oint **A**mplification of **ZZ** (JAZZ) experiment, which is a modified **BI**linear **R**otational **D**ecoupling (BIRD) [^fn1]. The standard BIRD sequence used in nuclear magnetic resonance (NMR) is a Ramsey experiment on one qubit, with echo pulses on both the measured qubit (Q<sub>i</sub>) and the coupled qubit (Q<sub>j</sub>).  In the JAZZ experiment, this sequence is performed twice, for each initial state of the coupled qubit. Additionally, the phase of the final &pi;/2-rotation is varied in order to detect an oscillating signal. &zeta;<sub>ij</sub> is equal to the frequency difference found between the two experiments.  The JAZZ experiment is shown in the figure below, and the measurements of all &zeta;<sub>ij</sub> are in the following table. The GD pulse notation is defined below in the Gate Specification section.  

[^fn1]: J.R. Garbow, D.P. Weitekamp, A. Pines, Bilinear rotation decoupling of homonuclear scalar interactions, Chemical Physics Letters, Volume 93, Issue 5, 1982, Pages 504-509.

<img src="../images/zz_sequence.png?raw=true" width="400">


In the crosstalk matrix, the error bar is less than 1 kHz for all &zeta;<sub>ij</sub> and a dash indicates an interaction strength for that pair < 25 kHz. This crosstalk matrix was taken for V1.0.0 (see version log for specific changes).


| &zeta;<sub>ij</sub>/2&pi; (kHz)  |  Q0 |   Q1|  Q2 |Q3   |  Q4 |
|:-:|---|---|---|---|---|
|   **Q0**|  X |  -43 | -83  |  - |  - |
|   **Q1**|  -45 |  X | -25  |  - |  - |
|   **Q2**| -83  |  -27 |  X | -127  | -38  |
|   **Q3**|  - |  - |  -127 |  X |  -97 |
|   **Q4**|  - |  - |  -34 |  -97 | X  |
 


## Experimental Setup
The following cartoon shows a depiction of the device I/O microwave setup:

<img src="../images/Ibmqx2-expsetup.png?raw=true" width="320">

## Gate Specification
 
<img src="../images/gatedef_U1U2U3_CNOT.png?raw=true" width="320">

A frame change (FC) is equivalent to applying a virtual *Z*-gate in software, where *Z*(&theta;)=FC(-&theta;). Gaussian derivative (GD) and Gaussian flattop (GF) pulses are defined with amplitude and angle parameters.

### Two-Qubit Gates
All currently calibrated two-qubit gates and their directions are defined in the coupling map and shown in the device picture below.  Generally, two-qubit gates are possible between neighboring qubits that are connected by a superconducting bus resonator.  The IBM Q experience uses the cross-resonance interaction as the basis for the CX-gate.  This interaction is stronger when choosing the qubit with higher frequency to be the control qubit, and the lower frequency qubit to be the target, so the frequencies of the qubits determines the direction of the gate.  

<img src="../images/ibmqx2-connections.png?raw=true" width="320">

Reported gate errors are measured using simultaneous randomized benchmarking (RB)[^fn2]. RB gives the average error per Clifford gate, which we convert to error per gate according to the set of primitive gates used on QX2.

[^fn2]: Jay M. Gambetta, A. D. Córcoles, S. T. Merkel, B. R. Johnson, John A. Smolin, Jerry M. Chow, Colm A. Ryan, Chad Rigetti, S. Poletto, Thomas A. Ohki, Mark B. Ketchen, and M. Steffen, Characterization of Addressability by Simultaneous Randomized Benchmarking, *Phys. Rev. Lett.* 109, 240504.
