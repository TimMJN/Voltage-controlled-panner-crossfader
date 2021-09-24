# Voltage-controlled panner/crossfader
 Dual voltage-controlled panner/crossfader for Kosmo and Eurorack modular synths. The module design features:
 - two independent panners/crossfaders
   - based on a single A3360 VCA chip
   - linear response
   - on-the-fly selectable functionality
 - two internal LFOs
   - square/triangle waveforms
   - wide frequency range
   - separate outputs, normralled to the CV inputs

A short [demonstration](https://youtu.be/eCm593cbdqw) is available on YouTube. View the [schematic](voltage_controlled_panner_crossfader_schematic/voltage_controlled_panner_crossfader.pdf) and [bill of materials](https://htmlpreview.github.io/?https://github.com/TimMJN/Voltage-controlled-panner-crossfader/blob/main/voltage_controlled_panner_crossfader_schematic/voltage_controlled_panner_crossfader_BOM.html) on this repository.

# Notes and Frequently Asked Questions
## The build
### Part selection
This module design relies on some opamp arithmetics, but does not provide calibration options for every stage. Therefore, it's recommended to use resistors with 1% tolerance or better, especially on all 100k resistors. This will result in better performance; more balanced outputs (in panner mode) and less bleed-through (in crossfader mode).

### Calibration
Each panner/crossfader stage has a single centre-trim setting, accesible by removing the pan/fade knob. The calibration procedure is fairly straightforward. If you have access to a multimeter:
- Apply a constant voltage to one of the inputs, leave the other input empty.
- Put the pan/fade potentiometer in the centre position.
- Compare the voltages on both outputs through the testing points on the back of the module.
- Adjust the trimmer until both outputs are equal.
- 
If you do not have access to a multimeter (you should when buidling DIY modules, even a simple one will do), you can choose to apply an audio signal to one of the inputs, and adjust until both outputs have equal volume.

## The patch
### What is a panner/crossfader?
Each section of this module as two inputs and two outputs. By using select connections, multiple functions are available:

#### Panner
For this functionality, connect an audio signal to one of the inputs, and treat the two outputs as a stereo signal. The input signal is distributed between the two output channels according to the control voltage, moving the audio source left and right in the stereo image. It should be noted that this module has a linear response, not what is commonly known as 'pan law'. In practice, this means that the stereo volume in the centre position will be slightly lower than in the panned positions.

#### Crossfader
To obtain crossfading behaviour, connect two audio (or CV) inputs, and one of the two outputs. The output signal will blend or fade between the two inputs, depending on the control voltage. It is possible that the output contains a little bit of both signals even in the extreme positions. This is a result of the single-VCA design and part tolerances.

While these describe the most common applications of the module, two more configurations are possible:
#### Linear VCA
By using only one input and one output, the module can be used as a VCA with either a linear of an inverse-linear response, depending on the output selected.

#### Stereo crossfader
It's possible to connect both inputs and both outputs simultanuously. The resulting behaviour can be intepreted in two ways. Treating the output as two mono signals, it can be seen as two oppositely cross-faded signals. Viewing it as a stereo output, the two inputs will move in opposite directions in the stereo image, constantly switching places.
