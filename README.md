# One Sample OSC 1 and One Sample OSC 2


**IMPORTANT for MAC users**
Audio Unit runs on M1 machines. If you run into the prompt, that the plugin can't be opened because it is not from a verified developer just do this routine:
- go to your plugins folder /Library/Audio/Plug-Ins/Components
- right click the plugin or ctrl click the plugin
- choose open with and select terminal
- after the terminal appears open your Macs "system preferences", got to "security" and select "allow" for the plugin
- close all windows and terminal

After that procedure, the plugin works. Btw: This routine works for other software that is blocked as well.

Version 0.2

Pure Data Abstractions and VST3 and Audio Unit Plugins: 

[Download the latest Release here.](https://github.com/tob-har/1_Sample_Processor/releases)<br>
[Have a look/listen here](https://youtu.be/Gmqx0_3zaCM)<br>
[... and here.](https://youtu.be/PEX9j8iqWEo)<br>
[Talk about the project at ZKM next_generation 8.0](https://zkm.de/en/media/video/tobias-hartmann-000002083-seconds)




<img src="https://github.com/tob-har/one_sample_osc/blob/master/plugin_dev/One_Sample_OSC_1/oso1_screenshot.png" alt="YOne Sample OSC 1" width="500"/>
<img src="https://github.com/tob-har/one_sample_osc/blob/master/plugin_dev/One_Sample_OSC_2/oso2_screenshot.png" alt="YOne Sample OSC 2" width="500"/>




**One Sample OSC 1** and **One Sample OSC 2** are two different approaches one the same concept:

Processing a stereo audio input signal on a one sample accurate level.
The input audio signal is read out sample by sample. It is possible to interfere with the speed or timing, at which those samples are written consecutively into wavetables of two oscillators for instant playback at a given frequency. 

The unusual and non-accurate timing caused by this kind of signal processing results in a great variety of sounds. Due to the sample accurate processing, the output signal is always related to (and depending on) the audio input signal. 
Feel free to experiment with different settings and don’t forget to especially explore extreme small and large values.


### About the plugins

To install the VST3 and Audio Unit plugins unzip the downloaded archive and put the extracted Files into your VST3 and Audio Unit plugin directory.
(On MAC you find it here: /Library/Audio/Plug-Ins/VST3 and /Library/Audio/Plug-Ins/components)

Then open the DAW of your choice and find your plugins under VST3/Tobias Hartmann/ or AU/Tobias Hartmann/

The plugins are made possible thanks to Camomile by Pierre Guillot:

https://github.com/pierreguillot/Camomile


### About the abstractions 

[one_sample_osc_1] and [one_sample_osc_2] are both Pure Data Vanilla abstractions. 
Pure Data 0.50 or later is necessary. Pure Data 0.50.2 recommended.
The abstracionts are documented in the corresponding help files and all inlets and outlets are labeled and described within the abstraction.

Both abstractions feature control over:

- Input Volume (range 0-1)
- Input Gain (range 1-20)
- Dry/Wet Mix (range 0-1)
- Output Volume (range 0-1)
- Oscialltors playback frequency (in Hz)

There is a siginficant difference in the signal processing of the abstractions:

- [one_sample_osc_1] basically sends the incoming audio at a fixed given blocksize to a wavetable, that is read out by an [tabosc4~] oscillator instantly. The initial blocksize for sending the incoming audio stream is 1 sample, and the oscillaor subpatch is always reblocked to 1 sample blocksize (and 8 times oversampling). You can change the writing block size in steps at power of 2 (1, 2, 4, 8, 16, … ) Changing the reblocking blocksize of the osciallator subpatch can be done, but this is likely to cause crashing the whole patch. 
- [one_sample_osc_2] as based around [fexpr~]. The incoming audio stream feeds a buffer wavetable of the size of 1 sample. You can controll the speed in milliseconds at which this one-sample-buffer is read out and written consecutively into the 512 samples large oscillator wavetable for instant playback. The range is by default 0-3 milliseconds interval for writing each sample. In the help file a basic division by 10 lets you access the range 0-0.3 milliseconds.

Feel free to inplement the abstractions according to your needs or however you want to use it.
It is also possible to extend them for processing more audio channels, or to put an offset at one of the audio write speed or playback frequency for instant audible stereo effects. 


### About the help files and how to get started in Pure Data

Download the release V. 0.1.1 linked above.
Extract the .zip file. 
Put the Pure Data vanilla abstractions [one_sample_osc_1] and [one_sample_osc_2] in a new Pure Data patcher.
Open help file to get furhter informations and to explore the most basic features with a demo sample.
The folder [audio] contains the examples sound file (amen break 44.1 kHz) but you can load your own or use reatime input.


Enjoy!







---


Published under MIT License

Copyright 2020 Tobias Hartmann 

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions: The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software. 

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
