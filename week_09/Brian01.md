---
title: "01: [Spotr: GPS Spoofing Detection via Device Fingerprinting] by [M. Foruhandeh, A. Z. Mohammed, G. Kildow, P. Berges, and R. Gerdes]"
date: 2020-08-30
type: book
commentable: true

# Provide the name of the presenter
summary: "Presenters: Brian Lu and Matthew Sahara"

# Provide other tags that describe the paper
tags:
- teaching
- ee693e
- wireless fingerprinting
- gps spoofing
---

***
## Paper Summary
GPS has very quickly taken on a vital role in the world that we currently live in, but GPS has inherent security flaws that are easily exploited. There are two prominent ways to breach the security of a transmission, an overpower attack or a spoofing attack. An overpower attack is to simply apply a more powerful signal than the ones that can be detected by a target, and because GPS receivers automatically lock onto the strongest signal, these types of attacks are the easiest to apply. Spoofing attacks are a little bit more complicated, it relies on trying to imitate a real satellite signal but with different data than what the real satellite is sending. Spotr aims to be a cost effective way to handle these two types of attacks, by implementing their program onto only the GPS receivers instead of other proposed methods which are not as efficient or cost effective. 

## Presentation
{{< youtube w7Ft2ymGmfc >}}

[PROVIDE A VIDEO RECORD OF YOUR PRESENTATION]
***

## Review
### Strengths
- The paper is very well written, in terms of the author's thought process on the steps taken and in describing how their testing worked.
- The explanation on what GPS is, and how the entire transmission and receiving process works is very well thought out and thorough.


### Weaknesses
- Although the paper clearly explains how Spotr was tested there was not much explained about the algorithms used and the backend of Spotr.
- There was too much time spent on trying to explain the background on GPS, related works, and other solutions that have been proposed.


### Detalied Comments
The background information on the topics of GPS, and the testing procedure of Spotr were written very clearly, and in depth. The paper starts with a brief description of the history and architecture of GPS and the problems associated with it’s past, then describes related works and other solutions that have been looked into for overpower and spoofing attacks. The overall breakdown from the different components of GPS, how GPS works, and the explanation of solutions proposed were extremely helpful and in depth. The problem arises when it seems that the paper might have spent too much time on the background topics related to Spotr rather than Spotr itself. Although there is a lot of information regarding the testing process and explanations for their results, there was not a lot pertaining to the choices or testing of the algorithms and design of the MVN and its calssifiers. A lot of attention was placed towards why Spotr is the choice for GPS security but if the paper also included the design constraints about why MVN was chosen, or maybe the thought process behind the testing, it would have been more complete as a paper. As of right now it seems to only point out a problem and provide a solution, without really showing how they came upon that solution.

### Implementation
There are two types of attacks that Spotr is tested against, a physical layer attack where the goal is to change the position, velocity, or time in a satellite signal transmission to a GPS receiver. The second type of attack is replay attack, where real transmissions are spoofed and played back again to a receiver. Spotr takes a signal and extracts the features from it and uses those features inside a MVN distribution and compares it to a predetermined threshold to see if that signal is authentic or fake. The threshold is the point along a MVN distribution where the equal error rate is even on both sides, and in order to obtain that threshold testing needs to be done before Spotr is accurate. The training is done with two data sets, Satgrid and Texbat. Satgrid is the author’s own set of data made to look like an antenna transmission using their own USRP and SDR. Texbat is a tested repository of spoofing traces and clean traces provided by the University of Texas. The Satgrid and Texbat datasets are used to train the threshold till it hits EER, after that Spotr is tested in a few scenarios, detection and tracking over time, at different locations,  multipath, attacks, and different hardware platforms. In scenario one with tracking over time, 40,000 samples from Satgrid are taken and an MVN and threshold was modeled after the data, afterwards a new set of data from a different day was used to see id the modeled MVN and threshold models work. The data is in Table 1. Tracking of location was done in a similar way, with Satgrid providing clean data to train Spotr and then using another set of data from a different location to test the modeled Sport. For training of Multipath Texbat was used, training was done with a multipath free data set and then Spotr was given a set of multipath rich dataset to detect. The scenario with different attacks uses the combined data from the previous test runs and puts data through Spotr which has location, time, and multipath differences from the clean runs. The final test is to see if Spotr models can clearly distinguish authentic and fake signals if it was trained for example with Satgrid but given Texbat data, it was concluded that it would not work.


### Experimentation
[PROVIDE FIGURES/TABLE/WRITTEN-PROOF FROM THE PAPER]

{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2020_fall/raw/main/week_09/images/example.png" title="[RESULTS FROM THE PAPER]" width="300" >}}

[(OPTIONAL) PROVIDE FIGURES/TABLE/WRITTEN-PROOF FROM YOUR OWN EXPERIMENT]

{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2020_fall/raw/main/week_09/images/example.png" title="[RESULTS FROM YOU]" width="300" >}}

[DISCUSS THE DIFFERENCES AND CAUSES BETWEEN RESULTS, IF ANY]

### Audience Questions
- What is the threshold? Or what is the experimental value in which they can differentiate a legitimate or genuine signal? MVN distribution in context.
<br /> 

- Is their spoting detector affected by the number of devices that the spoofer is utilizing?
<br /> 

- Is it possible to further improve the "maximum continuous spoofing time" by feeding more sample points? (By how much? Ex. 100 s to 47.3 s reduction, possible to reduce further?)
<br /> 

- The approach has 100% FPR in cross platform validation. How could this be useful?
<br /> 

- Would an attacker need anything else to bypass SPOTR if they knew what a genuine signal looked like?
<br /> 

- can a strong attacker use the same dataset to generate signal that is closer to genuine signal?
<br /> 

- Why can't an adversary mimic the fingerprinted signal?
<br /> 

- What are the benefits of using MVN apart from being able to handle multi-dimensional data?
<br /> 
