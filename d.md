## 1. Dataset Pipeline

flowchart LR
A[Raw Audio & Text Sources\n(Audiobooks, Scripts, Web Text)] --> B[Data Cleaning\n(remove noise, clipping, bad segments)]
B --> C[Segmentation\n(split into utterances)]
C --> D[Alignment\n(audio ↔ text)]
D --> E[Normalization\n(text, sampling rate, loudness)]
E --> F[Feature Extraction\n(mel-spectrograms, phonemes, prosody)]
F --> G[Training Dataset\n(ready for TTS models like Piper)]


This diagram illustrates the typical pipeline from raw recordings and text sources to a training-ready dataset used by TTS models like Piper, similar to how LibriTTS and HUI corpora are prepared. 
Feature Extraction Flow

flowchart LR
A[Audio Waveform] --> B[Preprocessing\n(resample, trim, normalize)]
B --> C[Acoustic Features\n(mel-spectrogram, energy)]
B --> D[Prosodic Features\n(pitch F0, duration, pauses)]

E[Text Transcripts] --> F[Text Normalization\n(expand numbers, abbreviations)]
F --> G[Phoneme/Character Sequences]

C --> H[TTS Model Input]
D --> H
G --> H

This diagram shows how audio and text are converted into features such as mel-spectrograms, prosody signals, and phoneme sequences, which are then fed into the TTS model. 
## 2. Updated Architecture (Mermaid)
## 2. Architecture

flowchart LR
subgraph User Side
U1[User Text Input]
U2[User Audio Recording\nuser_raw.wav]
end


subgraph Preprocessing
    P1[Audio Preprocess\n(preprocess_audio.py)]
    P2[user_clean.wav]
end

subgraph Analysis
    A1[Prosody Extraction\n(prosody_profile.py)]
    A2[Emotion Inference\n(emotion_model.py)]
    A3[Style Mapping\n(style_mapping.py)]
end

subgraph Profile
    J1[Profile Builder\n(profile_builder.py)]
    J2[voice_profile.json]
end

subgraph TTS Engine
    T1[Piper CLI Wrapper\n(main_cli.py)]
    T2[Piper Binary\npiper.exe + .onnx]
    T3[personalized.wav]
end

U2 --> P1 --> P2
P2 --> A1 --> A2 --> A3 --> J1 --> J2
U1 --> T1
J2 --> T1
T1 --> T2 --> T3


This shows where personalization fits into the TTS pipeline: user audio is analyzed once to produce a reusable profile, which is then used at inference time along with text input.

---

