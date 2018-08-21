# IBM Q 16 Rueschlikon V1.x.x

**display_name**: IBM Q 16 Rueschlikon  
**backend_name**: ibmqx5  
**backend_version**: 1.x.x   
**sample_name**: albatross 

This document contains information about the IBM Q experience **ibmqx5** backend for version 1.x.x. 

This device was formally backend **ibmqx3** for version 1.0.0. 

## Contributors (alphabetical)
Baleegh Abdo, Vivekananda Adiga, Lev Bishop, Markus Brink, Nicholas Bronn, Jerry Chow, Antonio Córcoles, Andrew Cross, Jay M. Gambetta, Jose Chavez-Garcia, Jared Hertzberg, Oblesh Jinka, George Keefe, David McKay, Salvatore Olivadese, Jason Orcutt, Hanhee Paik, Jack Rohrs, Sami Rosenblatt, Jim Rozen, Martin Sandberg, Dongbing Shao, Sarah Sheldon, Firat Solgun, Maika Takita

## Device Specifications 

The connectivity on the device is provided by total 22 coplanar waveguide (CPW) "bus" resonators, each of which connects two qubits. The connectivity configuration is shown in the figure below; the colored dots indicate qubits, and the colored bars indicate CPW bus resonators. Three different resonant frequencies are used for the bus resonators. The white bars indicate the buses with a resonant frequency of 6.25 GHz, the grey bars 6.45 GHz, and the black bars 6.65 GHz.    

<img src="../images/ibmqx3-bus.png?raw=true" width="750">

Each qubit has a dedicated CPW readout resonator attached (labeled as R) for control and readout. The following picture shows the chip layout.

<img src="../images/ibmqx3-labeled.png?raw=true" width="320">

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

<img src="../images/zz_sequence.png?raw=true" width="400">

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
| **Q8** | - | - | - | - | - | - | - | -59 | | -26| - | - | - | - | - | - |
| **Q9** | - | - | - | - | - | - | - | - | -25 | | -40 | - | - | - | - | - |
| **Q10** | - | - | - | - | - | - | - | -71 | - | -43 | | -38 | - | - | - | - |
| **Q11** | - | - | - | - | - | - | -68 | - | - | - | -42 | | -51 | - | - | - |
| **Q12** | - | - | - | - | - | -51 | - | - | - | - | - | -50 | | -43 | - | - |
| **Q13** | - | - | - | - | -27 | - | - | - | - | - | - | - | -46 | | -74 | - |
| **Q14** | - | - | - | -50 | - | - | - | - | - | - | - | - | - | -69 | | -103 |
| **Q15** | -61 | - | -55 | - | - | - | - | - | - | - | - | - | - | - | -106 | 



## Experimental Setup
The following cartoon shows a depiction of the device I/O microwave setup. We acknowledge MIT-Lincoln lab for providing the traveling-wave parametric amplifiers (TWPA) for this system.   

<img src="../images/ibmqx3-expsetup.png?raw=true" width="400">

## Gate Specification
 
<img src="../images/gatedef_U1U2U3_CNOT.png?raw=true" width="320">

A frame change (FC) is equivalent to applying a virtual *Z*-gate in software, where *Z*(&theta;)=FC(-&theta;). Gaussian derivative (GD) and Gaussian flattop (GF) pulses are defined with amplitude and angle parameters.

### Two-Qubit Gates

Generally, two-qubit gates are possible between neighboring qubits that are connected by a superconducting bus resonator.  The IBM Q experience uses the cross-resonance interaction as the basis for the CX-gate.  This interaction is stronger when choosing the qubit with higher frequency to be the control qubit and the lower frequency qubit to be the target, so the frequencies of the qubits determines the direction of the gate.  There are some exceptions to the rule of high frequency control/low frequency target: the gate direction must be reversed if the higher levels of the control qubit are degenerate with the target qubit, or if either qubit is coupled to a third (spectator) qubit that has the same frequency or a higher level with the same frequency as the target. Directions of the two-qubit gates are defined in the [version_log](./version_log.md).  

Reported gate errors are measured using simultaneous randomized benchmarking (RB)[^fn2]. RB gives the average error per Clifford gate, which we convert to error per gate according to the set of primitive gates used on IBMQX5.

[^fn2]: Jay M. Gambetta, A. D. Córcoles, S. T. Merkel, B. R. Johnson, John A. Smolin, Jerry M. Chow, Colm A. Ryan, Chad Rigetti, S. Poletto, Thomas A. Ohki, Mark B. Ketchen, and M. Steffen, Characterization of Addressability by Simultaneous Randomized Benchmarking, Phys. Rev. Lett. 109, 240504.
