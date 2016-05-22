---
layout: post
title: RF, A Scope for Video Preservation
---

Along with a waveform monitor and vectorscope, Radio Frequency, or RF, can serve as an excellent real-time signal evaluation metric when preserving early analog videotape. RF exists as a frequency-modulated signal that bypasses the demodulation process found in most video television recorders (VTRs) and decks. As a result you get what could be considered an EKG-like readout of a videotape’s signal characteristics.

![]({{ site.url }}/assets/img/rf_signalexplained.jpg)

When viewed on a calibrated waveform monitor, the signal characteristics of RF consist simply of frequency and amplitude. Portraits of each video head are seen in two adjacent parts of the RF envelope. The larger and more uniform amplitude across the envelope, the greater the signal’s fidelity. This can be achieved by adjusting a deck’s skew and tracking upon tape playback.

It’s relatively easy to set up an RF scope. One was installed and used by the a/v technicians at XFR STN with just under a day of training. I use a dedicated Tek 528 for monitoring RF during 3/4″ UMatic and 1/2″ open reel transfers, but one could easily use an existing waveform monitor that’s already in service. A waveform monitor measuring RF should be set to FLAT, which displays the entire signal frequency range (we typically use the Low Pass/IRE position when we look at video signals). In the case of my Tek 528, the composite input is fed by the selected deck’s RF output (decks like Sony’s BVU950 Umatic VTR will usually a specific output for RF, appropriately labelled “RF OUT”). Composite video is also taken from the selected deck and used as an external reference (REF EXT), in order to synchronize the sweep.

Now that the basics of the RF scope are covered, let’s look at some use cases:

![]({{ site.url }}/assets/img/normalrf1.jpg)

Here is a video signal with what could be considered a “normal” RF envelope. The amplitude is not exactly uniform, but the tracking and skew have been adjusted for optimization.

![]({{ site.url }}/assets/img/rf_partialheadclog1.jpg)

For tapes suffering from sticky-shed syndrome (SSS), the RF scope provides a more intimate account of the head drama unfolding in real time. Above is the resulting RF envelope coming off of a tape with sticky shed, showing one of the two video heads getting “clogged” with loose oxide particles. 

![]({{ site.url }}/assets/img/rf_fullheadclog1.jpg)

Here’s the RF envelope off of the same tape a few seconds later, with both video heads completely clogged. The real-time assessment is crucial for acting quickly to deteriorated tape and preventing any further damage to a tape upon playback.

A previous version of this piece was presented at 2013’s AMIA Conference, with slides available here. I’m naturally indebted to Maurice Schechter’s video engineering wisdom on this topic.