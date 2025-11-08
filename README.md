# Parakeet ASR

Speech recognition using NVIDIA's Parakeet TDT model.

## Features

- 🎙️ Speech-to-text transcription using NVIDIA Parakeet TDT model (runs on `parakeet-tdt-0.6b-v3`)
- 📊 Timestamped transcription results
- 📝 Support for multiple audio formats (WAV, FLAC, MP3, M4A, etc.)
- 💾 Session History with export options (CSV, TXT, SRT)
- 🎯 Optimized for both short and long audio files
- 💻 GPU acceleration support (CUDA) with fallback to CPU

## Requirements

- **Python 3.11** (This is **critical**. Do not use Python 3.12+ as PyTorch/NeMo dependencies may fail.)
- **NVIDIA GPU with CUDA** (Strongly recommended). This guide assumes **CUDA 13.0**.
- **FFmpeg** (Must be installed on the system and added to the PATH).

## 🚀 Setup (Critical Steps)

Follow these steps exactly to avoid dependency errors.

### 1. Create a Virtual Environment (Recommended)

First, create and activate a new virtual environment using **Python 3.11**. This prevents package conflicts with your other projects.

```pwsh
# Create the environment
py -3.11 -m venv .venv
```

```pwsh
# Activate the environment
.\.venv\Scripts\activate
```

(If you choose not to do this, all packages will be installed globally, which can cause future conflicts.)

### 2. Manually Install PyTorch

You must install PyTorch and its components before installing the other requirements. This command installs the version built for CUDA 13.0.

```pwsh
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu130
```

### 3. Install App Requirements

Now that PyTorch is correctly installed, you can install the rest of the app's packages from the `requirements.txt` file.

```pwsh
pip install -r requirements.txt
```

### 4. Install Missing Dependencies

The `requirements.txt` file is kept minimal to avoid build errors. You must manually install `msgpack`, which `librosa` needs.

```pwsh
pip install msgpack
```

### 5. Install Optional Dependencies (Recommended)

To get the best performance and remove common warnings, install `cuda-python`.

```pwsh
pip install cuda-python>=12.3
```

## Usage

1. Run the application:
   ```pwsh
   streamlit run app.py
   ````

2. Upload an audio file (MP3, WAV, FLAC, etc.).
3. Wait for the model to process and transcribe.
4. View and export the transcription results.

## Notes

- NVIDIA GPU with CUDA support is strongly recommended for optimal performance.
- Long audio files (>8 minutes) will automatically use optimized settings.
- Maximum recommended audio duration is 30 minutes.

## Acknowledgements

This project is a fork of and based on the original:  [parakeet-asr-demo](https://github.com/SridharSampath/parakeet-asr-demo) by [Sridhar Sampath](https://github.com/SridharSampath).  
Special thanks to the original author for their work.