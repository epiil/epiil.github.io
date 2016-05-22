---
layout: post
title: Misunderstanding Metadata
---

Metadata extraction is a daily routine for archivists engaged in digital preservation. While at times this activity appears as a rigid structure with a set of rules and logic, it is oftentimes an imprecise process that requires a level of informed interpretation on the user end. Semantics play a huge role in the information exchange between developers and downstream archival communities.

ExifTool and MediaInfo are two of the most common metadata extraction tools used by archival communities at large. Both tools have been in operation for just over a decade (MediaInfo is in its twelfth year of production, ExifTool in its eleventh), and both are integrated in the back end of countless utilities and libraries including Invisor (MediaInfo), Zencoder (MediaInfo), and MDQC (ExifTool and MediaInfo).

Technical metadata is culled from a variety of sources in audiovisual files – raw stream information, “atoms” in Quicktime files, “chucks” in WAV files, and “packets” in MPEG transport streams to name a few. Metadata extraction tools pull values from these sources and apply strings and human-readable labels in a variety of readouts. A good example of this is a file’s time scale (e.g. 2997/100Hz), which is pulled from Quicktime’s ‘mvhd’ (Movie Header) atom. MediaInfo, for example, will serve this value in its main extraction table in the context of the container codec (eg., Video_Frame_Rate).

Without a properly defined unit of measurement, some values can appear divergent when compared across different sets of tools. A recent test sample came up where a file’s bit-depth per component value differed between both MediaInfo and ExifTool. Using ExifTool on a sample DV video file, ExifTool displays a bit depth value of 24:

![]({{ site.url }}/assets/img/plainviewpoolcarve_exiftoolregular_excerpt.png)

This value differs in comparison to Mediainfo’s extraction of 8 bits, the “correct” value:

![]({{ site.url }}/assets/img/lainviewpoolcarve_mediainforegular_excerpt.png)

Why the discrepancy, if the information appears to come from a single source? The issue is each tool’s individual definition of bit-depth. A bits-per-pixel unit of measurement (eg., 24 bits) is largely preferred by the still image community (a core user group of ExifTool), while the moving image community prefers a bits-per-component value (eg., 8-bit).  Since each tool may cater to a specific archival community, such a unit of measurement needs to be identified by the end user early on in order to put the correct values to use.

To take another example of misidentification on the user end, here are values extracted from a Quicktime-wrapped v210 10-bit uncompressed file, used commonly as a preservation master format for analog video reformatting:

![]({{ site.url }}/assets/img/mpeg4.png)

The Format profile and container ID check out, but what’s with the MPEG-4 value listed as the file’s Format? Well, Quicktime served as the basis for the MPEG-4 format in 1998, and as it became an industry standard it retained the latter’s ISO label. Nowadays archivists associate the MPEG-4 descriptor largely with MPEG-4 Part 10/AVC, otherwise known as H.264. Thus the current usage of MPEG-4 speaks of something else entirely, giving the impression of a strange bedfellow when found in the header of an uncompressed file.

![]({{ site.url }}/assets/img/aja.png)

A similar but slightly more obscure example is the v210 codec hint, “AJA Video Systems Xena.”  Since the v210 codec was originally used by AJA Video Systems (specifically in their Xena analog-to-digital converter), this information has retained in proximity to the codec ID for legacy purposes. A quick glance of this value and one could assume that this relates to the analog-to-digital converter used in the creation of the file itself (AJA converter boxes are still widely in operation). This is not the case. (Note: If one needed such information, it could be derived by the adjacent “encoding library” metadata value).

To speculate as to where certain values are coming from, a more verbose readout of the metadata trace is available with Exiftool using the command `exiftool -v5`. Here, one could parse through the individual sources (in this case, Quicktime atoms):

![]({{ site.url }}/assets/img/plainviewpoolcarve_exiftoolv5_excerpt.png)

A similar verbose readout can be retreived using Mediainfo’s command `mediainfo --Inform="Details;1"`:

![]({{ site.url }}/assets/img/plainviewpoolcarve_mediainfoinformdetails1_excerpt.png)

Tools will oftentimes prioritize metadata coming from a file’s raw stream in their main extraction tables, using container information as a fallback. The verbose trace shows both the bit stream and container metadata, for better or for worse. One interesting and potentially problematic source of metadata is Quicktime’s Sample Description (‘stsd’) atom, seen above in the ExifTool and MediaInfo traces. The ‘stsd’ atom consists of what what values could potentially be in a given file, not what they actually are. The sample description atom contains what its name implies, a table of sample descriptions. Media may have one or more sample descriptions, depending on the number of different encoding schemes used and on the number of files used to store the data.

How does one determine the faithfulness of extracted metadata? Compare the values across tools, and use verbose readouts to check the source atoms, chunks and packets for possible indicators.  Determine units of measurement before the fact and make sure that values aren’t a misapprehension of legacy information. And it’s always helpful to check out the forums for both tools to report bugs and submit feature requests. ExifTool’s forum is here, MediaInfo’s forum is here.

Thanks to Dave Rice and Jerome Martinez for their comments.