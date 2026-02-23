# 🎬 AI-DUBBING

> **Automatically dub videos into any language — preserving each speaker's voice using AI.**

[![Open Single Person Dubbing in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/KUNALDEBNATH/AI-DUBBING/blob/main/Single_Person_Dubbing.ipynb)
[![Open Multi Person Dubbing in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/KUNALDEBNATH/AI-DUBBING/blob/main/Multiple_Person_Dubbing.ipynb)

---

## 📌 Overview

AI-DUBBING is an end-to-end pipeline that takes any video, transcribes its speech, translates it to a target language, synthesizes natural-sounding dubbed audio (with per-speaker voice cloning), and merges it back into the original video — all inside Google Colab.

Two notebooks are provided depending on your use case:

| Notebook | Use Case |
|---|---|
| `Single_Person_Dubbing.ipynb` | One speaker — voice-cloned dubbing using XTTS v2 |
| `Multiple_Person_Dubbing.ipynb` | Multiple speakers — diarization + pitch-adjusted per-speaker TTS |

---

## 🧠 How It Works

### 🎙️ Single Person Dubbing

```
Input Video
    │
    ▼
Extract Audio (MoviePy)
    │
    ▼
Transcribe Speech (Google Speech Recognition)
    │
    ▼
Translate Text (Deep Translator → target language)
    │
    ▼
Clone Voice & Synthesize Speech (XTTS v2 — multilingual)
    │
    ▼
Merge Dubbed Audio back into Video (MoviePy)
    │
    ▼
Output Dubbed Video 🎬
```

### 👥 Multiple Person Dubbing

```
Input Video
    │
    ▼
Extract Audio (MoviePy)
    │
    ▼
Speaker Diarization (pyannote.audio → RTTM file)
    │
    ▼
Segment & Transcribe per Speaker (OpenAI Whisper)
    │
    ▼
[Optional] Review & Edit Utterances per Speaker
    │
    ▼
Text-to-Speech per Speaker (gTTS + Pitch Shifting)
    │
    ▼
Combine All Speaker Audio with Timing
    │
    ▼
Output Combined Dubbed Audio 🔊
```

---

## ✨ Features

- 🌍 **Multi-language support** — Translate and dub into 15+ languages including Hindi, Bengali, Arabic, Spanish, French, Chinese, and more
- 🗣️ **Voice Cloning** (Single-person) — Uses XTTS v2 to preserve the original speaker's voice characteristics
- 👥 **Multi-Speaker Diarization** — Automatically separates speakers using pyannote.audio and generates pitch-differentiated voices per speaker
- ✏️ **Manual Utterance Editing** — Review, edit, or delete any transcribed utterance before synthesis (multi-person mode)
- 🎞️ **Full Video Merge** — Final dubbed audio is seamlessly merged back into the source video

---

## 🚀 Getting Started

### Prerequisites

- A Google Account (to run on Colab)
- A [Hugging Face](https://huggingface.co) account + API token (for multi-person diarization)

### Run on Google Colab

Just click the badge above for the notebook you need — no local setup required!

---

## 📂 Notebooks

### 1. `Single_Person_Dubbing.ipynb`

Best for: Vlogs, lectures, solo presentations, YouTube videos

**Key libraries:**
- `moviepy` — Video/audio splitting and merging
- `SpeechRecognition` — Speech-to-text transcription
- `deep_translator` — Language translation
- `TTS (XTTS v2)` — Multilingual voice-cloned speech synthesis

**Steps:**
1. Upload your video to Colab
2. Run all cells in order
3. Set your `target_language` in the translation cell
4. Download `output.mp4` — your dubbed video!

---

### 2. `Multiple_Person_Dubbing.ipynb`

Best for: Interviews, conversations, podcasts, panel discussions

**Key libraries:**
- `pyannote.audio` — Speaker diarization (who spoke when)
- `openai-whisper` — Accurate per-segment transcription
- `gTTS` — Text-to-speech synthesis
- `pydub` — Audio manipulation and pitch shifting

**Steps:**
1. Upload your video to Colab
2. Add your Hugging Face token in the diarization cell
3. Run cells — the pipeline diarizes, transcribes, and synthesizes each speaker
4. Optionally review and edit utterances per speaker
5. Get `combined_speech.wav` with all speakers dubbed

> **Supports up to 4 speakers** with unique pitch profiles to distinguish voices.

---

## 🌐 Supported Languages

| Language | Code |
|---|---|
| English | `en` |
| Hindi | `hi` |
| Bengali | `bn` |
| Spanish | `es` |
| French | `fr` |
| German | `de` |
| Italian | `it` |
| Portuguese | `pt` |
| Polish | `pl` |
| Turkish | `tr` |
| Russian | `ru` |
| Dutch | `nl` |
| Czech | `cs` |
| Arabic | `ar` |
| Chinese (Simplified) | `zh-cn` |

---

## 🛠️ Tech Stack

| Component | Technology |
|---|---|
| Video Processing | MoviePy |
| Speech Recognition | Google Speech Recognition, OpenAI Whisper |
| Speaker Diarization | pyannote.audio |
| Translation | Deep Translator (Google Translate API) |
| Voice Synthesis | XTTS v2 (Coqui TTS), gTTS |
| Audio Processing | pydub |
| Runtime | Google Colab (GPU recommended) |

---

## ⚠️ Notes

- For **XTTS v2** (voice cloning), a GPU runtime is strongly recommended in Colab (`Runtime > Change runtime type > GPU`)
- The **Hugging Face token** required for pyannote diarization can be obtained for free at [huggingface.co/settings/tokens](https://huggingface.co/settings/tokens) — make sure to accept the pyannote model terms
- Long videos may take several minutes to process depending on Colab GPU availability

---

## 👤 Author

**Kunal Debnath**
- GitHub: [@KUNALDEBNATH](https://github.com/KUNALDEBNATH)

