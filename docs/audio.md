# HushLine Audio

## Components

### Callibrator

Measures silence and voice samples to establish initial audio characteristics and configure the Noise Tracker.

Returns True if calibration succeeded, False if something went wrong (e.g. user didn't speak).

future behavior: We'll also make it such that eventually the callibration data is just recorded and isn't needed unless the state of voice samples changes drastically.

### Mic Stream

Captures Audio and converts it to HushLine's own Audio frames.

#### Audio input to Audio frame output

-- microphone input -> RtAudio -> Ring Buffer (stores the latest samples)-> Audio frame (512 samples)

### VAD

Uses Silero VAD to classify which audio frames pass as speech and which do not

### Noise Tracker

Calculates the Background Noise Floor to compare with the loudness of speech. This will help prevent false positives if the background is highly Noisy.

## Tools 

### Audio Backend

### RtAudio

HushLine will use RtAudio for cross-platform real-time microphone Input.

RtAudio provides a common C++ interface over platform-specific audio APIs and supports the major OSs.

github link: [https://github.com/thestk/rtaudio]

### Silero VAD

We will use Silero VAD, as it is a light weight model that is pretty accurate for speech recognition even under heavy noise environment.

github link: [https://github.com/snakers4/silero-vad]

### Audio Format

example: [https://github.com/snakers4/silero-vad/blob/master/examples/cpp/silero-vad-onnx.cpp]

- Sample rate: 16KHZ
- Channels: Mono
- Sample format: float32 <RTAUDIO_FLOAT32>
- Frame duration: 32ms 

-- 16,000 samples/sec × 0.032 sec
= 512 samples --- 1 audio frame

###