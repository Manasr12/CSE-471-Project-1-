# Project 1 CSE 471

## Table of Contents
- [Introduction](#introduction)
- [Group Members](#group-members)
- [Score File Format](#score-file-format)
- [Score File Example](#score-file-example)
- [Component Overview](#component-overview)
  - [Subtractive Synthesizer](#Subtractive-Synthesizer)
  - [Chorus](#Chorus)
  - [Flanging](#Flanging)
  - [Reverberation](#Reverberation)
  - [Ring Modulation](#Ring-Modulation)
- [Grading Elements](#grading-elements)

## Introduction
Provide an introduction to your project. Explain what the project is about and what it aims to achieve.

## Group Members
- Duncan Stewart
- Mannan Dhillon
## component-overview
- Subtractive Synthesizer
- Effects:
  - Chorus
  - Flanging
  - Reverberation
  - Ring Modulation
 

## Subtractive Synthesizer
Completed by Mannan Dhillon
10 - Waveform playback from tables - 10 completed as described
20 - Varying pitch playback from tables - 20 completed as described
30 - Envelope generation - 30 completed as described
35 - Polyphony - 35 completed as described
40 - Reson implementation and the Moog sound - 40 completed as described
50 - Filter envelopes - 50 completed as described

Summary: 
The Sub class serves as the main component of the subtractive synthesizer. It orchestrates the sound generation process by utilizing the SubWave class. Upon playing a note, the Start method in Sub initializes the envelope and amplitude filter. The SetNote method adjusts sound attributes based on a CNote object.

The SubWave class is responsible for the actual sound generation. It uses a wavetable for this purpose. The Generate method in SubWave retrieves and outputs the waveform from the wavetable. The SetWavetables method populates the wavetable with samples and applies a resonant filter if enabled. The ResonFilt method implements this resonant filter, emphasizing a specific frequency and influencing the sound’s timbre. This intricate interplay of components results in the final sound output.

All components of this instrument have been completed as specified, our grading for this section is above.

## Effects:
Completed by Duncan Stewart

10 - Component passes audio - 10 completed as described
20 - 1 Effect - 10 completed as described
30 - 3 Effects - 10 completed as described
40 - Controllable effects send - 10 completed as described
50 - 4 Effects - 10 completed as described

Summary: 
The BaseEffect class serves as the foundation for all audio effects in the system. It initializes two queues, m_lque and m_rque, in its constructor. The SetNote method processes a CNote object and extracts its attributes. The ProcessAttribute method then applies these attributes to the effect.

This class provides methods to set various effect parameters such as ‘wet’, ‘dry’, ‘delay’, and ‘threshold’. These parameters are essential in shaping the sound output of the audio effects. The BaseEffect class is a crucial component that enables the creation of diverse audio effects in the system.

## Chorus
The Chorus class is an audio processor that modifies the input sound to produce a richer output. It uses a wavetable and a low-frequency oscillator (LFO) to create a chorus effect. The depth, rate, mix, and output gain of the effect can be adjusted, allowing for a wide range of sounds. The Chorus class also includes methods to start the effect, process the input frame, and update the LFO increment. 
## Flanging
The Flanger class is an audio effect processor that creates a flanging effect. It initializes parameters such as depth, rate, feedback, delay index, and output gain in its constructor. The Process method applies the flanging effect to the input frame by calculating a low-frequency oscillator (LFO) value, determining the delay length, and mixing the delayed sample with the input frame.
## Reverberation
The Reverb class is an audio effect processor that creates a reverberation effect. It initializes parameters such as room size, damping, wet level, and write index in its constructor. The Process method applies the reverb effect to the input frame by calculating a low-frequency oscillator (LFO) value, determining the delay length, and mixing the delayed sample with the input frame.
## Ring Modulation
The RingMod class is an audio effect processor that creates a ring modulation effect. It initializes parameters such as modulation frequency and current phase in its constructor. The Process method applies the ring modulation effect to the input frame by calculating a modulator signal, which is a sine wave with the current phase, and then mixing this signal with the input frame.
## Score File Format
Describe the format of your score files. Include details such as the file type (e.g., `.txt`, `.json`, `.xml`), the structure of the content, encoding used, and any other relevant information.

Here is the format of our score file below: 

<?xml version="1.0" encoding="utf-8"?>
<score bpm="100" beatspermeasure="4">
    <instrument instrument="SubtractiveInstrument">
        <!-- London Bridge is falling down, -->
        <note measure="1" beat="1" duration="2" note="D4" wavetype="Triangle" />
        <note measure="1" beat="3" duration="2" note="E4" wavetype="Triangle" />
        <note measure="2" beat="1" duration="2" note="F4" wavetype="Triangle" />
        <note measure="2" beat="3" duration="2" note="A4" wavetype="Triangle" />
	<note measure="3" beat="1" duration="2" note="F4" wavetype="Triangle" />
        <note measure="3" beat="3" duration="2" note="A4" wavetype="Triangle" />
        <note measure="4" beat="1" duration="2" note="E4" wavetype="Triangle"/>
        <note measure="4" beat="3" duration="2" note="D4" wavetype="Triangle"/>
        <!-- My fair lady. -->
        <note measure="5" beat="1" duration="3" note="D4" wavetype="Triangle"/>
    </instrument>
	<instrument instrument="Chorus">
        <!-- Falling down, falling down, -->
        <note measure="3" beat="1" delay=".1" wet=".5" dry=".5"/>
        <note measure="3" beat="3" delay=".1" wet=".7" dry=".3"/>
    </instrument>
</score>

This was a testing file we used to see if our Chorus effect worked. As you can see it it very similar to the original Synthie test files. We just made effects and the Subtractive wave seperate instruments in the file itself. Effects always come after our actual instrumnet "Instrument", like the subtractive instrument we implemented. Each note contains specific information that is used in our instrument such as beat, duration, note, wavetype etc.
