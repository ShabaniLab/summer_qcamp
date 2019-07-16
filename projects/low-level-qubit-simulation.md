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

To help you get started, we describe below the implementation of the basic
Hamiltonians and collapse operators you will need for the different elements
mentioned above. You can/should also look at some of the examples in
http://qutip.org/tutorials.html, in particular
https://nbviewer.jupyter.org/github/qutip/qutip-notebooks/blob/master/examples/qubit-dynamics.ipynb
and https://nbviewer.jupyter.org/github/qutip/qutip-notebooks/blob/master/examples/rabi-oscillations.ipynb
can help you get started.

Note: When working with multi partite system remember that you have to take
the tensor product of the different operator to form an operator that can
operate over the whole system

### Qubit

The Hamiltonian of a single qubit is defined as follows:

```python
from qutip import sigmaz

H = wq / 2.0 * sigmaz()

```

where wq is the qubit frequency (it is convenient to express all energy
scale in term of frequency).

The relaxation and dephasing of a qubit can be described by the following
collapse operators:

- Relaxation can be described by the operator `sigmam()` that goes
from |1〉 to |0〉
- Dephasing can be described by the operator `sigmaz()`


### Transmon

To represent the transmon qubit with more than two levels we will model as an
anharmonic oscillator by inclusing the quartic term coming from the Josephson
Junction non-linearity. We can describe the infinite number of state of the
system so we will truncate it to N levels. 4 or 5 levels should be enough in
general but you can experiment with this number.

```python
from qutip import destroy

a  = destroy(N)

H = (wq + alpha/2) * a.dag() * a - alpha/2 * (a.dag() * a * a.dag() * a)

```

wc is the qubit frequency (0 -> 1 transition) and alpha is the anharmonicity
of the qubit.

The relaxation and dephasing of a qubit can be described by the following
collapse operators:

- Relaxation can be described by the operator `a` that removes energy from the
  system.
- Dephasing can be described by the operator `a.dag() * a` that introduce
  frequency fluctuations.


### Cavity

A cavity is simply a linear oscillator so its representation is simpler
than the transmon but very similar.

```python
from qutip import destroy

a  = destroy(N)

H = wc * a.dag() * a

```

wc is the cavity frequency

Often cavities are coupled to the external world (for readout) and the number
of excitation decay. This can be modelled by using `a` as a collapse operator.


### Field/Cavity-qubit coupling

The coupling of the qubit to a cavity can be described in the following way:

```python
from qutip import destroy, sigmam, qeye, tensor

a  = tensor(destroy(N), qeye(2))
sm = tensor(qeye(N), sigman(2))
sz = tensor(qeye(N), sigmaz())

# Most general representation
H = wc * a.dag() * a + wq / 2.0 * sz + g * (a.dag() + a) * (sm + sm.dag())

# Approximate (Rotating Wave Approximation) representation
H = wc * a.dag() * a + wq / 2.0 * sz + g * (a.dag() * sm + a * sm.dag())

```

For the case of a classical drive you can replace the `(a.dag() + a) * (sm + sm.dag())`
term by `f(t) * sigmax() + g(t) * sigmay()` and remove the cavity part of the
Hamiltonian. Actually, you ca also move into the frame rotating at the
frequency of the microwave drive by writing the Hamiltonian:

```python
H = (wc - wd)/2.0 *sigmaz() + fr(t) * sigmax() + gr(t) * sigmay()
```

where fr and gr now only describe the envelope of the pulse and not the fast
rotation anymore which makes the simulation easier.

When studying pulse you will have to vary the amplitude of the field in time.


### Field/Cavity-transmon coupling

```python
from qutip import destroy, sigmam, qeye, tensor

a  = tensor(destroy(N), qeye(2))
b = tensor(qeye(N), destroy(2))

# Most general representation
H = wc * a.dag() * a + (wq + alpha/2) * b.dag() * b - alpha/2 * (b.dag() * b * b.dag() * b) + g * (a.dag() + a) * (b + b.dag())

# Approximate (Rotating Wave Approximation) representation
H = wc * a.dag() * a + (wq + alpha/2) * b.dag() * b - alpha/2 * (b.dag() * b * b.dag() * b) * (a.dag() * b + a * b.dag())

```

For the case of a classical drive you can replace the `(a.dag() + a) * (b + b.dag()))`
term by `f(t) * (a + a.dag()) + g(t) * 1j *(a - a.dag())` and remove the cavity
part of the Hamiltonian. Actually, you ca also move into the frame rotating at
the frequency of the microwave drive by writing the Hamiltonian:

```python
H = (wq + alpha/2 - wd) * b.dag() * b - alpha/2 * (b.dag() * b * b.dag() * b) + fr(t) * (a + a.dag()) + gr(t) * 1j *(a - a.dag())
```

where fr and gr now only describe the envelope of the pulse and not the fast
rotation anymore which makes the simulation easier.

When studying pulse you will have to vary the amplitude of the field in time.
