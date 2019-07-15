Majorana on an Ising chain
==========================

This series of projects builds on the project the lab team presented at the IBM
hackaton back in March.

It follows the proposal in https://arxiv.org/pdf/1703.08224.pdf to
emulate a Majorana braiding operation on an Ising chain with ferromagnetic
interaction and a transverse field. Qiskit is used to describe the system in
term of gates.

One interesting fact is that usually braiding is impossible in 1D but here the
use of an additional coupler spin, inducing a three spins interactions, allows
to circumvent that limitation.

All the details and the current implementation can be found at
https://github.com/ShabaniLab/qiskit-hackaton-2019

Since the entirety of that project has been realized in 24 straight hours there
is a number of open questions that could be addressed in a project.

## Directions

Possible directions are listed below. The goal is not to explore them all !
Pick what interest you the most and try to go as deep as possible, then switch
to a different topic if you still have time. Also if a different question
occurs to you feel free to investigate it !

- The simulation relies on the Suzuki-Trotter expansion (https://en.wikipedia.org/wiki/Time-evolving_block_decimation#The_Suzuki-Trotter_expansion).
  Due to the time constraints, the quality of the approximation as a function
  of the time step was never studied in details. Filling that gap and looking
  at the possible advantages of higher order scheme both in the presence and
  absence of the coupler would be very interesting.
- The time evolution of the system is more complex than one may suspect at
  first. During the hackaton, it was noted that even though one may expect to
  increase the fidelity by using slower magnetic field changes (in the absence
  of noise), specific durations seemed to give better result. This was also
  confirmed by some collaborators, the 'Majorana' oscillating in and
  out of existence. Further characterizing those processes in the absence and
  presence of the coupler and a function of the chain length is another
  direction (more than a single project maybe).
- This simulation is fairly demanding. Studying its most basic element in
  the presence of noise to determine what could be potentially run on an
  actual hardware would also provide interesting insight. Obviously this
  should build up on the optimizations discussed in the first two points.

This project could also connect to the "Qubit manipulation simulations" project
to try to implement in a native manner some of the gates required.
