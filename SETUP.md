# Setup Instructions

## Prerequisites
- Python 3.10+
- Google account for Google Drive and Google Colab
- Conda or other virtual environment manager recommended
- Recommended to run notebooks through Google Colab extension in VS Code
- GPU recommended (Google Colab T4 was sufficient for this project)

## Environment Setup
1. Open and sign in to Google Colab (https://colab.research.google.com)
2. Mount Google Drive. Open a new notebook and in a new cell, run
```python
from google.colab import drive
drive.mount('/content/drive')

import os
os.chdir('/content/drive/MyDrive/NEW_FOLDER_NAME')
```
You may be required to grant Colab permissions.

3. Clone repository. From the terminal, run
```bash
git clone https://github.com/victoriaf55/cs372-final.git
```
4. Install dependencies. From the terminal, run
```bash
pip install -r cs372-final/requirements.txt
```

## Running the Project
### Training
```bash
python train.py
```

Checkpoints are saved every 50 updates to /content/drive/MyDrive/NEW_FOLDER_NAME/checkpoints/

Training logs for TensorBoard are saved to /content/drive/MyDrive/NEW_FOLDER_NAME/logs/

### Monitoring Training
Launch TensorBoard in Colab:
```python
%load_ext tensorboard
%tensorboard --logdir /content/drive/MyDrive/NEW_FOLDER_NAME/logs
```

### Evaluation
Evaluate the latest checkpoint:
```bash
python evaluate.py
```

Evaluate a specific checkpoint:
```bash
python evaluate.py --checkpoint /path/to/checkpoint.pt
```

Evaluate and record video:
```bash
python evaluate.py --record
```

Compare all checkpoints:
```bash
python evaluate.py --compare
```

### Viewing Results
Videos are saved to /content/drive/MyDrive/NEW_FOLDER_NAME/videos/

## No External APIs Required
This project uses only open-source tools and the MuJoCo physics engine
via the Gymnasium interface. No API keys or external services are needed.