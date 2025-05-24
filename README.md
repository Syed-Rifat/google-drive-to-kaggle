
# 📘 Using Google Drive Datasets in Kaggle Notebooks

This guide explains how to import datasets from **Google Drive** into **Kaggle Notebooks** for machine learning, data analysis, or other workflows.

---

## ✅ Prerequisites

- A Google Drive account with your dataset uploaded
- A Kaggle account
- Dataset must be shared as **"Anyone with the link"**

---

## 🔗 Step 1: Get Google Drive Shareable Link

1. Right-click your dataset file in Google Drive → **Get link**
2. Change access to **"Anyone with the link"**
3. Copy the link.

Example:
```
https://drive.google.com/file/d/1aB2C3D4E5F6G7H8I9J/view?usp=sharing
```

Extract the **file ID**:
```
File ID = 1aB2C3D4E5F6G7H8I9J
```

---

## 🧪 Step 2: Create a Kaggle Notebook

1. Go to [Kaggle Notebooks](https://www.kaggle.com/code)
2. Click **"New Notebook"**
3. Enable the following in Settings:
   - ✅ Internet
   - (Optional) ✅ GPU or TPU

---

## 📥 Step 3: Install `gdown` and Download the File

```python
# Install gdown
!pip install -q gdown

# Google Drive file ID and desired output file name
file_id = '1aB2C3D4E5F6G7H8I9J'
output_name = 'dataset.zip'  # Or dataset.csv

# Download using gdown
!gdown https://drive.google.com/uc?id={file_id} -O {output_name}
```

---

## 🗜️ Step 4: Unzip the Dataset (If zipped)

```python
import zipfile
import os

if output_name.endswith('.zip'):
    with zipfile.ZipFile(output_name, 'r') as zip_ref:
        zip_ref.extractall('dataset')
    print("Unzipped successfully.")
else:
    print("No unzipping needed.")
```

---

## 📊 Step 5: Load the Dataset

```python
import pandas as pd

# Adjust this path as per your data structure
df = pd.read_csv('dataset/data.csv')
df.head()
```

---

## 💾 Optional: Upload Cleaned Dataset to Kaggle

1. Go to [Kaggle Datasets](https://www.kaggle.com/datasets)
2. Click **"New Dataset"**
3. Upload your file and set it to **Private**
4. Add it later using the **Add Data** tab in a Kaggle notebook

---

## 📂 Repository Structure

```
google-drive-to-kaggle/
├── README.md
├── GoogleDrive_to_Kaggle_Notebook.ipynb
```

---

## 📘 License

This project is licensed under the MIT License.
