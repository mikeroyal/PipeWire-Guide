<h1 align="center">
 <img src="https://user-images.githubusercontent.com/45159366/142936394-b546784e-231a-4391-9dd8-c686e5a7eee9.png">
  <br />
  PipeWire Guide
</h1>

<p align="center">
<img src="https://user-images.githubusercontent.com/45159366/144766375-c90533df-e0d6-4893-9131-465fe54e236d.png">
<br />
</p>


#### A guide covering PipeWire including the applications and tools that will make you a better and more efficient with your PipeWire.

**Note: You can easily convert this markdown file to a PDF in [VSCode](https://code.visualstudio.com/) using this handy extension [Markdown PDF](https://marketplace.visualstudio.com/items?itemName=yzane.markdown-pdf).**

# Table of Contents

1. [Getting Started with PipeWire](https://github.com/mikeroyal/PipeWire-Guide#getting-started-with-pipewire)

   - [PipeWire Tools](https://github.com/mikeroyal/PipeWire-Guide#pipewire-tools)
   - [Setting up PipeWire for Ubuntu/Debian](https://github.com/mikeroyal/PipeWire-Guide#setting-up-pipewire-for-ubuntudebian)

2. [Wayland Development](https://github.com/mikeroyal/PipeWire-Guide#wayland-development)

# Getting Started with PipeWire

[How Audio is implemented with PipeWire](https://docs.pipewire.org/page_audio.html)

[PipeWire Design](https://docs.pipewire.org/page_pipewire.html)

[PipeWire Library](https://docs.pipewire.org/page_library.html)

[DMA-BUF sharing](https://docs.pipewire.org/page_dma_buf.html)

[PipeWire Daemon](https://docs.pipewire.org/page_daemon.html)

[PipeWire Tools](https://docs.pipewire.org/page_tools.html)

[PipeWire Session Manager](https://docs.pipewire.org/page_session_manager.html)

[PipeWire Modules](https://docs.pipewire.org/page_pipewire_modules.html)

[PipeWire API](https://docs.pipewire.org/page_api.html)

   - [Client Implementation](https://docs.pipewire.org/page_client_impl.html)
   - [Proxy](https://docs.pipewire.org/page_proxy.html)
   - [Streams](https://docs.pipewire.org/page_streams.html)
   - [Thread Loop](https://docs.pipewire.org/page_thread_loop.html)
 
[PipeWire - ArchWiki](https://wiki.archlinux.org/title/PipeWire#JACK_clients)

[WirePlumber Documentation](https://pipewire.pages.freedesktop.org/wireplumber/)

<p align="center">
 <img src="https://user-images.githubusercontent.com/45159366/142779615-d631251b-a2d6-48b4-8194-7985604a8563.png">
  <br />
</p>

How WirePlumber, the PipeWire session manager works. Source: [Collabora](https://www.collabora.com/news-and-blog/blog/2020/05/07/wireplumber-the-pipewire-session-manager/)

## PipeWire Tools

[PipeWire](https://pipewire.org) is a server and user space API to deal with multimedia pipelines.It provides a low-latency, graph based processing engine on top of audio and video devices that can be used to support the use cases currently handled by both pulseaudio and JACK. PipeWire was designed with a powerful security model that makes interacting with audio and video devices from containerized applications easy. Nodes in the graph can be implemented as separate processes, communicating with sockets and exchanging multimedia content using fd passing. PipeWire was created by [Wim Taymans](https://gitlab.freedesktop.org/wtaymans), Principal Engineer at Red Hat and co-creator of the GStreamer multimedia framework.
 
 **Key features of PipeWire include:**
 
   - Capture and playback of audio and video with minimal latency.
   - Real-time Multimedia processing on audio and video.
   - Multiprocess architecture to let applications share multimedia content.
   - Seamless support for PulseAudio, JACK, ALSA and GStreamer applications.


[WirePlumber](https://pipewire.pages.freedesktop.org/wireplumber/) is a modular session / policy manager for [PipeWire](https://pipewire.org/) and a GObject-based high-level library that wraps PipeWire’s API, providing convenience for writing the daemon’s modules as well as external tools for managing PipeWire. The WirePlumber daemon implements the session & policy management service. It follows a modular design, having plugins that implement the actual management functionality.

[Core API](https://docs.pipewire.org/group__api__pw__core.html) is used by all clients that need to communicate with the [PipeWire Daemon](https://docs.pipewire.org/page_daemon.html) and provides the necessary structs to interface with the daemon.

[Implementation API](https://docs.pipewire.org/group__api__pw__impl.html) is primarily used by the [PipeWire Daemon](https://docs.pipewire.org/page_daemon.html) itself but also by the [PipeWire Session Manager](https://docs.pipewire.org/page_session_manager.html) and modules/extensions that need to build objects in the graph.

[SPA (Simple Plugin API)](https://docs.pipewire.org/group__api__spa.html) is an extensible API to implement all kinds of plugins.

### Audio Tools & Libraries to use with PipeWire

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

[NoiseTorch](https://github.com/lawl/NoiseTorch) is an easy to use open source application for Linux with PulseAudio or PipeWire. It creates a virtual microphone that suppresses noise, in any application. 

<p align="center">
<img src="https://user-images.githubusercontent.com/45159366/167501959-0ca879bb-8c37-4979-94e7-c253bb50fde7.png">
<br />
</p>

[QjackCtl](https://qjackctl.sourceforge.io/) is a simple Qt application to control the JACK sound server daemon, specific for the Linux Audio Desktop infrastructure.

[Catia](https://kx.studio/Applications:Catia) is a JACK Patchbay, with some neat features like A2J bridge support and JACK Transport. It's supposed to be as simple as possible so it can work nicely on non-Linux platforms. 

[JACK Audio Connection Kit AKA JACK](https://jackaudio.org/) is a professional sound server daemon that provides real-time, low-latency connections for both audio and MIDI data between applications that implement its API. JACK can be configured to send audio data over a network to a main machine, which then outputs the audio to a physical device. This can be useful to mix audio from a number of linked computers without requiring additional cables or hardware mixers, and keeping the audio path digital for as long as possible.

[JACK2](https://github.com/jackaudio/jack2) is a C++ version of the JACK low-latency audio server for multi-processor machines. It is a new implementation of the JACK server core features that aims at removing some limitations of the JACK1 design. The activation system has been changed for a data flow model and lock-free programming techniques for graph access have been used to have a more dynamic and robust system.

[OpenMAX™](https://www.khronos.org/openmax/) is a cross-platform API that provides comprehensive streaming media codec and application portability by enabling accelerated multimedia components to be developed, integrated and programmed across multiple operating systems and silicon platforms.

[H.264(AVC)](https://en.wikipedia.org/wiki/H.264/MPEG-4_AVC) is a video compression standard based on block-oriented and motion-compensated integer-DCT coding that defines multiple profiles (tools) and levels (max bitrates and resolutions) with support up to 8K.

[H.265(HEVC)](https://en.wikipedia.org/wiki/High_Efficiency_Video_Coding) is a video compression standard that is the successor to H.264(AVC). It offers a 25% to 50% better data compression at the same level of video quality, or improved video quality at the same bit-rate.

[FFmpeg](https://ffmpeg.org) is a leading multimedia framework that can decode, encode, transcode, mux, demux, stream, filter and play pretty much anything that humans and machines have created. It supports the most obscure ancient formats up to the cutting edge ones on multiple platforms such as Windows, macOS, and Linux.

[GStreamer](https://gstreamer.freedesktop.org/) is a library for constructing graphs of media-handling components. The applications it supports range from simple Ogg/Vorbis playback, audio/video streaming to complex audio (mixing) and video (non-linear editing) processing. Applications can take advantage of advances in codec and filter technology transparently.

[Media Source Extensions (MSE)](https://www.w3.org/TR/media-source/) is a [W3C specification](https://github.com/w3c/media-source) that allows JavaScript to send byte streams to media codecs within Web browsers that support HTML5 video and audio. Also, this allows the implementation of client-side prefetching and buffering code for streaming media entirely in JavaScript.

[WebRTC](https://webrtc.org/) is an open-source project that adds real-time communication capabilities to your application that works on top of an open standard. It supports video, voice, and generic data to be sent between peers, allowing developers to build powerful voice- and video-communication solutions.

## Setting up PipeWire for Ubuntu/Debian

**Note:** For those using Pop!_OS 22.04 or later PipeWire is already setup by default.

**Add PipeWire PPA**

```$ sudo add-apt-repository ppa:pipewire-debian/pipewire-upstream```

**Install the pipewire-audio-client-libraries and additional libraries to use Bluetooth, GStreamer, or JACK devices with your Ubuntu/Debian system.**
 
 ```$ sudo apt update```
  ```  $ sudo apt install pipewire pipewire-audio-client-libraries gstreamer1.0-pipewire libpipewire-0.3-{0,dev,modules} libspa-0.2-{bluetooth,dev,jack,modules} pipewire{,-{audio-client-libraries,pulse,media-session,bin,locales,tests}}```

**After installation has completed, run the following command to reload the daemon in systemd.**

```$ systemctl --user daemon-reload```

**Disable PulseAudio in Ubuntu. It will no longer be needed, since we are using PipeWire.**

```$ systemctl --user --now disable pulseaudio.service pulseaudio.socket```

**PulseAudio is disabled, we can start PipeWire and enable it to run automatically upon system boot.**

```$ systemctl --user --now enable pipewire pipewire-pulse```

**Run the following command to ensure that PipeWire is running.**

```$ pactl info```

### Reverting Changes

```$ sudo apt remove pipewire pipewire-audio-client-libraries gstreamer1.0-pipewire libpipewire-0.3-{0,dev,modules} libspa-0.2-{bluetooth,dev,jack,modules} pipewire{,-{audio-client-libraries,pulse,media-session,bin,locales,tests}}```

**Reload the daemon in systemd.**

```$ systemctl --user daemon-reload```

**Re-enables the PulseAudio service after you do a system reboot.**

```$ systemctl --user --now enable pulseaudio.service pulseaudio.socket```

**Ensure that PulseAudio has been completely restored.**
 
```$ pactl info```


# Wayland Development
[Back to the Top](https://github.com/mikeroyal/PipeWire-Guide#table-of-contents)

<p align="center">
 <img src="https://user-images.githubusercontent.com/45159366/104235197-79cf4e00-5409-11eb-97a6-a12f7bd8ad2a.png">
  <br />
</p>

## Wayland Learning Resources

[Wayland](https://wayland.freedesktop.org) is a protocol for a compositor to talk to its clients as well as a C library implementation of that protocol. The compositor can be a standalone display server running on Linux kernel modesetting and evdev input devices, an [X application](https://www.x.org/wiki/XServer/), or a wayland client itself.

[Wayland Architecture](https://wayland.freedesktop.org/architecture.html)

[Wayland Documentation](https://wayland.freedesktop.org/docs/html/)

[Sotfware Toolkits that have Wayland support right now](https://wayland.freedesktop.org/toolkits.html)

[Contribution instructions for Wayland](https://gitlab.freedesktop.org/wayland/wayland/blob/master/CONTRIBUTING.md)

[Contribution instructions for Weston](https://gitlab.freedesktop.org/wayland/weston/blob/master/CONTRIBUTING.md)

[Reporting Wayland bugs](https://gitlab.freedesktop.org/wayland/wayland/issues)

[Reporting Weston bugs](https://gitlab.freedesktop.org/wayland/weston/issues)

[WSLG: X11 and Wayland Applications in Windows Subsystem for Linux(WSL2)](https://linuxplumbersconf.org/event/9/contributions/611/attachments/702/1298/XDC2020_-_X11_and_Wayland_applications_in_WSL.pdf)

[Qt Wayland Compositor](https://doc.qt.io/qt-5/qtwaylandcompositor-index.html)

[Qt Wayland Compositor Examples](https://doc.qt.io/qt-5/qtwaylandcompositor-examples.html)

[Wayland on ArchWiki](https://wiki.archlinux.org/index.php/Wayland)

[Sway on ArchWiki](https://wiki.archlinux.org/index.php/Sway)

[Wayland on Ubuntu Wiki](https://wiki.ubuntu.com/Wayland)

[Wayland on Debian Wiki](https://wiki.debian.org/Wayland)

[The Wayland Display Server on Fedora Docs](https://docs.fedoraproject.org/en-US/fedora/rawhide/system-administrators-guide/Wayland/)

[Wayland features on Fedora Project Wiki](https://fedoraproject.org/wiki/Wayland_features)

[Wayland on GNOME Wiki](https://wiki.gnome.org/Initiatives/Wayland)

[KWin/Wayland on KDE Community Wiki](https://community.kde.org/index.php?title=KWin/Wayland)

[Wayland Desktop Landscape on Gentoo Wiki](https://wiki.gentoo.org/wiki/Wayland_Desktop_Landscape)

[Wayland in Void Linux Handbook](https://docs.voidlinux.org/config/graphical-session/wayland.html)

[Wayland on Enlightenment DE](https://www.enlightenment.org/about-wayland)

## Wayland Tools

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
