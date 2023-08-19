<h1 align="center">
 <img src="https://user-images.githubusercontent.com/45159366/142936394-b546784e-231a-4391-9dd8-c686e5a7eee9.png">
  <br />
  PipeWire Guide
</h1>

<a href="https://github.com/mikeroyal?tab=followers">
         <img alt="followers" title="Follow me on Github for Updates" src="https://custom-icon-badges.demolab.com/github/followers/mikeroyal?color=236ad3&labelColor=1155ba&style=for-the-badge&logo=person-add&label=Follow&logoColor=white"/></a> 	

![Maintenance](https://img.shields.io/maintenance/yes/2023?style=for-the-badge)
![Last-Commit](https://img.shields.io/github/last-commit/mikeroyal/pipewire-guide?style=for-the-badge)


#### A guide covering PipeWire including the applications and tools that will make you a better and more efficient with your PipeWire.

**Note: You can easily convert this markdown file to a PDF in [VSCode](https://code.visualstudio.com/) using this handy extension [Markdown PDF](https://marketplace.visualstudio.com/items?itemName=yzane.markdown-pdf).**

<p align="center">
<img src="https://user-images.githubusercontent.com/45159366/144766375-c90533df-e0d6-4893-9131-465fe54e236d.png">
<br />
</p>

# Table of Contents

1. [Getting Started with PipeWire](https://github.com/mikeroyal/PipeWire-Guide#getting-started-with-pipewire)
   * [Developer Resources](#developer-resources)
   * [PipeWire Tools](https://github.com/mikeroyal/PipeWire-Guide#pipewire-tools)
   * [Audio Tools & Libraries to use with PipeWire](https://github.com/mikeroyal/PipeWire-Guide#Audio-Tools--Libraries-to-use-with-PipeWire)
     * [DAW/Sequencers](#dawsequencers)
     * [System utilities - Plugin hosts & adapters](#system-utilities---plugin-hosts--adapters)
     * [System utilities - Network streaming/broadcasting](#system-utilities---network-streamingbroadcasting)
   * [Installing PipeWire for Debian](https://github.com/mikeroyal/PipeWire-Guide#installing-pipewire-for-debian)
   * [Installing PipeWire for Ubuntu](https://github.com/mikeroyal/PipeWire-Guide#installing-pipewire-for-ubuntu)
   * [Installing PipeWire on openSUSE](https://github.com/mikeroyal/PipeWire-Guide#Installing-PipeWire-on-openSUSE)
   * [Installing PipeWire on Arch Linux](https://github.com/mikeroyal/PipeWire-Guide#Installing-PipeWire-on-Arch-Linux)
   * [Setting up OBS Studio](https://github.com/mikeroyal/PipeWire-Guide#Setting-up-OBS-Studio)
      * [Useful OBS Studio 3rd party Plugins & Themes](https://github.com/mikeroyal/PipeWire-Guide#useful-obs-studio-3rd-party-plugins-and-themes)

2. [Wayland Development](https://github.com/mikeroyal/PipeWire-Guide#wayland-development)

# Getting Started with PipeWire

[Back to the Top](#table-of-contents)

[PipeWire](https://pipewire.org) is a server and user space API to deal with multimedia pipelines.It provides a low-latency, graph based processing engine on top of audio and video devices that can be used to support the use cases currently handled by both pulseaudio and JACK. PipeWire was designed with a powerful security model that makes interacting with audio and video devices from containerized applications easy. Nodes in the graph can be implemented as separate processes, communicating with sockets and exchanging multimedia content using fd passing. PipeWire was created by [Wim Taymans](https://gitlab.freedesktop.org/wtaymans), Principal Engineer at Red Hat and co-creator of the GStreamer multimedia framework.
 
 **Key features of PipeWire include:**
 
   - Capture and playback of audio and video with minimal latency.
   - Real-time Multimedia processing on audio and video.
   - Multiprocess architecture to let applications share multimedia content.
   - Seamless support for PulseAudio, JACK, ALSA and GStreamer applications.

### Developer Resources

[Back to the Top](#table-of-contents)

 * [How Audio is implemented with PipeWire](https://docs.pipewire.org/page_audio.html)
 * [PipeWire API](https://docs.pipewire.org/page_api.html)
   - [Client Implementation](https://docs.pipewire.org/page_client_impl.html)
   - [Proxy](https://docs.pipewire.org/page_proxy.html)
   - [Streams](https://docs.pipewire.org/page_streams.html)
   - [Thread Loop](https://docs.pipewire.org/page_thread_loop.html)
     
 * [PipeWire Design](https://docs.pipewire.org/page_pipewire.html)
 * [PipeWire Library](https://docs.pipewire.org/page_library.html)
 * [DMA-BUF sharing](https://docs.pipewire.org/page_dma_buf.html)
 * [PipeWire Daemon](https://docs.pipewire.org/page_daemon.html)
 * [PipeWire Tools](https://docs.pipewire.org/page_tools.html)
 * [PipeWire Session Manager](https://docs.pipewire.org/page_session_manager.html)
 * [PipeWire Modules](https://docs.pipewire.org/page_pipewire_modules.html)
 * [PipeWire - ArchWiki](https://wiki.archlinux.org/title/PipeWire#JACK_clients)
 * [PipeWire - Debian Wiki](https://wiki.debian.org/PipeWire)
 * [PipeWire - Ubuntu Wiki](https://wiki.ubuntu.com/DesktopTeam/TestPlans/Pipewire)
 * [PipeWire - openSUSE Wiki](https://en.opensuse.org/openSUSE:Pipewire)
 * [PipeWire - Void Linux Handbook](https://docs.voidlinux.org/config/media/pipewire.html)
 * [PipeWire - Gentoo Wiki](https://wiki.gentoo.org/wiki/PipeWire)
 * [PipeWire - NixOS Wiki](https://nixos.wiki/wiki/PipeWire)
 * [Virtual Devices - PipeWire Wiki](https://gitlab.freedesktop.org/pipewire/pipewire/-/wikis/Virtual-devices#virtual-devices)
 * [WirePlumber Documentation](https://pipewire.pages.freedesktop.org/wireplumber/)
 * [Linux Audio Foundation](https://linuxaudiofoundation.org/)
 * [Linux Audio Wiki - All apps](http://wiki.linuxaudio.org/apps/all)
 * [LV2 Plugins list](https://lv2plug.in/pages/projects.html)
 * [Wine-VST](https://github.com/Sangeppato/wine-vst)
 * [JACK Audio Wiki](https://github.com/jackaudio/jackaudio.github.com/wiki)

<p align="center">
 <img src="https://user-images.githubusercontent.com/45159366/142779615-d631251b-a2d6-48b4-8194-7985604a8563.png">
  <br />
</p>

How WirePlumber, the PipeWire session manager works. Source: [Collabora](https://www.collabora.com/news-and-blog/blog/2020/05/07/wireplumber-the-pipewire-session-manager/)

## PipeWire Tools

[Back to the Top](#table-of-contents)

[WirePlumber](https://pipewire.pages.freedesktop.org/wireplumber/) is a modular session / policy manager for [PipeWire](https://pipewire.org/) and a GObject-based high-level library that wraps PipeWire’s API, providing convenience for writing the daemon’s modules as well as external tools for managing PipeWire. The WirePlumber daemon implements the session & policy management service. It follows a modular design, having plugins that implement the actual management functionality.

[Core API](https://docs.pipewire.org/group__api__pw__core.html) is used by all clients that need to communicate with the [PipeWire Daemon](https://docs.pipewire.org/page_daemon.html) and provides the necessary structs to interface with the daemon.

[Implementation API](https://docs.pipewire.org/group__api__pw__impl.html) is primarily used by the [PipeWire Daemon](https://docs.pipewire.org/page_daemon.html) itself but also by the [PipeWire Session Manager](https://docs.pipewire.org/page_session_manager.html) and modules/extensions that need to build objects in the graph.

[SPA (Simple Plugin API)](https://docs.pipewire.org/group__api__spa.html) is an extensible API to implement all kinds of plugins.

[PipeWire-rs](https://gitlab.freedesktop.org/pipewire/pipewire-rs) is a Rust bindings for pipewire and SPA libraries.

### Audio Tools & Libraries to use with PipeWire

[Back to the Top](#table-of-contents)

[EasyEffects](https://github.com/wwmm/easyeffects) is an applicaton that provides a limiter, compressor, convolver, equalizer and auto volume and many other plugins for PipeWire applications.

<p align="center">
<img src="https://user-images.githubusercontent.com/45159366/169711136-70c5cdb5-3275-4857-9072-44bdf1041bd2.png">
<br />
</p>

[Helvum](https://gitlab.freedesktop.org/pipewire/helvum) is a GTK-based patchbay for pipewire, inspired by the JACK tool [Catia](https://kx.studio/Applications:Catia).

<p align="center">
<img src="https://user-images.githubusercontent.com/45159366/167501914-f21977bc-6b9a-4367-9340-e7e406d6f429.png">
<br />
</p>

[qpwgraph](https://gitlab.freedesktop.org/rncbc/qpwgraph) is a graph manager dedicated to [PipeWire](https://pipewire.org/), using the [Qt C++ framework](https://qt.io/), based and pretty much like the same of [QjackCtl](https://qjackctl.sourceforge.io/).

<p align="center">
<img src="https://user-images.githubusercontent.com/45159366/167501947-0a149f5a-84ec-4469-a6dd-4c3715d0670d.png">
<br />
</p>

[JamesDSP for Linux](https://github.com/Audio4Linux/JDSP4Linux) is an audio effect processor for PipeWire and PulseAudio clients.

<p align="center">
<img src="https://user-images.githubusercontent.com/45159366/167501954-29d7e852-8a5b-41f8-a3b6-88db39e290d6.png">
<br />
</p>

[NoiseTorch](https://github.com/noisetorch/NoiseTorch) is an easy to use open source application for Linux with PulseAudio or PipeWire. It creates a virtual microphone that suppresses noise, in any application. 

<p align="center">
<img src="https://user-images.githubusercontent.com/45159366/167501959-0ca879bb-8c37-4979-94e7-c253bb50fde7.png">
<br />
</p>

[SuperCollider](http://supercollider.github.io/) is a platform for audio synthesis and algorithmic composition, used by musicians, artists, and researchers working with sound. It consists of:

   * Scsynth, a real-time audio server with hundreds of unit generators ("UGens") for audio analysis, synthesis, and processing
   * Supernova, an alternative server to scsynth with support for parallel DSP on multi-core processors.
   * Sclang, an interpreted programming language that controls the servers.
   * Scide, an editing environment for sclang with an integrated help system.
   
<p align="center">
<img src="https://user-images.githubusercontent.com/45159366/185702191-850c780b-3ae0-420a-9d4e-6804cd682363.png">
<br />
SuperCollider
</p>

[SonoBus](https://sonobus.net) is an easy to use application for streaming high-quality, low-latency peer-to-peer audio between devices over the internet or a local network.

<p align="center">
<img src="https://user-images.githubusercontent.com/45159366/185702345-6ba90601-cb15-42db-a397-bb61350853dd.png">
<br />
SonosBus
</p>

[REAPER](https://www.reaper.fm/) is a complete digital audio production application for computers, offering a full multitrack audio and MIDI recording, editing, processing, mixing and mastering toolset. REAPER supports a vast range of hardware, digital formats and plugins, and can be comprehensively extended, scripted and modified. 

<p align="center">
<img src="https://user-images.githubusercontent.com/45159366/185702830-5135cca3-f113-4391-acdb-839a6813bcc8.png">
<br />
Reaper
</p>

[Soundux](https://soundux.rocks/) is a cross-platform soundboard.

<p align="center">
<img src="https://user-images.githubusercontent.com/45159366/185702167-32c43bff-211e-4545-9234-7cb28f81646d.png">
<br />
Soundux
</p>

[JUCE](https://juce.com/) is an open-source cross-platform C++ application framework for desktop and mobile applications, including VST, VST3, AU, AUv3, RTAS and AAX audio plug-ins. 

<p align="center">
<img src="https://user-images.githubusercontent.com/45159366/185703182-4af9f991-288d-413c-8a0c-b475a78be518.png">
<br />
JUCE
</p>

[Helio Workstation](https://helio.fm/) is free and open-source music sequencer, designed to be used on all major platforms.

<p align="center">
<img src="https://user-images.githubusercontent.com/45159366/185702188-faddbe40-a37d-469b-8b96-80a9d18101b1.png">
<br />
Helio
</p>

[Zrythm](https://www.zrythm.org/) is a digital audio workstation designed to be featureful and easy to use. It offers streamlined editing workflows with flexible tools, limitless automation capabilities, powerful mixing features, chord assistance and support for various plugin and file formats.

<p align="center">
<img src="https://user-images.githubusercontent.com/45159366/185702208-030afa5f-b1d3-4068-9589-1544a33e0657.png">
<br />
Zrythm
</p>

[Yabridge](https://github.com/robbert-vdh/yabridge) is a modern and transparent way to use Windows VST2 and VST3 plugins on Linux.

<p align="center">
<img src="https://user-images.githubusercontent.com/45159366/185702206-b94af236-fcea-455a-bbec-df304b6fcfaf.png">
<br />
Yabridge
</p>
 
[Squeezer](https://github.com/mzuther/Squeezer) is a flexible general-purpose audio compressor with a touch of citrus.

<p align="center">
<img src="https://user-images.githubusercontent.com/45159366/185702199-6c3e2016-5387-43d7-9c5c-639a61c39ef8.png">
<br />
Squeezer
</p>

[Matchering 2.0](https://github.com/sergree/matchering) is a novel [Containerized Web Application](https://github.com/sergree/matchering#docker-image---the-easiest-way) and [Python Library](https://pypi.org/project/matchering) for audio matching and [mastering](https://en.wikipedia.org/wiki/Audio_mastering).

[QjackCtl](https://qjackctl.sourceforge.io/) is a simple Qt application to control the JACK sound server daemon, specific for the Linux Audio Desktop infrastructure.

[Catia](https://kx.studio/Applications:Catia) is a JACK Patchbay, with some neat features like A2J bridge support and JACK Transport. It's supposed to be as simple as possible so it can work nicely on non-Linux platforms. 

[JACK Audio Connection Kit AKA JACK](https://jackaudio.org/) is a professional sound server daemon that provides real-time, low-latency connections for both audio and MIDI data between applications that implement its API. JACK can be configured to send audio data over a network to a main machine, which then outputs the audio to a physical device. This can be useful to mix audio from a number of linked computers without requiring additional cables or hardware mixers, and keeping the audio path digital for as long as possible.

[JACK2](https://github.com/jackaudio/jack2) is a C++ version of the JACK low-latency audio server for multi-processor machines. It is a new implementation of the JACK server core features that aims at removing some limitations of the JACK1 design. The activation system has been changed for a data flow model and lock-free programming techniques for graph access have been used to have a more dynamic and robust system.

[Cava](https://github.com/karlstav/cava) is a bar spectrum audio visualizer for terminal (ncurses) or desktop (SDL).

[Musikcube](https://musikcube.com/) is a cross-platform, terminal-based audio engine, library, player and server written in c++.

[LabSound](https://github.com/LabSound/LabSound) is a C++ graph-based audio engine. 

[Pure Data](https://github.com/pure-data/pure-data) is a free real-time computer music system.

[OpenMAX™](https://www.khronos.org/openmax/) is a cross-platform API that provides comprehensive streaming media codec and application portability by enabling accelerated multimedia components to be developed, integrated and programmed across multiple operating systems and silicon platforms.

[H.264(AVC)](https://en.wikipedia.org/wiki/H.264/MPEG-4_AVC) is a video compression standard based on block-oriented and motion-compensated integer-DCT coding that defines multiple profiles (tools) and levels (max bitrates and resolutions) with support up to 8K.

[H.265(HEVC)](https://en.wikipedia.org/wiki/High_Efficiency_Video_Coding) is a video compression standard that is the successor to H.264(AVC). It offers a 25% to 50% better data compression at the same level of video quality, or improved video quality at the same bit-rate.

[FFmpeg](https://ffmpeg.org) is a leading multimedia framework that can decode, encode, transcode, mux, demux, stream, filter and play pretty much anything that humans and machines have created. It supports the most obscure ancient formats up to the cutting edge ones on multiple platforms such as Windows, macOS, and Linux.

[GStreamer](https://gstreamer.freedesktop.org/) is a library for constructing graphs of media-handling components. The applications it supports range from simple Ogg/Vorbis playback, audio/video streaming to complex audio (mixing) and video (non-linear editing) processing. Applications can take advantage of advances in codec and filter technology transparently.

[Media Source Extensions (MSE)](https://www.w3.org/TR/media-source/) is a [W3C specification](https://github.com/w3c/media-source) that allows JavaScript to send byte streams to media codecs within Web browsers that support HTML5 video and audio. Also, this allows the implementation of client-side prefetching and buffering code for streaming media entirely in JavaScript.

[WebRTC](https://webrtc.org/) is an open-source project that adds real-time communication capabilities to your application that works on top of an open standard. It supports video, voice, and generic data to be sent between peers, allowing developers to build powerful voice- and video-communication solutions.

### DAW/Sequencers

[Back to the Top](#table-of-contents)

* [dino](http://dino.nongnu.org/) is an integrated MIDI piano roll editor and sequencer engine.
* [friniika](http://www.frinika.com/) is a complete music workstation for Windows/Linux/macOS.
* [Harrison Mixbus](http://harrisonconsoles.com/site/mixbus.html) is the first full-featured DAW with true analog style mixing.
* [helio-workstation](https://helio.fm/) is a free linear-based music for macOS, Linux, Windows, iOS and Android, with clean interface, version control, synchronization between devices, undo history, and more. 
* [Laborejo](https://laborejo.org/laborejo/) is a MIDI sequencer based on classical music notation. 
* [meterec](https://meterec.sourceforge.net/) is a minimalistic multi track recorder.
* [muse](https://muse-sequencer.github.io/) is a Qt4-based audio/MIDI sequencer.
* [ossia score](https://ossia.io/) is an interactive sequencer with intelligent timelines supporting audio, video, OSC, MIDI, DMX and more.
* [Patroneo](https://www.laborejo.org/patroneo)  is an easy to use, pattern based midi sequencer.
* [qtractor](https://qtractor.sourceforge.net/) is a MIDI/Audio multi-track sequencer application.
* [REAPER](https://www.reaper.fm/) is a complete digital audio production application for computers, offering a full multitrack audio and MIDI recording, editing, processing, mixing and mastering toolset.
* [sequencer64](https://github.com/ahlstromcj/sequencer64) is a real-time MIDI sequencer, a major reboot of seq24 with many new features.
* [Stargate DAW](https://github.com/stargatedaw/stargate) is a Cross-platform, all-in-one DAW and plugin suite.
* [Zrythm](https://www.zrythm.org/) is a highly automated and intuitive digital audio workstation.


### System utilities - Plugin hosts & adapters

[Back to the Top](#table-of-contents)

* [carla-lv2/vst](https://kxstudio.linuxaudio.org/Applications:Carla) is an audio plugin host (LV2/VST plugins).
* [festige](https://www.syntheway.net/FeSTige.htm) is a graphical interface for fst and dssi-vst, allowing you to run Windows VST plugins on Linux. 
* [dssi-vst](http://breakfastquay.com/dssi-vst/) is an Adapter for VST an VSTi audio plugins.
* [linvst](https://github.com/osxmidi/LinVst) is a LinVst enables Windows VSTs to be used as Linux VSTs in Linux VST-capable DAWs.
* [mod-host](https://github.com/moddevices/mod-host) is a LV2 host for JACK, controllable via socket or command line.
* [synthpod](https://open-music-kontrollers.ch/lv2/synthpod/) is a Synthpod is an LV2 host.
* [vst-bridge](https://github.com/abique/vst-bridge) is a VST bridge for Windows vst on Linux.
* [wineasio](https://sourceforge.net/projects/wineasio/) is a Wine ASIO driver for JACK.
* [yabridge](https://github.com/robbert-vdh/yabridge) is a modern and transparent way to use Windows VST2 and VST3 plugins on Linux

### System utilities - Network streaming/broadcasting

[Back to the Top](#table-of-contents)

* [autoradio](https://autoradiobc.sf.net) is a radio automation software.
* [gpac](https://gpac.wp.mines-telecom.fr/) is a GPAC Project on Advanced Content.
* [jamulus](https://jamulus.io/) is a Low latency audio server/client for collaborative music sessions.
* [larigira](https://git.lattuga.net/boyska/larigira) is a radio automation software based on MPD.
* [Open Broadcaster Software](https://obsproject.com/) is a recorder and streamer for live video content.
* [vlc-bin](https://www.videolan.org/vlc/) is a multimedia player and streamer (headless).
* [vlc](https://www.videolan.org/vlc/) is a multimedia player and streamer.
* [zita-njbridge](https://kokkinizita.linuxaudio.org/linuxaudio/downloads/index.html) is a Jack clients to transmit multichannel audio over a local IP network.

## Installing PipeWire for Debian

[Back to the Top](#table-of-contents)

<p align="center">
 <img src="https://user-images.githubusercontent.com/45159366/185811902-d09f898c-a30f-4a24-af42-4e0d5cbd8f7f.png">
  <br />
</p>


* [PipeWire - Debian Wiki](https://wiki.debian.org/PipeWire)

Before you begin make sure to cd ```/etc/apt/sources.list.d``` in the terminal.

### Install PipeWire

```sudo apt install pipewire```

**Create this empty file:**

```# touch /etc/pipewire/media-session.d/with-pulseaudio```

Create a pipewire-pulse service by copying the example files:

```# cp /usr/share/doc/pipewire/examples/systemd/user/pipewire-pulse.* /etc/systemd/user/```

#### Run these three commands as your regular user (not as root):

**Check for new service files with:**

```systemctl --user daemon-reload```

**Disable and stop the PulseAudio service with:**

```systemctl --user --now disable pulseaudio.service pulseaudio.socket```

**Enable and start the new pipewire-pulse service with:**

```systemctl --user --now enable pipewire pipewire-pulse```

**This will configure PipeWire to activate its PulseAudio replacement daemon. Verify that it's enabled by running:**

```LANG=C pactl info | grep '^Server Name'```

It should say **Server Name: PulseAudio (on PipeWire 0.3.19)**.

**To ensure this continues working after a reboot. You will need to "mask" the PulseAudio service by running:**

```systemctl --user mask pulseaudio```


## Installing PipeWire for Ubuntu

[Back to the Top](#table-of-contents)

<p align="center">
 <img src="https://user-images.githubusercontent.com/45159366/218303402-8bd864ab-42cd-406d-b624-c33f9343e16e.png">
  <br />
</p>


* [PipeWire - Ubuntu Wiki](https://wiki.ubuntu.com/DesktopTeam/TestPlans/Pipewire)

**Note:** For those using Pop!_OS 22.04 or later PipeWire is already setup by default. PipeWire will be default starting with [Ubuntu 22.10 (October 2022)](https://discourse.ubuntu.com/t/pipewire-as-a-replacement-for-pulseaudio/28489/30). So these install instructions are for those running older Ubuntu versions like 22.04 and 20.04 LTS releases.

Before you begin make sure to cd ```/etc/apt/sources.list.d``` in the terminal.

### Install PipeWire

```sudo apt install pipewire```

**Create this empty file:**

```# touch /etc/pipewire/media-session.d/with-pulseaudio```

Create a pipewire-pulse service by copying the example files:

```# cp /usr/share/doc/pipewire/examples/systemd/user/pipewire-pulse.* /etc/systemd/user/```

#### Run these three commands as your regular user (not as root):

**Check for new service files with:**

```systemctl --user daemon-reload```

**Disable and stop the PulseAudio service with:**

```systemctl --user --now disable pulseaudio.service pulseaudio.socket```

**Enable and start the new pipewire-pulse service with:**

```systemctl --user --now enable pipewire pipewire-pulse```

**This will configure PipeWire to activate its PulseAudio replacement daemon. Verify that it's enabled by running:**

```LANG=C pactl info | grep '^Server Name'```

It should say **Server Name: PulseAudio (on PipeWire 0.3.19)**.

**To ensure this continues working after a reboot. You will need to "mask" the PulseAudio service by running:**

```systemctl --user mask pulseaudio```

## Installing PipeWire on openSUSE

[Back to the Top](#table-of-contents)

<p align="center">
<img src="https://user-images.githubusercontent.com/45159366/185811690-0f12b042-585a-4f62-84c6-dadd38fdf8a3.png">
<br />
</p>

* [PipeWire - openSUSE Wiki](https://en.opensuse.org/openSUSE:Pipewire)

**Note: With [openSUSE TumbleWeed](https://get.opensuse.org/tumbleweed/) PipeWire comes installed already, but for [openSUSE Leap](https://get.opensuse.org/leap/15.4/) you will need to install PipeWire.**

 ### Install PipeWire packages:
 
 ```sudo zypper in pipewire pipewire-pulseaudio pipewire-alsa pipewire-aptx```
 
### Then enable pipewire sockets and session manager:

```systemctl --user enable --now pipewire.socket```

```systemctl --user enable --now pipewire-pulse.socket```

```systemctl --user enable --now wireplumber.service```
 
 
## Installing PipeWire on Arch Linux

[Back to the Top](#table-of-contents)

<p align="center">
<img src="https://user-images.githubusercontent.com/45159366/185810674-cde93673-afaa-43f9-9b77-c542d0463c31.png">
<br />
</p>

 * [PipeWire - ArchWiki](https://wiki.archlinux.org/title/PipeWire#JACK_clients)
 * [Pipewire and JACK on Arch Linux by Scott Petersen](https://www.scottericpetersen.com/2022/05/27/pipewire-and-jack-on-arch-linux/)
 
 **Note: [Helvum](https://gitlab.freedesktop.org/pipewire/helvum) (GTK patchbay for PipeWire).**
 
 ```sudo pacman -S pipewire pipewire-alsa pipewire-pulse pipewire-jack wireplumber helvum```

 or
 
  **Note: [qpwgraph](https://github.com/rncbc/qpwgraph) (PipeWire Graph Qt GUI Interface).**
 
 ```sudo pacman -S pipewire pipewire-alsa pipewire-pulse pipewire-jack wireplumber qpwgraph```
 
 
### Then enable pipewire sockets and session manager:

```systemctl --user enable --now pipewire.socket```

```systemctl --user enable --now pipewire-pulse.socket```

```systemctl --user enable --now wireplumber.service```
 
## Setting up OBS Studio

[Back to the Top](#table-of-contents)

<p align="center">
 <img src="https://user-images.githubusercontent.com/45159366/185703842-0926e10a-467a-471c-b5f6-b74df4e460d9.png">
  <br />
</p>

[OBS (Open Broadcaster Software)](https://obsproject.com/) is free and open source software for video recording and live streaming. Stream to Twitch, YouTube and many other providers or record your own videos with high quality H264 / AAC encoding. OBS Studio added **native PipeWire and Wayland support in version 27**. 

 [![OBS Studio Flatpak on Flathub](https://user-images.githubusercontent.com/45159366/185704745-32111c92-2687-49f6-9247-6e925f6a41a6.png)](https://flathub.org/apps/details/com.obsproject.Studio)
 
 <p align="center">
 <img src="https://user-images.githubusercontent.com/45159366/185704748-217443ac-57e3-4ab3-ba74-6d09c2fe62fb.png">
  <br />
  OBS Studio
</p>


 * [OBS PipeWire Audio Capture](https://github.com/dimtpap/obs-pipewire-audio-capture) is a plugin adds 3 sources for OBS Studio tocapture audio outputs, inputs and applications using PipeWire.
 
 * [OBS Scale To Sound](https://github.com/dimtpap/obs-scale-to-sound) is a plugin for OBS Studio that adds a filter which makes a source scale based on the audio levels of any audio source you choose.
 
  * [OBS Studio Fully-loaded](https://github.com/wimpysworld/obs-fully-loaded) is a script for Ubuntu/Debian-based systems that installs OBS Studio along with pre-loaded extra features and plugins. This project is developed and maintained by [Martin Wimpress](https://github.com/wimpysworld/).
 
 ### Useful OBS Studio 3rd party plugins and themes.

  * **[Advanced Scene Switcher](https://github.com/WarmUpTill/SceneSwitcher)** plugin; an automated scene switcher.
  * **[Audio Pan](https://github.com/norihiro/obs-audio-pan-filter)** plugin; control stereo pan of audio source.
  * **[Browser](https://github.com/obsproject/obs-browser)** plugin; CEF-based OBS Studio browser plugin.
  * **[Directory Watch Media](https://github.com/exeldro/obs-dir-watch-media)** plugin; filter you can add to media source to load the oldest or newest file in a directory.
  * **[Downstream Keyer](https://github.com/exeldro/obs-downstream-keyer)** plugin; add a Downstream Keyer dock.
  * **[Dynamic Delay](https://github.com/exeldro/obs-dynamic-delay)** plugin; filter for dynamic delaying a video source.
  * **[Freeze Filter](https://github.com/exeldro/obs-freeze-filter)** plugin; freeze a source using a filter.
  * **[Gradient Source](https://github.com/exeldro/obs-gradient-source)** plugin; adding gradients as a Soource.
  * **[GStreamer](https://github.com/fzwoch/obs-gstreamer)** plugins; feed GStreamer launch pipelines into OBS Studio and use GStreamer encoder elements.
  * **[Move Transition](https://github.com/exeldro/obs-move-transition)** plugin; move source to a new position during scene transition.
  * **[Multi Source Effect](https://github.com/norihiro/obs-multisource-effect)** plugin; provides a custom effect to render multiple sources.
  * **[NDI](https://github.com/Palakis/obs-ndi)** plugin; Network A/V via NewTek's NDI.
  * **[NvFBC](https://gitlab.com/fzwoch/obs-nvfbc)** plugin; screen capture via NVIDIA FBC API. Requires [NvFBC patches for Nvidia drivers](https://github.com/keylase/nvidia-patch) for consumer grade GPUs.
  * **[Pulse App Capture](https://github.com/jbwong05/obs-pulseaudio-app-capture)** plugin; capture application audio from PulseAudio.
  * **[Soundboard](https://github.com/cg2121/obs-soundboard)** plugin; adds a soundboard dock.
  * **[Source Copy](https://github.com/exeldro/obs-source-copy)** plugin; adds copy and paste options to the tools menu.
  * **[Source Dock](https://github.com/exeldro/obs-source-dock)** plugin; create a Dock for a source, which lets you see audio levels, change volume and control media. 
  * **[Recursion Effect](https://github.com/exeldro/obs-recursion-effect)** plugin; recursion effect filter.
  * **[Replay Source](https://github.com/exeldro/obs-replay-source)** plugin; slow motion replay async sources from memory.
  * **[RGB Levels](https://github.com/petrifiedpenguin/obs-rgb-levels-filter)** plugin; simple filter to adjust RGB levels.
  * **[RTSPServer](https://github.com/iamscottxu/obs-rtspserver/)** plugin; encode and publish to a RTSP stream.
  * **[Scale to Sound](https://github.com/Qufyy/obs-scale-to-sound)** plugin; adds a filter which makes a source scale based on the audio levels of any audio source you choose
  * **[Scene Collection Manager](https://github.com/exeldro/obs-scene-collection-manager)** plugin; filter, backup and restore Scene Collections.
  * **[Scene Notes Dock](https://github.com/exeldro/obs-scene-notes-dock)** plugin; create a Dock for showing and editing notes for the current active scene.
  * **[Source Record](https://github.com/exeldro/obs-source-record)** plugin; make sources available to record via a filter.
  * **[Source Switcher](https://github.com/exeldro/obs-source-switcher)** plugin; to switch between a list of sources.
  * **[Spectralizer](https://github.com/univrsal/spectralizer)** plugin; audio visualization using fftw.
  * **[StreamFX](https://github.com/Xaymar/obs-StreamFX)** plugin; collection modern effects filters and transitions.
  * **[Teleport](https://github.com/fzwoch/obs-teleport)** plugin; open NDI-like replacement.
  * **[Text Pango](https://github.com/kkartaltepe/obs-text-pango)** plugin; Provides a text source rendered using Pango with multi-language support, emoji support, vertical rendering and RTL support.
  * **[Text PThread](https://github.com/norihiro/obs-text-pthread)** plugin; Rich text source plugin with many advanced features.
  * **[Time Warp Scan](https://github.com/exeldro/obs-time-warp-scan)** plugin; a time warp scan filter.
  * **[Transition Table](https://github.com/exeldro/obs-transition-table)** plugin; customize scene transitions.
  * **[Virtual Cam Filter](https://github.com/exeldro/obs-virtual-cam-filter)** plugin; make sources available to the virtual camera via a filter
  * **[VNC Source](https://github.com/norihiro/obs-vnc)** plugin; VNC viewer that works as a source.
  * **[Websockets](https://github.com/Palakis/obs-websocket)** plugin; remote-control OBS Studio through WebSockets, compatible with [StreamControl](https://play.google.com/store/apps/details?id=dev.t4ils.obs_remote&hl=en).

# Wayland Development
[Back to the Top](https://github.com/mikeroyal/PipeWire-Guide#table-of-contents)

<p align="center">
 <img src="https://user-images.githubusercontent.com/45159366/104235197-79cf4e00-5409-11eb-97a6-a12f7bd8ad2a.png">
  <br />
</p>

## Wayland Learning Resources

[Back to the Top](#table-of-contents)

[Wayland](https://wayland.freedesktop.org) is a protocol for a compositor to talk to its clients as well as a C library implementation of that protocol. The compositor can be a standalone display server running on Linux kernel modesetting and evdev input devices, an [X application](https://www.x.org/wiki/XServer/), or a wayland client itself.

 * [Wayland Architecture](https://wayland.freedesktop.org/architecture.html)

 * [Wayland Documentation](https://wayland.freedesktop.org/docs/html/)

 * [Sotfware Toolkits that have Wayland support right now](https://wayland.freedesktop.org/toolkits.html)

 * [Contribution instructions for Wayland](https://gitlab.freedesktop.org/wayland/wayland/blob/master/CONTRIBUTING.md)

 * [Contribution instructions for Weston](https://gitlab.freedesktop.org/wayland/weston/blob/master/CONTRIBUTING.md)

 * [Reporting Wayland bugs](https://gitlab.freedesktop.org/wayland/wayland/issues)

 * [Reporting Weston bugs](https://gitlab.freedesktop.org/wayland/weston/issues)

 * [WSLG: X11 and Wayland Applications in Windows Subsystem for Linux(WSL2)](https://linuxplumbersconf.org/event/9/contributions/611/attachments/702/1298/XDC2020_-_X11_and_Wayland_applications_in_WSL.pdf)

 * [Qt Wayland Compositor](https://doc.qt.io/qt-5/qtwaylandcompositor-index.html)

 * [Qt Wayland Compositor Examples](https://doc.qt.io/qt-5/qtwaylandcompositor-examples.html)

 * [Wayland on ArchWiki](https://wiki.archlinux.org/index.php/Wayland)

 * [Sway on ArchWiki](https://wiki.archlinux.org/index.php/Sway)

 * [Wayland on Ubuntu Wiki](https://wiki.ubuntu.com/Wayland)

 * [Wayland on Debian Wiki](https://wiki.debian.org/Wayland)

 * [The Wayland Display Server on Fedora Docs](https://docs.fedoraproject.org/en-US/fedora/rawhide/system-administrators-guide/Wayland/)

 * [Wayland features on Fedora Project Wiki](https://fedoraproject.org/wiki/Wayland_features)

 * [Wayland on GNOME Wiki](https://wiki.gnome.org/Initiatives/Wayland)

 * [KWin/Wayland on KDE Community Wiki](https://community.kde.org/index.php?title=KWin/Wayland)

 * [Wayland Desktop Landscape on Gentoo Wiki](https://wiki.gentoo.org/wiki/Wayland_Desktop_Landscape)

 * [Wayland in Void Linux Handbook](https://docs.voidlinux.org/config/graphical-session/wayland.html)

 * [Wayland on Enlightenment DE](https://www.enlightenment.org/about-wayland)

## Wayland Tools

[Back to the Top](#table-of-contents)

[Weston](https://gitlab.freedesktop.org/wayland/weston) is a lightweight and functional Wayland compositor.

[XWayland](https://wayland.freedesktop.org/xserver.html) is an X Server running as a Wayland client(for backwards compatibility), allowing the [Xorg server](https://www.x.org/wiki/XServer/) can be modified to use wayland input devices for input and forward either the root window or individual top-level windows as wayland surfaces.

[KWin](https://community.kde.org/KWin/Wayland) is the window manager for the KDE Plasma Desktop. It gives you complete control over your windows, making sure they're not in the way but aid you in your task. It paints the window decoration, the bar on top of every window with (configurable) buttons like close, maximize and minimize.

[Qt](https://www.qt.io/) is the faster, smarter way to create innovative devices, modern UIs & applications for multiple screens. It is one of the most popular toolkits for the Wayland and X11 windowing.

[GTK](https://www.gtk.org/) is a free and open source cross-platform widget toolkit for creating graphical user interfaces developed by [GNOME Project](https://www.gnome.org/). It is one of the most popular toolkits for the Wayland and X11 windowing.

[NVIDIA Wayland EGL External Platform library](https://github.com/NVIDIA/egl-wayland) is a work-in-progress implementation of a EGL External Platform library to add client-side Wayland support to EGL on top of EGLDevice and EGLStream families of extensions.

[NVIDIA EGL External Platform Interface](https://github.com/NVIDIA/eglexternalplatform) is a work-in-progress specification of the EGL External Platform interface for writing EGL platforms and their interactions with modern window systems on top of existing low-level EGL platform implementations. This keeps window system implementation specifics out of EGL drivers by using application-facing EGL functions.

[Sway](https://swaywm.org/) is an [i3](https://i3wm.org/)-compatible Wayland compositor.

[wlroots](https://github.com/swaywm/wlroots) is a modular Wayland compositor library.

[WayfireWM](https://github.com/WayfireWM/wayfire) is a 3D Wayland compositor, inspired by [Compiz](https://launchpad.net/compiz) and based on [wlroots](https://github.com/swaywm/wlroots).

[SDDM](https://github.com/sddm/sddm) is a modern display manager for X11 and Wayland aiming to be fast, simple and beautiful. It uses modern technologies like QtQuick, which in turn gives the designer the ability to create smooth, animated user interfaces.

[x11docker](https://github.com/mviereck/x11docker) is an application that you allows to run graphical desktop applications (and entire desktops) in Docker Linux containers.

[Mako](https://github.com/emersion/mako) is alightweight notification daemon for Wayland. It also works on [Sway](https://swaywm.org/).

[Wayland-rs](https://github.com/Smithay/wayland-rs) is a Rust implementation of the wayland protocol (client and server).

[Wine-wayland](https://github.com/varmd/wine-wayland) is an application that allows you to running DX9/DX11 and Vulkan games using pure Wayland and Wine/DXVK.

## Contribute

- [x] If would you like to contribute to this guide simply make a [Pull Request](https://github.com/mikeroyal/PipeWire-Guide/pulls).

## License
[Back to the Top](https://github.com/mikeroyal/PipeWire-Guide#table-of-contents)

Distributed under the [Creative Commons Attribution 4.0 International (CC BY 4.0) Public License](https://creativecommons.org/licenses/by/4.0/).
