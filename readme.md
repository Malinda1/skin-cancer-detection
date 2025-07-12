# Skin cancer detection model

detecting several type of lesion on skin 

| Short Code | Full Name | Type | Notes |
| --- | --- | --- | --- |
| AKIEC | Intraepithelial carcinoma / Bowen’s disease | Pre-cancer | May become cancerous |
| BCC | Basal Cell Carcinoma | Cancer | Common but treatable |
| BKL | Benign Keratosis-like Lesions | Benign | Sun/age-related |
| DF | Dermatofibroma | Benign | Small hard bump |
| MEL | Melanoma | Cancer | Dangerous if untreated |
| NV | Melanocytic Nevi | Benign | Normal moles |
| VASC | Vascular Lesions | Mostly benign | Blood vessel-related |
1. Detecting above skin lesions
2. then want to  display bellow status  



![Logo](images/ALL.jpeg)


## 🔴 1. **AKIEC**

**Actinic Keratoses and Intraepithelial Carcinoma (Bowen's Disease)**

➡️ **Type**: Pre-cancer or early-stage skin cancer



## ⚪ 2. **BCC**

**Basal Cell Carcinoma**

➡️ **Type**: Skin Cancer (Malignant)



## 🟤 3. **BKL**

**Benign Keratosis-like Lesions**

➡️ **Type**: **Benign (Non-cancerous)**


## 🟢 4. **DF**

**Dermatofibroma**

➡️ **Type**: Benign (Non-cancerous)



## ⚫ 5. **MEL**

**Melanoma**

➡️ **Type**: **Dangerous Skin Cancer** (Malignant)



## 🟠 6. **NV**

**Melanocytic Nevi (Moles)**

➡️ **Type**: Benign



## 🔵 7. **VASC**

**Vascular Lesions**

➡️ **Type**: Mostly benign


# Beginning the model development process

✅ Full Folder Structure for Skin Lesion Detection App

skin_lesion_app/
│
├── app/                        # FastAPI backend app
│   ├── [main.py](http://main.py/)                 # FastAPI entrypoint
│   ├── [api.py](http://api.py/)                  # Routes (e.g., /predict)
│   ├── model/                  # Model logic
│   │   ├── load_model.py       # Model loading logic
│   │   └── [predict.py](http://predict.py/)          # Prediction function
│   ├── utils/                  # Utilities like preprocessing
│   │   └── [preprocess.py](http://preprocess.py/)       # Image preprocessing
│   └── static/                 # Optional: sample images, docs
│       └── sample.jpg
│
├── model/                      # Stores trained model weights
│   └── skin_lesion_model.pt    # Trained PyTorch model
│
├── notebook/                   # Jupyter notebooks for EDA & training
│   └── train_model.ipynb       # Notebook to train & save model
│
├── utils/                      # Global utils if needed elsewhere
│   └── [helpers.py](http://helpers.py/)              # Misc helper functions
│
├── data/                       # Dataset storage
│   ├── raw/                    # Raw downloaded data
│   └── processed/              # Preprocessed/resized data
│
├── requirements.txt            # Python dependencies
├── Dockerfile                  # Docker container setup (optional)
├── [README.md](http://readme.md/)                   # Project description
└── .gitignore                  # Git ignore rules


## *model details*

✅ **`microsoft/beit-base-patch16-224-pt22k-ft22k`**

✅ Why It’s Suitable for Skin Lesion Classification

| Criteria | BEiT Verdict | Explanation |
| --- | --- | --- |
| 🔬 Medical Image Friendly | ✅✅✅ | Can capture fine textures, color variations in lesions. |
| 🖼️ Works with Color Images | ✅✅✅ | Processes RGB — important for lesions where color is diagnostic. |
| 🔧 Easy to Fine-Tune | ✅✅✅ | Available via Hugging Face + Transformers + Datasets. |
| 📈 Accuracy Potential | 🔥🔥🔥🔥 | Comparable or better than ViT if well fine-tuned. |

📌 Model Overview: `microsoft/beit-base-patch16-224-pt22k-ft22k`

| Attribute | Value |
| --- | --- |
| **Architecture** | Vision Transformer (Transformer Encoder only) |
| **Patch Size** | 16×16 |
| **Image Input Size** | 224×224 (RGB) |
| **Parameters** | ~86 million |
| **Pretrained On** | ImageNet-22k (14 million images, 21,000 classes) |
| **Fine-Tuned On** | ImageNet-22k again (classification refinement) |
| **Model Size on Disk** | ~340 MB |

🧠 Architecture Details

| Layer | Detail |
| --- | --- |
| **Hidden Size** | 768 |
| **Transformer Layers** | 12 |
| **Attention Heads** | 12 |
| **MLP Size** | 3072 |
| **Dropout** | 0.1 (standard) |
| **Positional Embedding** | Learned 2D |
| **Classifier Head** | Dense layer over `[CLS]` token |
