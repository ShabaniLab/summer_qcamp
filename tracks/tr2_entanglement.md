# Entanglement

Now that you are more familiar with what is a qubit, how to represent it and
how to play with it using Qiskit, let's move to a larger system (2 qubits).
Just as quantum mechanics challenges our intuition for single particle, it
introduces some surprises when we consider interacting system of multiple
particles.

### Reminder

This is not standard lecture. You will have to read through multiple references
to gain some insight of the rules of quantum mechanics and then try to map what
you learn to the notion of qubits using Qiskit. Qiskit is a tool for you to
experiment. If you don't understand something, try to think of a simple
experiment you can do using Qiskit and run it. Look at the results and see if
they fit with your expectations. Feel free to discuss with the other students
and you cannot find a solution to a technical problem online ask the mentors.

## References

- *QUANTUM MECHANICS The Theoretical Minimum* by LEONARD SUSSKIND and ART FRIEDMAN
  https://archive.org/details/QuaMecTheTheMin/page/n3
  - chapter 6: This chapter proposes some exercise the first are purely
    mathematical and can be skipped. From with 6.5 to 6.8, you can map them to
    experiments in Qiskit. Try to do so !


## Qiskit basics

To get started you can have a look at the qiskit documentation
https://qiskit.org/documentation/getting_started.html. You can look at
https://qiskit.org/documentation/terra/summary_of_quantum_operations.html
to learn what operation you can perform on your qubits using qiskit. Do not
focus too much on the maths, rather try to figure out what a given gate does
through simple tests.


## Directions

- During the exercise you will have to figure out how to create what is known
  as triplet and singlet state. Since you may not know how to characterize them
  using only measurement (yet), help yourself of the state vector simulator and
  `plot_state_city` tool to figure out how to create them.
- Try to thing about how you would fully characterize a two-qubit system the
  way you did with a single qubit ? The full answer is quite involved but you
  can at least describe the measurement procedure.

Once you have dealt with example of the book, try to investigate some larger
system (3 qubits) and once you feel at ease, have a look at the tutorials in
https://github.com/Qiskit/qiskit-tutorials/tree/master/community/terra/qis_intro
that covers most of the basic ideas we explored in the first two tracks.
