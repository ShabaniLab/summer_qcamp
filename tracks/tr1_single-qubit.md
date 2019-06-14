# Single qubit

The idea of this track is to familiarize yourself with some key concept of
quantum mechanics and to learn to transpose them in term of circuits using
Qiskit.

This is not standard lecture. You will have to read through multiple references
to gain some insight of the rules of quantum mechanics and then try to map what
you learn to the notion of qubits using Qiskit. Qiskit is a tool for you to
experiment. If you don't understand something, try to think of a simple
experiment you can do using Qiskit and run it. Look at the results and see if
they fit with your expectations. Feel free to discuss with the other students
and you cannot find a solution to a technical problem online ask the mentors.

## Readings

- Feynman lectures http://www.feynmanlectures.caltech.edu/III_toc.html
  - chapter 1
  - chapter 5
  - chapter 6

- *QUANTUM MECHANICS The Theoretical Minimum* by LEONARD SUSSKIND and ART FRIEDMAN
  - chapter 1
  - chapter 2 (you can skip the mathematical appendices at first)

## Qiskit basics

Some basics assumptions made in Qiskit:
- qubits always start in the zero state of the measurement basis
- the measurement basis has a fixed axis (z)

To get started you can have a look at the qiskit documentation
https://qiskit.org/documentation/getting_started.html. It describes a two-qubit
experiment but you can simply transform it in a single qubit one for your
purpose. You can look at https://qiskit.org/documentation/terra/summary_of_quantum_operations.html
to learn what operation you can perform on your qubit using qiskit (focus on
the single qubit part we will come to multi qubit operations later on). Do not
focus too much on the maths, rather try to figure out what a given gate does
through simple tests.

## Directions

- Qiskit has a fixed measurement basis how to emulate a rotation of the
  measurement basis ? Hint: it is a question of perspective.
- Can you figure out a way to understand what a given gate does simply based
  on measurements ?

Once you think you have a grasp of those look at
https://nbviewer.jupyter.org/github/Qiskit/qiskit-tutorials/blob/master/qiskit/basics/3_plotting_data_in_qiskit.ipynb
to learn about different ways of plotting when using different simulators.
Those simulators are further away from the experimental truth but can help
confirm some of your intuitions for a single qubit in a more visual manner.
