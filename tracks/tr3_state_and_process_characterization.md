# State and process characterization

In the first two tracks, we discussed how to characterize the state of one or
two qubits through measurements. We also looked into how one can determine the
effect of a circuit on an arbitrary state.

In this track we will formalize how to perform such operations in a systematic
manner.

This topic has strong links to the study of noise and errors in quantum circuits
that we will cover in the next track. Therefore, you may need to go back and forth
between the two tracks at some point.

## References

Fully characterizing the state of a quantum state requires performing a
tomography of the state. This procedure is called Quantum State Tomography (QST).
The following reference introduces it on both single qubit and two qubits
system:
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
[Quantum Computation and Quantum Information](http://mmrc.amss.cas.cn/tlb/201702/W020170224608149940643.pdf)

This track requires a good understanding of density matrices. Feel free to
check out Chapter 7 of "Quantum Mechanics: The Theoretical Minimum" for further
information on density matrices, the ways to construct and use them.


## Qiskit tools

Qiskit provides tools to perform both QST and QPT and more importantly to analyze
the results of those procedures under Qiskit Ignis. Those are illustrated in the
following notebooks:
- https://nbviewer.jupyter.org/github/Qiskit/qiskit-tutorials/blob/master/qiskit/ignis/state_tomography.ipynb
- https://nbviewer.jupyter.org/github/Qiskit/qiskit-tutorials/blob/master/qiskit/ignis/process_tomography.ipynb

## Directions

The notebooks teach you how to use the tools provided in Qiskit Ignis, which is
fine. However, before starting to play with those on different states and
processes, look at the circuits generated for QST and QPT. Do they match your
expectations based on what you did in the first two tracks ?

Try to compare the real hardware results of a simple QST with the perfect
situation represented by the simulator .
