---
title: "02: [Peek-a-Boo: I see your smart home activities, even encrypted!] 

by [Abbas Acar
, Hossein Fereidooni
, Tigist Abera
, Amit Kumar Sikder
, Markus Miettinen
,Hidayet Aksu
, Mauro Conti
, Ahmad-Reza Sadeghi
, Selcuk Uluagac]"
date: 2020-08-30
type: book
commentable: true

# Provide the name of the presenter
summary: "Presenter(s): [Brian Lu and Noha Mohammed]"

# Provide other tags that describe the paper
tags:
- teaching
- ee693e
---

***
## Paper Summary
  With the increased usage of Internet of Things (IoT) Devices, security concerns start to rise. One such concern that is brought up follows WiFi, BLE, and Zigbee devices that are connected together and used in a home or office setting. Physically placing a sniffer within a IoT network and using it to gather information, a multi-stage privacy attack is designed. The attack is made under the assumption that the sniffer would not be able to directly intercept or read the data that is being transmitted within this IoT network, as it will be under encryption. Instead, the sniffer will look at the characteristics of the transmitted data and use machine learning to make inferences on what each of the devices are doing. With this information, the goal is to inference what a person's actions are. The results of such an attack is shown by the paper, and can be seen to breach a person’s privacy with the tested WiFi, BLE, and Zigbee devices with over 90% accuracy in most cases.



***

## Presentation
{{< youtube w7Ft2ymGmfc >}}

[PROVIDE A VIDEO RECORD OF YOUR PRESENTATION]
***

## Review
### Strengths
- The paper gives a very well throught out attack, detailed as well, that matches their goal of infering the actions of a target.
- The figures used were very well done, concise and clear.

### Weaknesses
- The authors seemed to be caught up in thier perception of what the goal was and seemed to ignore other possible scenarios.
- The proposed attack has very strict limitations on what devices can be detected.

### Detalied Comments
The authors of this paper explained very well what steps and actions were taken and the results of such. This can be seen very clearly with the figures that were provided in the paper. Although the graphs and charts seemed plain, it had exactly what was necessary to show outcomes of each stage. Some examples could be the flow chart used to show the four stages in their attack. The attack itself has weaknesses that were partly looked over, although they were acknowledged at the very end, those faults do bring up some interesting points. The attack scenario focuses on trying to ultimately interpret the transmission from IoT devices and infer what someone in the house is doing. Although this was achieved in the paper, as seen by the high accuracy rate, this system would only work if there is one person in the scenario. Given multiple people in the house, the current attack would not work. This was briefly mentioned by the authors, but considering how many households or environments have multiple people this current architecture is extremely limited. The other weakness involves what devices in an IoT network can be a part of their attack. Their adversary model requires each device in a house to be previously researched in order for their machine learning algorithm to be able to work. This needs to be done because each device has unique traits to what their transmission looks like, so if an unidentified device is being used, the algorithim won't be able to properly fingerprint the characteristics from that device's transmission. 

### Implementation



### Experimentation
[PROVIDE FIGURES/TABLE/WRITTEN-PROOF FROM THE PAPER]

{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2020_fall/raw/main/week_11/images/example.png" title="[RESULTS FROM THE PAPER]" width="300" >}}

### Audience QUestions
Smart devices work dependently to provide better user experience whithin a network. How would injecting false packets affect devices that work together? Also, are these devices currently updated in order to mitigate such attacks?


-Can a different algorithm be implemented to increase accuracy against false data injection?

-How would the false data injection affect user experience?

-As more different kinds of smart devices are introduced, would it make this identification method more or less effective?

-will the false data affect other devices? if it does, can attackers exploit this to identify a false event?

-Can you explain further how spoofed data works? To blend in well with the other packets, it would need the same legitimate reciever IP, how does the reciever know its a spoofed packet?

-What would be the effect of random packet transmission do to the accuracy of classifing packets?

-Do you know how network transmission errors (i.e. malformed packets, retransmissions) are handled in the datasets? Are the filtered out before they are fed into the ML classifier?
