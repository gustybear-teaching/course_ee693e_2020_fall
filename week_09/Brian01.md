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
[PROVIDE ONE PARAGRAPH SUMMARIZING OF THE PAPER (>100 WORDS)]
***

## Presentation
{{< youtube w7Ft2ymGmfc >}}

[PROVIDE A VIDEO RECORD OF YOUR PRESENTATION]
***

## Review
### Strengths
[SUMMARIZE THE STRENGTHS OF THE PAPER IN FULL SENTENCES (>50 WORDS)]
- [STRENGTHS 01]
- [STRENGTHS o1]

### Weaknesses
[SUMMARIZE THE WEAKNESSES OF THE PAPER IN FULL SENTENCES (>50 WORDS)]
- [WEAKNESSES 01]
- [WEAKNESSES o1]

### Detalied Comments
[PROVIDE DETAILED EXPLIANATION OF THE STRENGHS AND WEAKNESSES LISTED ABOVE (>
200 WORDS)]

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
