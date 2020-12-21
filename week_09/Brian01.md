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
The background information on the topics of GPS, and the testing procedure of Spotr were written very clearly, and in depth. The paper starts with a brief description of the history and architecture of GPS and the problems associated with it’s past, then describes related works and other solutions that have been looked into for overpower and spoofing attacks. The overall breakdown from the different components of GPS, how GPS works, and the explanation of solutions proposed were extremely helpful and in depth. The problem arises when it seems that the paper might have spent too much time on the background topics related to Spotr rather than Spotr itself. Although there is a lot of information regarding the testing process and explanations for their results, there was not a lot pertaining to the choices or testing of the algorithms and design of the MVN. A lot of attention was placed towards why Spotr is the choice for GPS security but if the paper also included the design constraints about why MVN was chosen, or maybe the thought process behind the testing or finalizing the MVN algorithms was included as well, it would have been more complete as a paper. As of right now it seems to only point out a problem and provide a solution, without really showing how they came upon that solution.

### Implementation
[PROVIDE DETAILED EXPLIANATION OF THE CODES/DATA PROVIDED BY THE PAPER] (>
200 WORDS)]
[PROVIDE LINK(S) TO THE CODES/DATA PROVIDED BY THE PAPER](https://github.com/gustybear-teaching/course_ee693e_2020_fall)

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
