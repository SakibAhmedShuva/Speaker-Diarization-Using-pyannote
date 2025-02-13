# Speaker Diarization Analysis using pyannote.audio

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/SakibAhmedShuva/Speaker-Diarization-Using-pyannote/blob/main/Speaker_Diarization_Analysis.ipynb)

A Jupyter Notebook implementation for analyzing audio files to identify different speakers and their speech segments using pyannote.audio's speaker diarization pipeline.

## Features

- Detect number of unique speakers in audio files
- Identify exact time segments for each speaker
- Visual representation of speaker turns
- Support for WAV audio files
- Easy integration with Hugging Face models

## Requirements

- Python 3.6+
- PyTorch
- Jupyter Notebook
- Hugging Face account (for access token)

## Installation

1. Clone the repository:
```bash
git clone https://github.com/SakibAhmedShuva/Speaker-Diarization-Using-pyannote.git
cd Speaker-Diarization-Using-pyannote
```

2. Install dependencies:
```bash
pip install pyannote.audio jupyterlab
```

3. Obtain Hugging Face access token:
   - Create account at huggingface.co
   - Accept terms for pyannote/speaker-diarization
   - Create access token in profile settings

## Usage

1. Place your audio files (.wav) in the `audio_samples` directory
2. Open `Speaker_Diarization_Analysis.ipynb` in Jupyter Notebook
3. Replace `use_auth_token="YOUR_HF_TOKEN"` with your Hugging Face token
4. Modify the audio file path in the notebook
5. Run all cells

### Example code snippet:

```python
from pyannote.audio import Pipeline
  
pipeline = Pipeline.from_pretrained(
    "pyannote/speaker-diarization",
    use_auth_token="YOUR_HF_TOKEN_HERE"
)

diarization = pipeline(r"audio_samples/your_audio.wav")

for turn, _, speaker in diarization.itertracks(yield_label=True):
    print(f"Speaker {speaker} spoke from {turn.start:.1f}s to {turn.end:.1f}s")
```

### Example Output
![image](https://github.com/user-attachments/assets/42d8e806-7d5d-4358-a891-96b4d4be74c1)


## Contributing

Contributions are welcome! Please open an issue or PR for:
- Additional file format support
- Visualization improvements
- Performance optimizations

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- pyannote.audio team
- Hugging Face for model hosting
