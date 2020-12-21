---
title: "01:Lost and Found: Stopping Bluetooth Finders from
Leaking Private Information
  by Mira Weller, Jiska Classen, Fabian Ullrich"
date: 2020-08-30
type: book
commentable: true

# Provide the name of the presenter
summary: "Presenter(s): Brian Lu and Noha Mohammed"

# Provide other tags that describe the paper
tags:
- teaching
- ee693e
---

***
## Paper Summary
A Bluetooth finder is a compact battery-powered gadget that can be clipped to valuable objects such as pockets, keychains, or bicycles. The finder retains a Bluetooth link to the user's phone, and the user is alerted automatically of the loss of connection. This paper presents the first detailed study of existing commercial Bluetooth finders for security and privacy. Their analysis reveals some major vulnerability flaws in these smartphone devices products and the related downstream services in the cloud. They also reveal that all cloud-based items examined are leaking more private data than is needed for their respective cloud services. Overall, there is a wide demand for Bluetooth finders, but none of the current models is privacy-friendly. They narrow this gap by creating and integrating PrivateFind to ensure that consumer positions are never exposed to third parties. It is configured to run on hardware close to current finders, enabling vendors to upgrade their systems using PrivateFind.
***

## Presentation
{{< https://www.youtube.com/watch?v=ZFBQW_xu2F4 >}}

[PROVIDE A VIDEO RECORD OF YOUR PRESENTATION]
***

## Review
### Strengths
They analyzed Nut Find3, Tile Mate, Tile Pro, Musegear Finder, Pearl Callstel Key Finder, Gigaset g-tag, and Cube tracker which are top-ranked finders sold worldwide. In addition, a few lesser-known brands are evaluated on the basis of the ST17H26 chip that can be handled through various smartphone applications, including iTracing, iSearching, and FindELFI. Their review uncovers significant concerns with defense and privacy. Both problems were reported to the manufacturers, and most have been resolved by now. This illustrates how certain low-cost Internet of Things (IoT) providers seem to ignore sufficient product protection even today. A solution for protecting privacy has yet to be suggested, considering the number of Bluetooth finders available. Thus, for an IoT platform similar to those used on low-budget finders, they develop and enforce the privacy-preserving secure finder protocol PrivateFind.

- In popular Bluetooth finder ecosystems, they conduct a very good detailed analysis of features, security, and privacy.
-	Development of a new PrivateFind solution that embraces all the functionality observed, but maintains anonymity and privacy.
- Implementation of PrivateFind as an open-source software close to current finder hardware on a low-cost IoT platform.

### Weaknesses
There are extremely dubious several applications, and they do not Note that this information could be obtained for other purposes. These protection and privacy questions can be quickly overcome in the 
For example, by not using the app and the subsequent backend services, Sending to the cloud provider any unwanted results. They've agreed to on a more detailed plan and the design and execution of the 
PrivateFind, a privacy-friendly Bluetooth finder that avoids locations Cloud Server leakage.

- They belive that their sytem can achieve a more advanced security and privacy standard than any
commercial system they analyzed analyzed but they didn't compare their results with the other systems after implemntation.


### Detalied Comments

They carried out a detailed study of the most common Bluetooth finders currently on the market and evaluated their reliability and privacy. There is no design for any of the market-leading goods in a privacy-friendly manner, and many of them have severe security in several stages, defects. They found that All tested products have been developed and introduced without any privacy Emphasis, any of the tested devices pressured the user to build a cloud service account that was not actually necessary for the software to be used. The user's position was unintentionally recorded to a cloud provider by other users without an obvious purpose, any of the products had slight vulnerabilities in terms of security, such as inadequate API defense against unwanted contact. In comparison, some devices have skipped proper certification of the backend services' TLS license, in their corresponding backend, a few devices had significant security bugs that allowed attackers to gain access to other users' private data, and for more than a year, through numerous efforts to get in contact with them over various communication networks, one provider dismissed their reports of those vulnerabilities. The related cloud provider leaks confidential customer information until now, which can be readily accessed.
Their system has the same capabilities and runs on the same or equivalent hardware as other commercial products. This illustrates that Bluetooth finders that are privacy-friendly and safe can be designed without growing hardware costs and without the consumer missing functionality.


### Implementation
They detail how PrivateFind was realized in hardware, firmware, and as an Android app. For hardware Platform. After disassembly of popular Bluetooth finders, they were aware of the Bluetooth Smart Beacon System nRF51822. Its diameter is as small as 20 mm and comes with all the necessary features. They used the Bluetooth Low Energy Development Kit for the nRF51 Series during their development. It is based on the same chip but planned for development, ensuring that the board has more possibilities for input and output and is easier to flash. Constraints remain the same for firmware running on the chip. A fundamental finder example, which activates an alarm on Bluetooth link failure, already comes with the creation platform. Just the configuration, registration, and report protocols for PrivateFind had to be enforced.  For optimizing Hardware. There are also some encryption approaches available on the application site, such as Advanced Encryption Standard (AES). Encryption is Verified in the Missing Finder Data associated data encryption (AEAD), e.g., random nonce AES-CTR for associated data and authentication SHA256-HMAC. It is possible to use various types of encryption depending on the hardware platform.  Finally, the Android Application. The app runs in the background and establishes a Bluetooth link with the developed finder. This is achieved by Nordic Semiconductor using the Android BLE library. A finder's last recorded location is saved locally and be seen in Figure 5b. When the connection is broken, it plays a sound according to the user's tastes on the mobile or on the finder. In addition, the app in the background scans for and tracks other missing finders. 
They use the hardware offload of the Bluetooth controller, if assisted, to retain the battery on the handset.
The privatefind implementation shows in fig.5 

[PROVIDE LINK(S) TO THE CODES/DATA PROVIDED BY THE PAPER](https://github.com/gustybear-teaching/course_ee693e_2020_fall/blob/main/week_11/images/Lost%20and%20Found%20fig.5.png)

### Experimentation
PrivateFind makes the search of finder crowds without leaking private data. It avoids the leakage of data by default, as the server never sees in plaintext any GPS coordinates. Additionally, it makes anonymous Usage of the quest environment for crowds. It helps to discourage both the server resources and other users from monitoring it.  An end-to-end encryption key and an encryption key are defined in the setup process. Identifiers prove that the finder is actually owned by the owner, and it comes in two variants.  
End-to-end Encryption Key. The finder and the smartphone create a pre-shared e2e-key during the setup. By running the configuration process again, the e2e-key can be reset. Per system, keys are individual; any leaked key would only compromise one finder. The e2e-key is symmetrical due to the hardware constraints of the finder. This key never leaves the finder and the mobile after the setup.
Initial and Randomized Identifier. In addition, during initialization, the finder unveils its fixed identifier idinit. This identifier never changes, even though, after repeating the configuration process, the finder is reset. This identifier's format is implementation specific.
Proving Ownership: Only the owner of the finder can execute the configuration mode which resets e2e-key and leaks the unique identity idinit. The owner presses and holds the finder's button to enter the setup mode. The finder reaches startup mode just after clicking the button like this. Otherwise, the reconfiguration would not be approved.
Setup Variants: Although both configuration variants build an e2e-key, replace the idinit, and guarantee ownership through physical access, they vary significantly. The local design, shown in Figure 3a as a sequence diagram, guarantees that a finder is physically accessible to the user. In addition, the configuration shares e2e-key and idinit. The local system does not require a third party and there is no server registration. Note that Idinit can also be reset to a random value during initialization in this local version, since there are no external dependencies on it. At the expense of privacy, the manufacturer-verified configuration improves protection. It offers the same security properties as the local configuration. On top of that, it helps the vendor to verify that the finder is really one they have produced and attaches the Bluetooth configuration with manufacturer-verified encryption. Figure 3b illustrates the overall process.


{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2020_fall/blob/main/week_11/images/Lost%20and%20Found%20fig3a.png" width="300" >}}

[(OPTIONAL) PROVIDE FIGURES/TABLE/WRITTEN-PROOF FROM YOUR OWN EXPERIMENT]

{{< figure src="https://github.com/gustybear-teaching/course_ee693e_2020_fall/blob/main/week_11/images/Lost%20and%20Found%20fig3b.png" title="[RESULTS FROM YOU]" width="300" >}}

[DISCUSS THE DIFFERENCES AND CAUSES BETWEEN RESULTS, IF ANY]
