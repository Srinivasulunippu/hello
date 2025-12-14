
## 1. Dataset Pipeline

flowchart LR
A[Raw Audio & Text Sources\n(Audiobooks, Scripts, Web Text)] --> B[Data Cleaning\n(remove noise, clipping, bad segments)]


This diagram conceptually links dataset design choices (left) to the latent representation learned by a TTS model and finally to perceived voice qualities (right). 


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
