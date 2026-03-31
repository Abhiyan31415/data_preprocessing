Project: Neplish ASR Data Preprocessing Pipeline
What is this project?
This is a data preprocessing pipeline for a Nepali-English code-switched (Neplish) Automatic Speech Recognition (ASR) project. The goal is to prepare raw audio recordings and their transcripts for training a speech recognition model (likely Whisper-based) that can handle code-switching between Nepali and English languages.
What does it do?
The project takes raw audio files (AAC format) and their corresponding transcript files (TXT with timestamps), and processes them into a clean, augmented HuggingFace dataset ready for ASR model training.
Pipeline Steps:
1. Parse Transcripts - Extract timestamped segments from transcript files (handles multiple formats)
2. Segment Audio - Split audio files into smaller clips based on timestamps, convert to 16kHz mono WAV
3. Clean Transcripts - Resolve bracket annotations like [English/Nepali], remove [NOISE], [<unk>], etc.
4. Create HuggingFace Dataset - Build a dataset with train/validation/test splits (80/10/10)
5. Data Augmentation - Apply audio augmentations to increase training data:
   - Gaussian (white) noise
   - Pink (1/f) noise
   - Tempo change (time stretching)
   - Pitch shifting
   - Volume perturbation
6. Save Statistics - Generate JSON/Markdown reports with dataset statistics for presentation
Input Data
- 3 audio files: aashraya.aac, mukesh.aac, praja.aac
- 3 transcript files: With timestamps and Nepali-English mixed text
- Multiple speakers: Including sub-speakers in some recordings
Output
- Segmented WAV audio files (16kHz mono)
- Cleaned transcripts CSV
- HuggingFace DatasetDict (train/val/test splits)
- Augmented dataset (2x training data)
- Statistics JSON and Markdown reports
- Visualizations showing augmentation effects
Key Features
- Handles code-switched text (Nepali + English)
- Tracks code-switching statistics (% of samples with English words, top English words used)
- Demonstrates each augmentation with waveforms, spectrograms, and playable audio
- Follows patterns from existing minor-testing codebase
Files
- data_preprocessing.ipynb - Main preprocessing pipeline + augmentation demos
- visualization.ipynb - Charts and visualizations for presentation
- raw_dataset/ - Input audio and transcript files
- data/ - Output directory for processed data