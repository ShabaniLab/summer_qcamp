Annealer for Dopant Activation
========================

PID Parameters Optimization
---------------
- Connect the gas (N2 or Ar) and set to proper flow
- Turn on the power supply for the heating element
- Connect the handheld thermocouple to the DAQ to be able to read temperature independently
- Open the annealer GUI by activating the annealer python environment and running the annealpy file
- Setup the recipe with the following three steps:
    - Ramp up: Heating to the target temperature
    - Stabilize: Maintaining anneal temperature for a given period of time
    - Cooling down: Turning off the heater and letting the system cool down as fast as possible
- For the "Ramp up" and "Stabilize" steps, try to vary the P/I/D parameters in a manner that you get perfect anneal profile.


Dopant activation
---------------
- After optimizing your annealing profile, start with Si or Ge samples and anneal at various temperatures 
- To check the electrical properties of the samples, you can wire them up in van der Pauw configuration and cool them down in the Teslotron top-loader fridge.


Resources
---------------
- To know more about PID parameters for feedback loops review this wikipedia page: https://en.wikipedia.org/wiki/PID_controller
- To learn about ion implantation and dopant activation take a look at this paper: https://aip.scitation.org/doi/pdf/10.1063/1.331780?class=pdf