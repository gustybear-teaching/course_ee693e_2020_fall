---
title: "Peek-a-Boo: I see your smart home activities, even encrypted!

by Abbas Acar
, Hossein Fereidooni
, Tigist Abera
, Amit Kumar Sikder
, Markus Miettinen
,Hidayet Aksu
, Mauro Conti
, Ahmad-Reza Sadeghi
, Selcuk Uluagac"
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
{{< youtube a4yLZ6mdcK4 >}}

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
In order to implement the proposed attack, data needs to be gathered beforehand. With 22 different IoT devices the traffic trace from each is analysed and will be used for the fingerprinting algorithm. There are four main stages of the process, in order they are: Device identification, Device State Identification, Device State Classification, and User Activity Inference. The first stage involves figuring out what device is being used, this is done by comparing features of the transmission such as mean packet length, mean inter-arrival time, and standard deviation in packet lengths to features known from the control data set. The detection stage aims at determining when a device is on or idling. This is done by looking at the density of data being transmitted, when a device is in use a sudden increase of traffic is seen, when the device is done with whatever it is doing, the traffic observed goes back to a minimum. By examining this trait, the classifiers are able to be trained to determine whether something is on. The third stage involves identifying the action a device is in. With feature extraction a large set of information is gathered, by using a classifier called Extra Trees redundant information is taken out in order to make computing more efficient. Comparing the relevant features to what was taken from the controlled experiment the algorithm is able to make an assumption of the action that is happening. The final step involves combining the inferences on the actions of multiple devices throughout a house and comparing the timing, location of device, and what other devices are being used at the same time to make a guess at what the target is doing. In order to make this guess, the model must compare it to actions that are done in a controlled environment with devices set up similarly. To mitigate the leaks, false packets of data are injected into the traffic to obfuscate the trace from being properly analyzed from the attack. 


### Experimentation


{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2020_fall/raw/main/week_11/images/table2.png" title="[Table 2: Characteristics of network traces used in experiments.]" width="300" >}}
Table 2 is done before satge 1, this is the data from looking at the traffic traces of a device in a controlled experiment.

{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2020_fall/raw/main/week_11/images/figure2.png" title="[: Overview of our multi-stage privacy attack]" width="300" >}}
Figure 2 shows a flow chart of the attack model. 

{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2020_fall/raw/main/week_11/images/table3.png" title="[ Evaluation results of device activity detection stage.]" width="300" >}}
Table 3 shows the results of different evaluation metrics of stage 2 where the goal is to detemine if a device is in use.

{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2020_fall/raw/main/week_11/images/table5.png" title="[Hold-out validation results of RF classifier for all
IoT devices.]" width="300" >}}
Table 5 shows the accuracy of different evaluation metrics in determining what action is being done by a device in stage 3.

{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2020_fall/raw/main/week_11/images/table7.png" title="[User activity inference from network traffic data in
a smart home environment]" width="300" >}}
Table 7 is the results from stage 4, where the goal is to determine the actions of a target.

{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2020_fall/raw/main/week_11/images/figure4.png" title="[: Impact of false data injection experiments on the
attack accuracy]" width="300" >}}
Figure 4 is a graph of the accuracy of the attack model if false packets are inserted to the traffic trace.

### Audience Questions

- Smart devices work dependently to provide better user experience whithin a network. How would injecting false packets affect devices that work together? Also, are these devices currently updated in order to mitigate such attacks?
 <br />The injections usually mean a delay in time between devices that work together as it has more data to look through. This could lead to delays and possibly retransmissions.


- Can a different algorithm be implemented to increase accuracy against false data injection?
<br />A different algorithm can be used to offset the effects of the data injection described in the paper. The injection mentioned in the paper is random noise, if that is the case an algorithm can definitely remove it.
 
- How would the false data injection affect user experience?
  <br />Data injections can make it difficult for devices to properly understand a transmission, so there could be multiple delays in actions or even no action if there is enough false data.

 
- As more different kinds of smart devices are introduced, would it make this identification method more or less effective?
 <br />It would make this method more difficult, as this method inherently relies on having analysed the traffic of a device before and using that data as a comparison to the target's.
 
- will the false data affect other devices? if it does, can attackers exploit this to identify a false event?
 <br />The false data will affect other devices in terms of understanding what the transmission is. A false positive can be made as this current method looks mostly at packet length and size as features so a random data injection made to seem like an action can be done.
 
- Can you explain further how spoofed data works? To blend in well with the other packets, it would need the same legitimate reciever IP, how does the reciever know its a spoofed packet?
 <br />The packets would have identifiers to show the receiver that this is what it should read. The spoofer would then look for that identifier and use it.
 
- What would be the effect of random packet transmission do to the accuracy of classifing packets?
 <br />The effects can be seen in figure 4 where the more packets that are injected the less accurate their attack gets.
 
- Do you know how network transmission errors (i.e. malformed packets, retransmissions) are handled in the datasets? Are the filtered out before they are fed into the ML classifier?
 <br />In a real world scenario you would have to find a way to filter out the errors, if not the classifiers would probably not be able to handle it as they currently don't have a protocol for this event.
 
