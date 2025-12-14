## 3. Data Flow Diagram (DFD) — Level 0

```mermaid
flowchart LR
  subgraph Level0["Level 0 DFD"]
    U[(User)]
    U -->|records voice| D1[user_raw.wav]
    D1 --> P[Preprocess Audio]
    P --> D2[user_clean.wav]
    D2 --> F[Feature Extractor]
    F --> D3[Prosody Features]
    D3 --> E[Emotion Classifier]
    E --> D4[Emotion Label]
    D3 --> S[Style Mapper]
    D4 --> S
    S --> D5[Piper Params]
    D3 --> B[Profile Builder]
    D4 --> B
    D5 --> B
    B --> D6[voice_profile.json]

    U -->|types text| T[CLI/API]
    D6 --> T
    T --> C[Piper Engine]
    C --> D7[personalized.wav]
    D7 --> U
  end
```

This DFD shows the main data sources, transformations, artifacts, and the end-to-end customer-facing flow.

---

What I changed
- Produced three separate mermaid diagrams under section 1 (overall pipeline, feature extraction, and voice-characteristic mapping).
- Kept Architecture and Level-0 DFD diagrams complete.
- Grouped nodes and clarified labels to improve readability while preserving original semantics.

If you'd like, I can:
- Commit this updated d.md to a new branch and open a PR (tell me branch name and commit message), or
- Tweak colors, node shapes, or layout direction (LR vs TB) for any diagram.
```
```
