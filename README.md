# Project 1 CSE 471

## Introduction
For this project we used the Step 5 Synthie program and modified it to use a subtractive instrument and several effects. This page is our web page component of the project and serves to outline what we are submitting as our CSE 471 project. Also in this repo are the original score files. The Fur Elise file is our minute long song and the effects testing file showcases the functionality of our effects. The Wav files can be found there too. The actual project is submitted via D2L.
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
- 10 - Waveform playback from tables - 10 completed as described
- 20 - Varying pitch playback from tables - 20 completed as described
- 30 - Envelope generation - 30 completed as described
- 35 - Polyphony - 35 completed as described
- 40 - Reson implementation and the Moog sound - 40 completed as described
- 50 - Filter envelopes - 50 completed as described


Summary: 

The SubWave class is responsible for the actual sound generation. It uses a wavetable for this purpose. The Generate method in SubWave retrieves and outputs the waveform from the wavetable. The SetWavetables method populates the wavetable with samples and applies a resonant filter if enabled. The ResonFilt method implements this resonant filter, emphasizing a specific frequency and influencing the sound’s timbre. This combination of components results in the final sound output.

The Sub class is the core of our subtractive synthesizer project, successfully coordinating sound synthesis via the SubWave class. It has seen the completion of essential features: playback of waveforms from tables, fine-tuned pitch variations, creation of envelopes, implementation of polyphony, and the Moog-inspired Reson filter for the completed sound. We've also integrated filter envelopes to add depth and movement to the end product. These features have been tested, functioning exactly as outlined in the project specifications.

Upon triggering a note, the Sub class's Start method begins its process, initializing the envelope and amplitude filter. The SetNote method adapts the audio characteristics, taking input from the CNote object to tweak the pitch and timbre. SubWave has priority of generating the sound, with the Generate method utilizing the wavetable for waveforms and the SetWavetables method populating it with the necessary samples. The resonant frequencies work through the ResonFilt method, effecting the sound. 
All components of this instrument have been completed as specified, our grading for this section is above.

## Effects:
Completed by Duncan Stewart

- 10 - Component passes audio - 10 completed as described
- 20 - 1 Effect - 10 completed as described
- 30 - 3 Effects - 10 completed as described
- 40 - Controllable effects send - 10 completed as described
- 50 - 4 Effects - 10 completed as described

Summary: 
The BaseEffect class serves as the foundation for all audio effects in the system. It initializes two queues, m_lque and m_rque, in its constructor. The SetNote method processes a CNote object and extracts its attributes. The ProcessAttribute method then applies these attributes to the effect.

This class provides methods to set various effect parameters such as ‘wet’, ‘dry’, ‘delay’, and ‘threshold’. These parameters are essential in shaping the sound output of the audio effects. The BaseEffect class is a crucial component that enables the creation of diverse audio effects in the system.

## Chorus
The Chorus class is an effect that modifies the input sound to produce a richer output. It uses a wavetable and a low-frequency oscillator (LFO) to create a chorus effect. The depth, rate, mix, and output gain of the effect can be adjusted, allowing for a wide range of sounds. The Chorus class also includes methods to start the effect, process the input frame, and update the LFO increment. 
## Flanging
The Flanger class is an effect that creates a flanging effect. It initializes parameters such as depth, rate, feedback, delay index, and output gain in its constructor. The Process method applies the flanging effect to the input frame by calculating a low-frequency oscillator (LFO) value, determining the delay length, and mixing the delayed sample with the input frame.
## Reverberation
The Reverb class is an effect that creates a reverberation effect. It initializes parameters such as room size, damping, wet level, and write index in its constructor. The Process method applies the reverb effect to the input frame by calculating a low-frequency oscillator (LFO) value, determining the delay length, and mixing the delayed sample with the input frame.
## Ring Modulation
The RingMod class is an effect that creates a ring modulation effect. It initializes parameters such as modulation frequency and current phase in its constructor. The Process method applies the ring modulation effect to the input frame by calculating a modulator signal, which is a sine wave with the current phase, and then mixing this signal with the input frame.
## Remaining points:
- 10 - Suitable length audio files and web site turned in. -  10 completed as described
- 20 - Audio file is recognizable as music in the opinion of the TA and Instructor.- 10 completed as described (I mean come on its classical) 
- 30 - Audio file utilizes all system components. - 10 completed as described
- 40 - Audio file utilizes all capabilities of all system components.- 10 completed as described
- 50 - The script has at least 240 notes in it.- 10 completed as described

## Score File Format


Here is the format of our score file below: 
```score
<?xml version="1.0" encoding="utf-8"?>
<score bpm="100" beatspermeasure="4">
    <instrument instrument="SubtractiveInstrument">
        <note measure="1" beat="1" duration="2" note="D4" wavetype="Triangle" />
        <note measure="1" beat="3" duration="2" note="E4" wavetype="Triangle" />
        <note measure="2" beat="1" duration="2" note="F4" wavetype="Triangle" />
        <note measure="2" beat="3" duration="2" note="A4" wavetype="Triangle" />
	<note measure="3" beat="1" duration="2" note="F4" wavetype="Triangle" />
        <note measure="3" beat="3" duration="2" note="A4" wavetype="Triangle" />
        <note measure="4" beat="1" duration="2" note="E4" wavetype="Triangle"/>
        <note measure="4" beat="3" duration="2" note="D4" wavetype="Triangle"/>
        <note measure="5" beat="1" duration="3" note="D4" wavetype="Triangle"/>
    </instrument>
	<instrument instrument="Chorus">
        <note measure="3" beat="1" delay=".1" wet=".5" dry=".5"/>
        <note measure="3" beat="3" delay=".1" wet=".7" dry=".3"/>
    </instrument>
</score>
```
This was a testing file we used to see if our Chorus effect worked. As you can see it it very similar to the original Synthie test files. We just made effects and the Subtractive wave seperate instruments in the file itself. Effects always come after our actual instrument "Instrument", like the subtractive instrument we implemented. Each note contains specific information that is used in our instrument such as beat, duration, note, wavetype etc.

All score files we are submitting with our project are also present in this repo.
