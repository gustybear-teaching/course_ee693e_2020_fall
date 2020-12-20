---
title: "01: Zigator: Analyzing the Security of Zigbee-Enabled Smart Homes
 by Dimitrios-Gregios Akestoridis, Madhumitha Harishankar, Michael Weber, Patrik Tague"
date: 2020-08-30
type: book
commentable: true

# Provide the name of the presenter
summary: "Presenter(s): Japhet Ye, Grant Stankaitis"

# Provide other tags that describe the paper
tags:
- teaching
- ee693e
---

***
## Paper Summary
With the rise of the Internet of Things (IoT) where many devices are connected to each other to provide a particular service comes with many costs that manufacturers must deal with in order to keep the cost of such devices low and that does not impede on the devices function. A particular IoT protocol that the researchers are targeting is Zigbee. Controlled by the Zigbee Alliance, it is a low level connectivity protocol that allows low power communication on a network. Many modern IoT devices use this protocol and it is the one of the popular ones implemented in certain devices such as smart locks. They believe that this is a serious threat as smart devices that consumers use to protect themselves physically (such as using a smart door lock), the vulnerabilities goes from an internet security breach to a physical security breach as these devices often interact with the physical world frequently. They design Zigator, a Phython based security analyzer that determines if the network is safe and secure, along with a hardware testbed platform to use in tandem with Zigator.
***

## Presentation
{{< youtube w7Ft2ymGmfc >}}

[PROVIDE A VIDEO RECORD OF YOUR PRESENTATION]
***

## Review
### Strengths
- Strong background information about the protocol and the vulnerabilities that are in it due to the design choices that have been made to maintain such a low power cost.
- Clear explanations about the strategy that adversaries will use to exploit vulnerable networks.

### Weaknesses
- Not a lot of detail in how the program functions and we are only given a high level explanation.

### Detalied Comments
The authors go in depth on the reasonings to why the security vulnerability exists in the first place. Their main finding is that most networks are being configured in a more centralized fashion. Where there exists a main device that acts like a switch where it will route packets sent from one end node to another, and it verifies all the new nodes that are being connected to the network. The vulnerability lies in the new node connection as the process exposes important information to gain access to the network, and since all packets in a centralized Zigbee network is routed to the central device, adversaries can potentially exploits these two facts to gain access to the network.

However, the paper does not go in depth on the software, Zigator, and how it is built. We are told that it a Python based program with a user interface that has the capabilities of running the analysis on the networks, but nothing further than the repository. 


### Implementation
The authors gave the code repositories for the [wireshark profile](https://github.com/akestoridis/wireshark-zigbee-profile), [GNU radio flow graph for Zigator](https://github.com/akestoridis/grc-ieee802154), and the [USB receiver firmware](https://github.com/akestoridis/atusb-attacks). 

The authors set a few objectives to measure the security effectiveness of a device: 1) Authenticity, where the network should not allow unauthorized devices from impersonating other devices, 2) Integrity, where the network must be able to detect and reject tampered packets, 3) Confidentiality, unauthorized devices should not have access to unauthorized information about the network, and 4) Availability, the networking services should be free for devices on the network when it is needed.

The researchers set up the receiver and IEEE 802.15.4 antennae to be able to sniff packets, inject packets, and jam packets. The researchers used Wireshark to organize and colour code the various packets that the radio is receiving via a PCAP configuration file. To jam and inject packets, the researchers used the Scapy library for its ability to parse and modify packets so that the antennae can inject and jam packets.

For packet jamming, the researchers developed selective jammer that jams the reception of a real packet by forcing a state transition to where the receiver no longer actively listens to packets. Specifically, when a RX_START interrupt is detected, we retrieve the packet length and the next byte from the frame buffer until the jamming condition is met. Then we force the receiver to transition from the BUSY_RX state to the PLL_ON state via an injected FORCE_PLL_ON. By doing this, the transmission of the real packet is lost as the receiver is not listening for anything. After a set amount of time, the receiver then goes back to the RX_ON state to start receiving new packets.

### Experimentation
The researchers tested 10 different Zigbee devices that used the SmartThings Hub as the network coordinator. The devices were oriceeded to connect to the network one at a time, all while Zigator was running. 

They were 


[PROVIDE FIGURES/TABLE/WRITTEN-PROOF FROM THE PAPER]

{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2020_fall/raw/main/week_05/images/example.png" title="[RESULTS FROM THE PAPER]" width="300" >}}

[(OPTIONAL) PROVIDE FIGURES/TABLE/WRITTEN-PROOF FROM YOUR OWN EXPERIMENT]

{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2020_fall/raw/main/week_05/images/example.png" title="[RESULTS FROM YOU]" width="300" >}}

[DISCUSS THE DIFFERENCES AND CAUSES BETWEEN RESULTS, IF ANY]