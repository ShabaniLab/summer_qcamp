# State and process characterization

In the first two tracks, we discussed how to characterize the state of one or
two qubits through measurements. We also looked into how one can determine the
effect of a circuit on an arbitrary state.

In this track we will formalize how to perform such operations in a systematic
manner.

This topic has strong link to the study of noise and errors in quantum circuits
that we will aboard in the next track, so you may need to go back and forth
between the two tracks at one point.

## References

Fully characterizing the state of a quantum state requires to perform a
tomography of the state. The procedure is called Quantum State Tomography (QST).
The following reference introduces it on both single qubit and two qubits
system.
http://research.physics.illinois.edu/QI/Photonics/tomography-files/amo_tomo_chapter.pdf

In some cases we are not only concerned with the state prepared by the circuit,
but by the actual effect of a circuit on a generic state. This can be used for
example to verify that a circuit operates as predicted by the theory. Fully
determining the effect of a circuit requires to perform a Quantum Process
Tomography (QPT). Many flavors of it exist and the following reference
introduce the most common one.
https://arxiv.org/pdf/1502.01016.pdf

The following reference is a quite complete reference about quantum computing.
You can refers to it for additional discussions.
<mmrc.amss.cas.cn/tlb/201702/W020170224608149940643.pdf>


## Qiskit tools

Qiskit provide tools to perform both QST and QPT and more importantly to analyse
the results of those procedures under Qiskit Ignis. They are illustrated in the
following notebooks:
- https://nbviewer.jupyter.org/github/Qiskit/qiskit-tutorials/blob/master/qiskit/ignis/state_tomography.ipynb
- https://nbviewer.jupyter.org/github/Qiskit/qiskit-tutorials/blob/master/qiskit/ignis/process_tomography.ipynb

## Direction

The notebooks teach you how to use the tools provided in Qiskit Ignis which is
fine. However before starting playing with those on different states and
process, look at the circuits generated for QST and QPT. Do they match your
expectations based on what you did in the first two tracks ?
