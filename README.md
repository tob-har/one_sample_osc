# one_sample_osc

[Download the Pure Data abstracions V 0.1 (.zip) here.](https://github.com/tob-har/1_Sample_Processor/releases)

The Pure Data abstractions [one_sample_osc_1] and [one_sample_osc_2] are two different approaches one the same concept:

Processing an audio stream of two channels on a one sample accurate level, whereby the audio stream is read out sample by sample and one can interfere the speed or timing, at which those samples are written consecutively into a wavetable of two oscillators for instant playback at a given frequency. 

The unusual and non accureate timing caused by this kind of signal processing, results in a great variety of audible results during playback. Due to the sample accurate processing, the output is always related and depended on the audio input. Feel free to experiment with variouse settings and don’t forget to especially explore extreme small and large values!



### About the abstractions 

[one_sample_osc_1] and [one_sample_osc_2] are both Pure Data vanilla abstractions. 
Pure Data 0.50 or later is necessary. Pure Data 0.50.2 recommended.
The abstracionts are documented in the corresponding help files and all inlets and outlets are also labelled and described within the abstraction.

Both abstractions feature controll over:

- Input Volume (range 0-1)
- Input Gain (range 1-20)
- Dry/Wet Mix (range 0-1)
- Output Volume (range 0-1)
- Oscialltors playback frequency (in Hz)

There is a siginficant difference in the signal processing of the abstractions:

- [one_sample_osc_1] basically sends the incoming audio at a fixed given blocksize to a wavetable, that is read out by an [tabosc4~] oscillator instantly. The initial blocksize for sending the incoming audio stream is 1 sample, and the oscillaor subpatch is always reblocked to 1 sample blocksize (and 8 times oversampling). You can change the writing block size ins steps at power of 2 (1, 2, 4, 8, 16, … ) Changing the reblocking blocksize of the osciallator subpatch can be done, but this is likely to cause crashing the whole patch. 
- [one_sample_osc_2] as based around [fexpr~]. The incoming audio stream feeds a buffer wavetable of the size of 1 sample. You can controll the speed in milliseconds at which this one-sample-buffer is read out and written consecutivly into the 512 samples large oscillator wavetable for instant playback. The range is by default 0-3 milliseconds interval for writing each sample. In the help file a basic division by 10 lets you access the range 0-0.3 millisenconds.



### About the help files and how to get started

Download the release linked above.
Extract the .zip file. 
Place the Pure Data vanilla abstractions [one_sample_osc_1] and [one_sample_osc_2] in a new Pure Data patcher.
Open help file to get furhter informations and to explore the most basic features.
The folder [audio] contains the examples sound file (amen break 44.1 kHz) but you can load your own or use reatime input.


### Versions

- [Initial Release V 0.1 (02.05.2020)](https://github.com/tob-har/1_Sample_Processor/releases)


Feel free to inplement the abstractions according to your needs or however you want to use ist.
It is also possible to extend them for processing more audio channels, or to put an offset at one of the audio write speed or playback frequency for instant audible stereo effects. 

Enjoy!








---


Published under MIT License

Copyright 2020 Tobias Hartmann 

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions: The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software. 

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
