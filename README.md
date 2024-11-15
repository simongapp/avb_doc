# AVB Summary & notes

## What is AVB?

[Audio Video Bridging](http://en.wikipedia.org/wiki/Audio_Video_Bridging) is a term for a collection of IEEE Standards for time sensitive networking which facilitates the transport of high performance audio and video on a LAN:

* [IEEE Std 802.1BA-2011](http://standards.ieee.org/findstds/standard/802.1BA-2011.html), for profiles and overview.
* [IEEE Std 802.1Q-2011](http://standards.ieee.org/findstds/standard/802.1Q-2011.html), for traffic shaping (FQTSS) and the stream reservation protocol (SRP).
* [IEEE Std 802.1AS-2011](http://standards.ieee.org/findstds/standard/802.1AS-2011.html), for time synchronization (gPTP, Generalized Precision Time Protocol).
* [IEEE Std 1722-2016](http://standards.ieee.org/findstds/standard/1722-2016.html), for the Audio Video Transport Protocol (AVTP).
* [IEEE Std 1722.1-2021](https://standards.ieee.org/ieee/1722.1/6670/), for the AVB/TSN Discovery, Enumeration, Connection management, and Control protocol (ATDECC)

## How is media transported with AVB?

IEEE Std 1722-2016 builds on the following standards for media packetization:

* [IIDC (Instrumentation & Industrial Digital Camera) format](http://en.wikipedia.org/wiki/IIDC#IIDC), for the transport of uncompressed low latency digital camera video.
* [IEC 61883-4](https://webstore.iec.ch/en/publication/6067), for the transport of MPEG video streams.
* [IEC 61883-6](https://webstore.iec.ch/en/publication/6069), for the transport of Audio, SMPTE Time Code, and MIDI.
* [AVTP Audio Format(AAF)](https://standards.ieee.org/ieee/1722/5979/), optimized for minimum overhead compared to IEC 61883-6.
* [1394 Trade Association document 1999024](https://audio.dig4e.com/lectures/07-outsourcing_audio_services/1394_Trade_Association_Audio_and_Music_Data_Transmission_Protocol_2.3_2012.pdf), which details SMPTE Time Code encapsulation within IEC 61883-6


## What are the minimum requirements for an AVB switch?

An AVB Switch is required to support:

* IEEE Std. 802.1Q-2011 FQTSS and SRP.
* IEEE Std. 802.1AS-2011 on each AVB enabled ethernet port

## What are the minimum requirements for an AVB device?

An AVB Device that is both an ATDECC Talker and ATDECC Listener is required to support:

* IEEE Std. 802.1Q-2011 FQTSS and SRP.
* IEEE Std. 802.1AS-2011 on each AVB enabled ethernet port
* IEEE Std. 1722.1-2021 ATDECC(AVB/TSN Device Enumeration Discovery and Control)


# Standardization

|Standard|Title|Comment|
|:-|:-|:-|
|IEEE 802.1BA-2011|Audio Video Bridging (AVB) Systems|Identification of participating devices<br>[802.1BA](http://www.ieee802.org/1/pages/802.1ba.html)|
|IEEE 802.1Q-2011|Incorporates IEEE 802.1Qav and IEEE 802.1Qat|[802.1Q-2011](http://www.ieee802.org/1/pages/802.1Q-2011.html)<br>802.1Qav and 802.1Qat are two of the amendments to IEEE Std 802.1Q-2005 that were rolled into IEEE Std 802.1Q-2011.|
|IEEE 802.1Qav|Forwarding and Queuing for Time-Sensitive Streams (FQTSS)|Traffic shaping for AV streams (at both stream source and AVB bridge)<br>[802.1Qav](http://www.ieee802.org/1/pages/802.1av.html) is now known as IEEE Std 802.1Q-2011 Clause 34, "Forwarding and Queuing for time-sensitive streams".|
|IEEE 802.1Qat|Stream Registration Protocol (SRP)|Admission control<br>[802.1Qat](http://www.ieee802.org/1/pages/802.1at.html) is now known as IEEE Std 802.1Q-2011 Clause 35, "Stream Reservation Protocol".|
|IEEE 802.1AS-2011|Timing and Synchronization for Time-Sensitive Applications in Bridged Local Area Networks|Timing and Synchronization for Time-Sensitive Applications <br>gPTP (Generalized Precision Time Protocol)<br>Precise synchronization<br>[802.1AS](http://www.ieee802.org/1/pages/802.1as.html)|
|IEEE 1722-2016|Layer 2 Transport Protocol for Time Sensitive Applications in a Bridged Local Area Network|[IEEE 1722-2011](http://standards.ieee.org/findstds/standard/1722-2011.html)|
|IEEE 1722.1-2021|Device Discovery, Enumeration, Connection Management and Control Protocol for 1722-Based Devices|[IEEE 1722.1-2021](https://standards.ieee.org/ieee/1722.1/6670/)<br>**A**VB/ **T**SN, **D**iscovery, **E**numeration, **C**onnection management, **C**ontrol(**ATDECC**)|

# Links
[AVB/TSN from Jeff Koftinoff](https://avb.statusbar.com/page/)


# Organizations

## Avnu
To help ensure interoperability between devices that implement the AVB standards, the [Avnu Alliance](http://avnu.org) develops device certification for the automotive, consumer, and professional audio and video markets.

![Avnu logo](https://upload.wikimedia.org/wikipedia/commons/thumb/8/80/AVnu_certification_mark.jpg/300px-AVnu_certification_mark.jpg)

## IEEE

The [Time-Sensitive Networking Task Group](https://1.ieee802.org/tsn/) has been evolved from the former IEEE 802.1 Audio Video Bridging (AVB) TG

## AVB Glossary

* AVB := 802.1Q Clause 35 + 802.1Q Clause 24 + 802.1AS
* 802.1Q Clause 35 := MMRP + MVRP + MSRP = "Stream Registration Protocol" (SRP)
* 802.1Q Clause 34 := Forwarding and queuing for time-sensitive streams (FQTSS)
* 802.1AS := “Time Synchronization”	(gPTP)
* L2-based IEEE 1722, 1722.1

|Name|Definition|Example|
|:-|:-|:-|
|Audio Channel|One monophonic audio signal|A single channel of audio|
|Audio Cluster|A group of audio channels in a stream.|A single S/PDIF or AES3 connection which may contain a stereo audio signal with meta-data or an encoded 5.1 surround-sound audio.|
|Audio Map|A static mapping between an Audio Stream’s channels and an Audio Cluster’s channels for Streams and Stream Ports.|The Audio Map allows you to select which Audio Channels within which Audio Clusters in a Stream will be processed. For instance, an Audio Map could select: The “Third Channel” from the second 8 audio channel stream by choosing Channel 0 from Cluster 3 from the second audio stream|
|Audio Unit|Contains signal processing for a single Audio Clock Domain.|If a device had the capability of doing processing in multiple clock domains at the same time, the processing for each clock domain would be done within a separate Audio Unit.|
|AVB Interface|An AVB capable network interface capable of sourcing or sinking Streams and participating in an AVB domain.||
|ATDECC|The Acronym used to refer to IEEE Std 1722.1-2021 (AVB/TSN Discovery Enumeration Connection and Control)||
|ATDECC Entity|A logical object within an End Station that can accept and respond to ATDECC messages.|A device may contain more than one ATDECC Entity. Typically, an AVB device will only contain one ATDECC Entity. As far as the ATDECC Controller is concerned, two entities on one device are indistinguishable from two devices with one entity each. One use case for having two ATDECC Entities in one device is to partition it - allow one user to use one portion of a device while allowing another user on the network to change settings on another portion of the same device but not allowing the two users to affect each other’s settings.|
|Descriptor|A machine-readable description of an object within the ATDECC Entity data Model (AEM). Each descriptor has a Descriptor Type and a Descriptor Index.|An AVB_INTERFACE Descriptor describes an AVB Interface. A JACK_INPUT descriptor describes an Input Jack. There are descriptors for every user-relevant aspect of the device. A controller program can ask a device for these descriptors to learn about the capabilities of the device to present to the user.|
|Entity ID|The EUI-64 identifier (IEEE-defined 64-bit Extended Unique Identifier) of an ATDECC Entity. The Entity ID is based on the device’s ethernet port’s MAC address, the value of the top bits of which are purchased by a manufacturer from the IEEE. The Entity ID for a specific device is a globally unique number.||
|Entity Model ID|The EUI-64 identifier of an ATDECC Entity data Model (AEM). This is a unique number that the manufacturer assigns to device every time a new version of the entity model / object layout / processing structure changes.|If a controller sees two devices on the network with the same Entity Model ID, then it will know that these two devices have identical capabilities and processing structure without having to interrogate both of the devices.|
|Input Stream|A Stream that is received by an AVB Listener.||
|Jack|An ingress or egress point of a non-media-stream signal to or from an ATDECC Entity.|Typically, a Jack represents a physical connector on a device. A Jack may also be called “Captive” if the logical connector is internal only such as a connection to an amplifier for an embedded speaker driver.|
|Localized Description|A textual description of an object within the ATDECC Entity data Model (AEM) which can be represented in multiple languages. These descriptions are only set by the manufacturer of a device and the user can not change them.|An Input Jack may have a Localized Description which would contain the equivalent to the text that is printed on the Silk Screen on the chassis for the Jack. Since manufacturers may have different silkscreens for different markets, the data model can contain the multiple languages as well.|
|Matrix|A collection of orthogonal Controls arranged in a two dimensional array.|8 Audio Channel signals are sent to an 8x16 Matrix. The Matrix contains 128 “level” control points (represented in decibels), one for each combination of 8 inputs and 16 outputs. The Matrix mixes each input to each output based on the cross point level and outputs 16 Audio Channel signals.<br>32 Audio Channel signals are sent to an 32x32 Matrix. The Matrix contains 1024 control points, each with a “level” value (represented in decibels) and “delay” value (represented in seconds), one for each combination of 32 inputs and 32 outputs. The Matrix mixes and delays each input to each output and outputs 32 Audio Channel Signals.|
|Mixer|A Control that combines multiple signals into a single output signal.|8 Audio Channel signals are sent to a Mixer. The Mixer contains one “level” control point per input (represented in decibels). The 8 inputs are mixed with the appropriate levels and outputs one Audio Channel signal.|
|Media component|Fundamental data within an IEEE Std 1722 stream payload.|A single channel of audio<br>A single S/PDIF or AES3 connection containing stereo audio and meta data<br>A single S/PDIF or AES3 connection containing encoded 5.1 audio<br>MPEG video|
|Object Name|A 64 character UTF8 name of an object which the user may be able to set, if the device allows it.|Almost all objects (Descriptors) can have a user settable name. The most likely objects to have user settable names are the device (Entity), Stream Inputs, Stream Outputs, Input Jacks, and Output Jacks.|
|Port|An ingress or egress point of a signal for a Unit (one clock domain).|There are Audio Ports, Video Ports, and Sensor Ports, which correspond to processing done in Audio Units, Video Units, and Sensor Units.|
|Sub-Signal, Signal, Multi-channel Signal|'part of' or 'one or more media components'.|Video portion from MPEG Video data<br>Audio from an MPEG Video data<br>Closed captioning from MPEG Video data<br>A single S/PDIF or AES3 connection.<br>A single audio channel|
|Signal Selector|A Control for switchable signal routing.|A Signal Selector would be used to select audio coming from an analog input jack signal, a digital input jack signal, or an audio channel signal from an AVB stream. Only one source may be selected at a time.|
|Signal Splitter|A Control for splitting a signal into multiple sub-signals.|A Signal Splitter would be used to extract the 6 individual Audio Channels from an encoded 5.1 encoded S/PDIF signal. In this case, there would be one S/PDIF signal going into the Signal Splitter, and there would be 6 single audio channel signals coming out of the signal splitter.<br>A Signal Splitter would be used to extract the video media component and the audio media component from an MPEG transport stream. In this case there would be one MPEG video signal going into the Signal Splitter, and there would be one video signal and one MP3 encoded audio stream signal coming out of the signal splitter|
|Signal Demultiplexer|A Control for demultiplexing a signal into multiple signals.|MIDI data sent over an AVB Stream is transported in an Audio Cluster. One Audio Cluster contains up separate 8 MIDI Cables worth of MIDI data which are all multiplexed together. A Signal Demultiplexer would be used to extract the 8 MIDI cables from the one Audio Cluster into 8 individual MIDI cable signals.|
|Stream|A unidirectional flow of IEEE Std 1722 frames with the same StreamID.|A stream can be a single channel of audio<br>An MPEG video stream with embedded audio<br>An 8 channel stream<br>One or more S/PDIF lines<br>SMPTE time code<br>MIDI messages|
|Stream Input|A Stream Input defines a the part of a device that receives a single AVB Stream and tracks the format and stream status.||
|Stream Port Input|An ingress point of an AVB Stream into an Audio Unit|The Stream Input receives the AVB stream and sends it to the appropriate Audio Unit for processing within a Clock Domain via a Stream Port Input.|

# Dependency
* libsndfile1-dev
* libpcap-dev
* libpci-dev
* libjack-dev
* cmake3
* (cmocka) libcmocka-dev libcmocka0
* ninja
* asciidoc
* byobu



# Terminology

|Name|Full Name|Comment|
|:-|:-|:-|
|AVB|Audio Video Bridging||
|TSN|Time Sensitive Networking||
|[AES3(aka AES/EBU)](https://en.wikipedia.org/wiki/AES3)| a standard for the exchange of digital audio signals between professional audio devices.|Developed by the Audio Engineering Society (AES) and the European Broadcasting Union (EBU).<br>AES3 has been incorporated into the International Electrotechnical Commission's standard [IEC 60958](https://en.wikipedia.org/wiki/IEC_60958) and is available in a consumer-grade variant known as [S/PDIF](https://en.wikipedia.org/wiki/S/PDIF).<br>IEC 60958 Type I—Balanced, XLR<br>![XLR connectors](https://upload.wikimedia.org/wikipedia/commons/thumb/1/15/Xlr-connectors.jpg/450px-Xlr-connectors.jpg)<br>|
|[S/PDIF](https://en.wikipedia.org/wiki/S/PDIF)|Sony/Philips Digital Interface|The signal is transmitted over either a coaxial cable with RCA connectors or a fibre optic cable with TOSLINK connectors. S/PDIF interconnects components in home theatres and other digital high-fidelity systems.<br><br>IEC 60958 Type II—Unbalanced, RCA<br>![RCA connectors](https://upload.wikimedia.org/wikipedia/commons/thumb/9/91/Composite-cables.jpg/450px-Composite-cables.jpg)<br><br>IEC 60958 Type III Optical—Fiber, F05/TOSLINK<br>![TOSLINK connector](https://upload.wikimedia.org/wikipedia/commons/thumb/4/4d/TOS_LINK_clear_cable.jpg/330px-TOS_LINK_clear_cable.jpg)<br><br>Composite Video RCA connector(yellow)<br>![Composite Video RCA connector yellow](https://upload.wikimedia.org/wikipedia/commons/thumb/c/cd/Composite-video-cable.jpg/263px-Composite-video-cable.jpg)<br>|
|SDI|Serial digital interface (SDI)|a family of digital **video** interfaces first standardized by SMPTE (The Society of Motion Picture and Television Engineers) in 1989.<br>![SDI](https://upload.wikimedia.org/wikipedia/commons/thumb/b/b2/BNC_connector_%28male%29.jpg/330px-BNC_connector_%28male%29.jpg)|
|ADAS|Advanced driver-assistance systems||
|MOST|Media Oriented System Transport||
|[LIN](https://en.wikipedia.org/wiki/Local_Interconnect_Network)|(Local Interconnect Network) a very low cost in-vehicle sub-network||
|[FlexRay](https://en.wikipedia.org/wiki/FlexRay)|a general purpose high-speed protocol with safety-critical features|FlexRay is an [automotive network communications protocol](https://en.wikipedia.org/wiki/Vehicle_bus) developed by the FlexRay Consortium to govern on-board automotive computing. It is designed to be faster and more reliable than [CAN](https://en.wikipedia.org/wiki/Controller_Area_Network) and [TTP](https://en.wikipedia.org/wiki/Time-Triggered_Protocol), but it is also more expensive. The FlexRay consortium disbanded in 2009, but the FlexRay standard is now a set of ISO standards, ISO [17458-1](http://www.iso.org/iso/home/store/catalogue_tc/catalogue_detail.htm?csnumber=59804) to [17458-5](http://www.iso.org/iso/home/store/catalogue_tc/catalogue_detail.htm?csnumber=59809). |
|[IVI](https://baike.baidu.com/item/ivi/1069515)|In-Vehicle Infotainment|IVI能够实现包括三维导航、实时路况、IPTV、辅助驾驶、故障检测、车辆信息、车身控制、移动办公、无线通讯、基于在线的娱乐功能及TSP服务等一系列应用，极大的提升的车辆电子化、网络化和智能化水平。|
|ICE|In-Car entertainment|同上|
|RSES/RSE|Rear Seat Entertainment System/Rear Seat Entertainment|同上|
|HUD|Head Up Display||
|AAA2C|Avnu Automotive Advisory Council ||
|[AVTP]((http://avnu.org/wp-content/uploads/2014/05/AVnu-AAA2C_Audio-Video-Transport-Protocol-AVTP_Dave-Olsen.pdf))|Audio Video Transport Protocol||

## Automobile Glossary

### ADAS(Advanced driver-assistance systems)

![composition](https://github.com/feishengfei/avb_doc/raw/master/images/adas01.jpg)

![coverage](https://github.com/feishengfei/avb_doc/raw/master/images/adas02.png)

![coverage](https://github.com/feishengfei/avb_doc/raw/master/images/adas03.jpg)

![history/now/future](https://github.com/feishengfei/avb_doc/raw/master/images/adas_history_now_future.png)

![adas network](https://raw.githubusercontent.com/feishengfei/avb_doc/master/images/adas_require_network.png)

![MATEnet for Automotive Ethernet](https://github.com/feishengfei/avb_doc/raw/master/images/aut_MATEnet_Apps_Infographic_1024px.jpg)

![car avb structure](https://github.com/feishengfei/avb_doc/raw/master/images/car_avb_structure.png)

![car most structure](https://github.com/feishengfei/avb_doc/raw/master/images/car_most_structure.png)

###MOST(Media Oriented System Transport)

![most](https://raw.githubusercontent.com/feishengfei/avb_doc/master/images/most00.png)

![most](https://raw.githubusercontent.com/feishengfei/avb_doc/master/images/most01.png)

![most](https://raw.githubusercontent.com/feishengfei/avb_doc/master/images/most02.png)

![most](https://raw.githubusercontent.com/feishengfei/avb_doc/master/images/most03.png)

![most](https://raw.githubusercontent.com/feishengfei/avb_doc/master/images/most04.png)

![most](https://raw.githubusercontent.com/feishengfei/avb_doc/master/images/most05.png)

![most](https://raw.githubusercontent.com/feishengfei/avb_doc/master/images/most06.png)

![most](https://raw.githubusercontent.com/feishengfei/avb_doc/master/images/most07.png)

![most](https://raw.githubusercontent.com/feishengfei/avb_doc/master/images/most08.png)

![most](https://raw.githubusercontent.com/feishengfei/avb_doc/master/images/most09.png)

![most](https://raw.githubusercontent.com/feishengfei/avb_doc/master/images/most10.png)

![most](https://raw.githubusercontent.com/feishengfei/avb_doc/master/images/most11.png)

![most](https://raw.githubusercontent.com/feishengfei/avb_doc/master/images/most12.png)

