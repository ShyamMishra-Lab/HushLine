# HushLine Architecture

## Overview

HushLine listens to microphone input, detects when the user is speaking, and controls currently playing media.
(inspired from sony's speak to chat feature.)
* working python prototype using both Webrtc VAD and Silero VAD [https://github.com/ShyamMishra-Lab/Hushline-Ambient_Audio_Assistant]

## Main Components

### Audio
Responsible for capturing microphone input. Audio processing and handling audio frames.

--Audio Stream : captures microphone frames.
--VAD : determines whether a frame contains speech.
--Noise Tracker : estimates the current environmental/background noise.

### Intelligence
Determines if the processed data is speech or not.
--Confidence Engine : estimating the certainty of speech or silence to relay play/pause signals.
--Hum rejection : functionality to avoid triggers from humming by users for songs and stuff.

### Media Controller
Controls media playback through the operating system APIs, different layers for different OS.

## Data Flow

Audio -> Intelligence -> Media Controller

## Supported Platforms

- Fedora/Linux
- Windows