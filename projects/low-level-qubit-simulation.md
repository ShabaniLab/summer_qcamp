Qubit manipulation simulations
==============================

Qiskit provides us with a high-level and idealized vision of qubits. However,
if we constrain ourselves to small we can use other tools to explore in more
details the physics of the system.

In order to do this, we will need to use a different tool:
http://qutip.org/docs/latest/index.html. As with any new tool, it will take
some time to get familiar with it, but since it is written in Python and since
most quantum mechanical concepts will be familiar to you from your previous
readings it should go smoothly. The tips section below will also help you get
started.

## Directions

The idea of that family of project is to dive deeper into the detailed physics
of the transmon qubit. In particular, you will be able to explore the impact
of the presence of more than two levels in the transmon and the impact of
noise. Below are listed possible directions, you can decide to explore. The
goal is not to explore them all ! Pick what interest you the most and try to go
as deep as possible, then switch to a different topic if you still have time.
Also ift a different question occurs to you feel free to investigate it !

Note: In the following transmon refers to a non-linear oscillator model and
qubit to a simple two-level model.

- Single qubit:
  - Measurement induced state collapse (qubit/transmon + driven cavity)
  - Leakage into higher states: optimizing the pulse shape (transmon + drive)
  - Qubit and noise characterisation (qubit/transmon + drive)
  - Measurement induced dephasing (impact of residual photons in the readout on
    a qubit) (qubit/transmon + cavity)
  - Optimizing a gate in the presence of noise: optimal control
- Two qubits:
  - Impact of the coupling on single qubit operations (qubit/transmon x 2 +
    coupling/cavity)
  - Cross-resonance and the IBM CNOT gate: implementation and optimisation
    (qubit/transmon x 2 + coupling/cavity)
  - Impact of noise on the cross-resonance gate:
    - finite lifetime and coherence
    - spurious photons in the cavity
- Connect to the Majorana project and try to implement an efficient three qubit
  gate (open question it may very well not work).

## Tips

To help you get started we describe below the implementation of the basic
Hamiltonian you will need for the different elements mentioned above.

Note: When working with multi partite system remember that you have to take
the tensor product of the different operator to form an operator that can
operate over the whole system

### Qubit


### Transmon


### Cavity


### Cavity-qubit coupling


### Cavity-transmon coupling


### Cavity decay

