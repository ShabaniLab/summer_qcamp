Resonant circuit design test
============================

The idea of this project is to test the circuit that will be integrated in the
sample holder in the 'Sample holder PCB design project'. To be able to run the
tests you will have to order (ask Kasra or Joe for help) the following
components:

- Coilcraft: SMC inductor, packaging 0805CS kit C303-2
- MACOM: MA46H204-1056 (order ~10 from Digikey or Mouser)
- Resistors and capacitors, packaging 0402, as needed
  (refer to https://qdev.nbi.ku.dk/student_theses/pdf_files/PhDThesis_Nissen.pdf
  p 113 for possible manufacturers). Note that we may have already some of
  those so check the stocks.
- Minicircuits: Directional coupler ZEDC-15-2B
- Digikey/Mouser: SMP-MSLD-PCS

The tank circuit is described in https://link.aps.org/doi/10.1103/PhysRevApplied.5.034011
figure 1 a. It is composed of two variable capacitors (see inset with a
dashed frame), an inductor and is connected through a 5 kΩ resistor to a DC
line. The resistor in parenthesis in the schematic is simply used for modelling
purposes (not a physical component). An alternative design without the variable capacitors should also
be tested. To connect the AC port of the circuit use an SMP connector
SMP-MSLD-PCS (try to make your design 50 Ω match). As in the paper we will use a
large resistor (~ 1 GOhm) connected to ground to model the sample. You may have
to order it.

In order to be able to test it, you will have to design a test PCB to
accommodate the components. You will be able to fabricate it using the lab
milling machine.

Once you have the PCB and you have mounted all the components on it, ask for
help to setup the VNA to measure the reflected signal by using the directional
coupler. Study the dependence of the resonances as a function the varactor bias.
One of the goals is to check that those components behave as expected.
