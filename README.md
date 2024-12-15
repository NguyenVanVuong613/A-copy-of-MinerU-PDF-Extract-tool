# Setup and Run MinerU on Windows

## 1. Install Magic PDF

### Create a virtual environment using Conda:
```bash
conda create -n MinerU python=3.10
conda activate MinerU
```

### Download Magic PDF:
```bash
pip install -U magic-pdf[full] --extra-index-url https://wheels.myhloli.com
```

---

## 2. Download Models from HuggingFace

### Install huggingface_hub:
```bash
pip install huggingface_hub
```

### Download models:
#### Linux:
```bash
wget https://github.com/opendatalab/MinerU/raw/master/scripts/download_models_hf.py -O download_models_hf.py
```

#### Windows:
```powershell
Invoke-WebRequest -Uri "https://github.com/opendatalab/MinerU/raw/master/scripts/download_models_hf.py" -OutFile "download_models_hf.py"
```

### Run the script to download the model files and configure file:
```bash
python download_models_hf.py
```

The configuration file can be found in the user directory, with the filename `magic-pdf.json`.
Example: `C:\Users\user_name\magic-pdf.json`

### Modify the configuration file:
Change the line:
```json
"device-mode": "cpu"
```
to:
```json
"device-mode": "cuda"
```
if running with a GPU.

---

## 3. Run Magic PDF
On the command line, execute the following command:
```bash
magic-pdf -p "pdf directory here" -o "output folder here" -m auto
