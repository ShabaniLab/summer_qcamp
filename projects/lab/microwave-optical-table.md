Microwave optical table
=======================


Component positioning
---------------------

Figure out the best position for each component and the proper size for the
copper pieces to keep it in place (securing the mixers and power splitter is
the most important, securing the circulators would be best). Keep in mind that
the holes should not be too close to the edge (> 5mm).

Determine which piece requires a bottom spacer (to allow connecting SMA cables
to it).

Cut the copper pieces, using the sacrificial wood piece to avoid bending it too
much. Drill the holes (be careful copper tend top stick to the tool).

Put everything together.


Testing
-------

Check the power requirement of each mixer on the manufacturer's website, write
down the required power on the copper plate.

Connect the bottom microwave source to the power splitter (Krytar, blue) and
the middle one to the lone IQ mixer, using cables of the proper length.

Use the power analyser to determine how much power to apply so that each mixer
is properly driven (you may need to add an attenuator on one branch when the
same signal is used to drive 2 mixers). To do so disconnect the mixer from the
cable connected to the source and connect the signal analyser instead. Apply
0 dBm using the source and measure the received power (do not forget the -20 dB
attenuator before the signal analyser). From this you can deduce the
attenuation and what power to send to drive the mixer.

### Using the microwave sources

The three microwave sources (Signal Core) are started by switching the power
extension to which they are connected. They can be controlled from the computer
using the SC5511A USB Soft Front Panel program found under Signal Core in the
start menu and on the desktop. Each source is identified by its serial number
found on a sticker at its back. For testing you should use frequencies between
5 and 8 GHz. You should use the RF output 1 connector and be careful to avoid
static discharge when connecting or disconnecting.

### Using the power analyser

The power analyser (Signal Hound USB-SA124B) simply requires to be connected in
USB to the control computer. To avoid damaging it you should let the -20 dB
attenuator that is currently mounted on the input.

To use it, start the Spike program (found on the desktop of the control
computer). On the right hand side, you can set the frequency range over which
the device will measure. A span of 500 MHz, with a step of 500 kHz and RBW of
250 kHz should work well in all the cases we care about.


### Using the Keysight AWG and digitizer

To operate the Keysight rack you will need to use the Keysight SD1 SFP software
found under Keysight in the start menu. If the software only display "Demo
module", it means the instrument has not been properly recognized by the
computer. Make sure the instrument is on (the Fan LED should be on) and then
shutdown and restart the computer (check with Billy if this is fine). DO not
simply restart since it won't be enough to get the instrument talk to the
computer. If everything is fine you should see three panels:
- Module 0: M3202A
- Module 1: M3202A
- Module 2: M3102A

The first two are AWGs and the third one is a digitizer (high sampling rate
voltmeter). We will use the first AWGs to control the IQ mixer used to send
pulse to the qubit, and the second one to control the mixer on the readout
path. The I and Q ports of the readout mixer should be connected to channel 1
and 2 of the digitizer.

To use the AWGs you need to add a channel by clicking on the new folder icon
in the toolbar. You can then select the kind of waveform to play. We will use
Sinusoidal and AWG 1. Make sure to UNCHECK the HiZ check box otherwise their
will no output. For testing purposes, you can use a frequency of 50MHz. For the
amplitude you should check the specification of the mixers and compute the
power associated with the amplitude (V^2/50Ω). For a simple mixer when driving
the IF at 50 MHz, the power analyser should display 3 peaks:
- a weak one at the LO frequency
- two nearly symmetric ones at f_LO plus or minus 50 MHz.
For an IQ mixer it will depend on the relative amplitudes (and DC offset) of
drives applied on I and Q.

To use the AWG mode, you first need to create a waveform. Those are stored in
csv format (see for example the Gaussian pulse found on the desktop of the
control computer), and typically simply contain the voltage to set at each time
step (every ns). In our case, we need an envelope pulse with oscillation at
50 MHz. You can easily generate the proper file using Python. Next you need to
load your waveform in the memory of the instrument (Settings/AWG Memory and
click the small green plus button on the left). Finally to play that sequence
on the channel of your choice, you need to select it in Settings/AWG Queue
(click the green plus and click on the waveform name to select the proper one).
Try experimenting with  for example square, triangular, and gaussian envelope
and compare the spectrum at the output of the mixer using the spectrum
analyser. Note, that you need to click the play button for the sequence to run.

You can also measure propagation time in the microwave cable by connecting two
channels of one AWG to two channel of the digitizer using a very short cable in
one case and a very long in the other. In the digitizer pane, enable the two
channels you use and set the trigger on the channel with the short cable.
Select the proper input amplitude and set the impedance to 50 Ω. Finally click
Single and observe the traces. You may have to increase the number of points
(one every 2 ns) to see both. Measure the delay and estimate the speed of
propagation.
