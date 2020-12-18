---
title: "01: Practical Operation Extraction from Electromagnetic Leakage
for Side-Channel Analysis and Reverse Engineering by Piieter Robyns, Mariona Di Martino, Dennis Giese, Wim, Lamotte, Peter Quax, Guevara Noubir"
date: 2020-08-30
type: book
commentable: true

# Provide the name of the presenter
summary: "Presenter(s): Japhet Ye, Alvin Yang"

# Provide other tags that describe the paper
tags:
- teaching
- ee693e
---

***
## Paper Summary
In Reverse Engineering, the ability to determine the operation that is being executed on a black-box device is highly important to successfully determine the type of device it is. In this paper, the authors use a side-channel attack that analyzes the electromagnetic (EM) leakage of a processor and using a Machine Learning classification network to determine the operation that is being executed on the processor. They provided 66GB worth of complex traces of EM transmissions of operations that were executed on a Microcontroller with custom firmware. They propose a Convolutional Neural Network as the classifier, with an emphasis on the timing of the operation being executed. They compared this CNN with two other classification strategies to determine the effectiveness of their network. In the end, the have favorable results in a black-box scenario with the CNN models being 52.29% accurate.
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
- The authors do not expand on why the issue of using EM radiation leakage to determine the operation being executed is key to reverse engineering and potentially a serious security breach.


### Detalied Comments
[PROVIDE DETAILED EXPLIANATION OF THE STRENGHS AND WEAKNESSES LISTED ABOVE (>
200 WORDS)]

### Implementation
The authors provide their [source code](https://github.com/rpp0/em-operation-extraction) to us. The language of choice for the analysis is Python and in the code repository, have provided the code for their zero-mean normalized cross-correlation and mean squared error analysis, as well as the code for their 1-D, 2-D, and 1-D with classification Convolutional Neural Networks along with their training algorithm for all the networks. They relied on TensorFlow for the backend of their CNN's by creating a TensorFlow implementation of another paper's CNN called [WaveNet] (https://deepmind.com/blog/article/wavenet-generative-model-raw-audio) whose model theirs are based on. 

The authors also provided their [training and testing datasets](http://wisecdata.ccs.neu.edu/) that they used. The datasets are compromised of EM traces during the execution of their chosen operations. An example trace can be seen below.

{{ < figure src="https://github.com/gustybear-teaching/course_ee693e_2020_fall/raw/main/week_08/images/emtraceex.png" > }}

The architecture of their CNN can be found in the figure below. They feed the multi-dimensional data through 8 convolutional layers to extract different features, mainly instantaneous amplitude and the Short Time Fourier Transform (STFT), to be filtered down to the fully connected network that will then classify the frame. When designing the CNN, they had a few challenges they needed to overcome. Firstly, due to the variability of the operation executions, not all of the traces are of the same length. The authors decided to make the input of fixed length to accommodate the biggest trace size. Because of this, each of the convolutional layers have reduced filters to make the computation more tractable. In compensation, the inputs are widened and pooling layers added so that there is at best equal loss to the base model.

{{ < figure src="https://github.com/gustybear-teaching/course_ee693e_2020_fall/raw/main/week_08/images/cnnarch.png" > }}

The authors also describe two other CNN's for testing, a 2D CNN and another 1D CNN that also extracts extra features. The purpose of the 2D CNN is to determine whether or not the STFT is a viable input feature to a CNN. To accomplish this, the input is given a second dimension by overlapping each of teh traces by a 512-point STFT with the overlap being 50%, resulting in a 512x512 vector as an input. The purpose of the third CNN was to see if they can reasonably identify sub-operations in the trace. While the entire trace may be classified as a SHA1 operation, there are sub-operations within the SHA1 trace that the network does not pick out as features. This CNN's goal is to also classify sub-operations and boxing in the sub-operation in the trace.

### Experimentation
[PROVIDE FIGURES/TABLE/WRITTEN-PROOF FROM THE PAPER]

{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2020_fall/raw/main/week_08/images/example.png" title="[RESULTS FROM THE PAPER]" width="300" >}}

[(OPTIONAL) PROVIDE FIGURES/TABLE/WRITTEN-PROOF FROM YOUR OWN EXPERIMENT]

{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2020_fall/raw/main/week_08/images/example.png" title="[RESULTS FROM YOU]" width="300" >}}

[DISCUSS THE DIFFERENCES AND CAUSES BETWEEN RESULTS, IF ANY]
