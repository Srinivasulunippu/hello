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

