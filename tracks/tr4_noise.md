# Noise and qubit characterization

The goal of this chapter is to get you familiar with the impact of noise on
a qubit and with the methods that can be used to characterize a qubit.


## References

The following review paper on superconducting qubits technology gives abroad
overview of state of the art techniques. In particular section III A, B and C
provides an introduction to noise sources.
https://aip.scitation.org/doi/full/10.1063/1.5089550

Rigetti computing similarly to IBM provides a cloud service for quantum
computation. The documentation of PyQUIL ("equivalent" of Qiskit ) provides an
introduction to noise modelling.
http://docs.rigetti.com/en/stable/noise.html

Finally the chapter 8 of
[Quantum Computation and Quantum Information](http://mmrc.amss.cas.cn/tlb/201702/W020170224608149940643.pdf)
covers in a more technical manner the different ways one can represent noise.
It uses the same terminology as Qiskit and may help clarify the Qiskit
documentation.


## Qiskit

Qiskit provides both tools to simulate the impact of noise on a qubit under Aer
and tools to characterize qubits under Ignis. Because those characterizations
require to run many circuits it is not always practical to run them all on the
real hardware, but you can try to run a couple on a real backend to get a feel
for the real devices limitations.

The following two notebooks cover how to define noise in qiskit, and cover in
particular the noise model that can be used to approximate the noise on a real
device.
https://github.com/Qiskit/qiskit-tutorials/blob/master/qiskit/aer/building_noise_models.ipynb
https://github.com/Qiskit/qiskit-tutorials/blob/master/qiskit/aer/device_noise_simulation.ipynb

The first Ignis notebook focuses on the usual measurements to characterize noise,
such as T1 measurements, Ramsey oscillation, Hahn echo. The second one is more
geared toward analysing errors in gate that are not always the result of noise.
In both cases, the noise setup is sometime a bit tweaked to reflect the actual
measurement that relies on experimental parameters not accessible from Qiskit,
such as the frequency used to drive the qubit.
https://github.com/Qiskit/qiskit-tutorials/blob/master/qiskit/ignis/relaxation_and_decoherence.ipynb
https://github.com/Qiskit/qiskit-tutorials/blob/master/qiskit/ignis/hamiltonian_and_gate_characterization.ipynb


## Direction

As the previous one, that you can now re-visit with noise added, this track is
less guided. Feel free to explore different noise models and see how they
impact your result. For example, try to identify what kind of noise or error is
the most damaging to the preparation and characterization of the singlet state.

