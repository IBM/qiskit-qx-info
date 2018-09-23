# IBM Q 16 Melbourne V1.x.x

**display_name**: IBM Q 16 Melbourne  
**backend_name**: ibmq\_16\_melbourne  
**backend_version**: 1.x.x   
**sample_name**: albatross 

This document contains information about the IBM Q experience **ibmq\_16\_melbourne** backend for version 1.x.x. 

## Contributors (alphabetical)
Baleegh Abdo, Vivekananda Adiga, Lev Bishop, Markus Brink, Nicholas Bronn, Jerry Chow, Antonio Córcoles, Andrew Cross, Jay M. Gambetta, Jose Chavez-Garcia, Jared Hertzberg, Oblesh Jinka, Abhinav Kandala, George Keefe, David McKay, Salvatore Olivadese, Jason Orcutt, Hanhee Paik, Jack Rohrs, Sami Rosenblatt, Jim Rozen, Martin Sandberg, Dongbing Shao, Sarah Sheldon, Firat Solgun, Maika Takita, Jeng-Bang Yau

## Device Specifications 

The connectivity on the device is provided by total 22 coplanar waveguide (CPW) "bus" resonators, each of which connects two qubits. The connectivity configuration is shown in the figure below; the colored dots indicate qubits, and the colored bars indicate CPW bus resonators. Three different resonant frequencies are used for the bus resonators. The white bars indicate the buses with a resonant frequency of 6.25 GHz, the grey bars 6.45 GHz, and the black bars 6.65 GHz. Two of the qubits in the chip are not calibrated due to frequency instability and crosstalk issues. 

<img src="../images/melbourne-bus.png?raw=true" width=750">

Each qubit has a dedicated CPW readout resonator attached (labeled as R) for control and readout. The following picture shows the chip layout.

<img src="../images/melbourne-labeled.png?raw=true" width="320">

The following table shows some of the typical experimental parameters for this device (for V1.1.0).

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


where &omega;<sup>R</sup><sub>i</sub> is the resonance frequency of the readout resonator, &omega;<sub>i</sub> = (E<sub>i</sub> - E<sub>0</sub>)/&hbar; is the qubit frequency with i={0...1,0...10,...,01...0,1...0}.  The anharmonicity (&delta;<sub>i</sub>) is the difference between the frequency of the 1-2 transition and the 0-1 transition and is approx. ~290 MHz for all the qubits. That is, it is given by &delta;<sub>i</sub> = (E<sub>2i</sub> - 2E<sub>i</sub>+ E<sub>0</sub> )/&hbar;.  

Crosstalk, which we parameterize by &zeta;<sub>ij</sub> = (E<sub>i+j</sub> - E<sub>i</sub> - E<sub>j</sub> + E<sub>0</sub>)/&hbar; is measured using a **J**oint **A**mplification of **ZZ** (JAZZ) experiment, which is a modified **BI**linear **R**otational **D**ecoupling (BIRD) [^fn1]. The standard BIRD sequence used in nuclear magnetic resonance (NMR) is a Ramsey experiment on one qubit, with echo pulses on both the measured qubit (Q<sub>i</sub>) and the coupled qubit (Q<sub>j</sub>).  In the JAZZ experiment, this sequence is performed twice for each initial state of the coupled qubit. Additionally, the phase of the final &pi;/2-rotation is varied in order to detect an oscillating signal. &zeta;<sub>ij</sub> is equal to the frequency difference found between the two experiments.  The JAZZ experiment is shown in the figure below, and the measurements of all &zeta;<sub>ij</sub> are in the following table.  The GD pulse notation is defined below in the Gate Specification section.

[^fn1]: J.R. Garbow, D.P. Weitekamp, A. Pines, Bilinear rotation decoupling of homonuclear scalar interactions, *Chemical Physics Letters*, Volume 93, Issue 5, 1982, Pages 504-509.

<img src="../images/zz_sequence.png?raw=true" width="400">

Here is a typical crosstalk matrix (for V1.0.0), the error bar is less than 1 kHz for all &zeta;<sub>ij</sub> and a dash indicates an interaction strength for that pair < 5 kHz.

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



## Experimental Setup
The following cartoon shows a depiction of the device I/O microwave setup.

<img src="../images/melbourne-expsetup.png?raw=true" width="400">

## Gate Specification
 
<img src="../images/gatedef_U1U2U3_CNOT.png?raw=true" width="320">

A frame change (FC) is equivalent to applying a virtual *Z*-gate in software, where *Z*(&theta;)=FC(-&theta;). Gaussian derivative (GD) and Gaussian flattop (GF) pulses are defined with amplitude and angle parameters.

### Two-Qubit Gates

Generally, two-qubit gates are possible between neighboring qubits that are connected by a superconducting bus resonator.  The IBM Q experience uses the cross-resonance interaction as the basis for the CX-gate.  This interaction is stronger when choosing the qubit with higher frequency to be the control qubit and the lower frequency qubit to be the target, so the frequencies of the qubits determines the direction of the gate.  There are some exceptions to the rule of high frequency control/low frequency target: the gate direction must be reversed if the higher levels of the control qubit are degenerate with the target qubit, or if either qubit is coupled to a third (spectator) qubit that has the same frequency or a higher level with the same frequency as the target. Directions of the two-qubit gates are defined in the [version_log](./version_log.md).  

Reported gate errors are measured using simultaneous randomized benchmarking (RB)[^fn2]. RB gives the average error per Clifford gate, which we convert to error per gate according to the set of primitive gates used on IBMQX5.

[^fn2]: Jay M. Gambetta, A. D. Córcoles, S. T. Merkel, B. R. Johnson, John A. Smolin, Jerry M. Chow, Colm A. Ryan, Chad Rigetti, S. Poletto, Thomas A. Ohki, Mark B. Ketchen, and M. Steffen, Characterization of Addressability by Simultaneous Randomized Benchmarking, Phys. Rev. Lett. 109, 240504.
