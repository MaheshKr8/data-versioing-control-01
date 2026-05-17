# 🍷 Wine Prediction Project  
## DVC + AWS S3 + Git Integration for Dataset Versioning

This project demonstrates how to use:

- 📦 DVC (Data Version Control)
- ☁️ AWS S3 as Remote Storage
- 🔧 Git for Tracking Dataset Metadata
- 🤖 Wine Prediction Dataset

---

# 📁 Project Architecture

```text
Wine Prediction Project
│
├── data/
│   ├── wine_dataset.csv
│   ├── .gitignore
│   └── wine_dataset.csv.dvc
│
├── .dvc/
│
├── .gitignore
├── README.md
└── requirements.txt
```

---

# 🚀 Step 1: Install DVC

Install DVC using pip:

```bash
python -m pip install dvc
```

Verify installation:

```bash
dvc --version
```

---

# ⚙️ Step 2: Initialize DVC

Initialize DVC inside the project:

```bash
dvc init
```

This creates:

```text
.dvc/
.dvcignore
```

---

# 📊 Step 3: Add Dataset to DVC

Track the dataset using DVC:

```bash
dvc add data/wine_dataset.csv
```

This creates:

```text
data/wine_dataset.csv.dvc
```

DVC will also update:

```text
data/.gitignore
```

---

# 📝 Step 4: Track DVC Metadata with Git

Add DVC tracking files to Git:

```bash
git add data/.gitignore data/wine_dataset.csv.dvc
```

Commit changes:

```bash
git commit -m "Track wine dataset using DVC"
```

---

# ☁️ Step 5: Configure AWS S3 as Remote Storage

## Create AWS Access Keys

Go to:

```text
AWS Console → Security Credentials → Access Keys
```

Generate:

- Access Key ID
- Secret Access Key

---

# 🔐 Configure AWS CLI

Run:

```bash
aws configure
```

Provide:

```text
AWS Access Key ID
AWS Secret Access Key
Region
Output format
```

---

# 📦 Install DVC S3 Support

```bash
python -m pip install dvc-s3
```

---

# ☁️ Add S3 Remote Storage

```bash
dvc remote add -d myremotedev s3://mlops-mahesh-dvc
```

Explanation:

| Command | Purpose |
|---|---|
| `remote add` | Adds remote storage |
| `-d` | Sets as default remote |
| `myremotedev` | Remote name |
| `s3://mlops-mahesh-dvc` | S3 bucket path |

---

# ⬆️ Push Dataset to S3

```bash
dvc push
```

This uploads dataset files to AWS S3.

---

# 🔄 Updating Dataset Versions

Whenever dataset changes:

## Step 1: Modify Dataset

```text
data/wine_dataset.csv
```

---

## Step 2: Re-track Dataset

```bash
dvc add data/wine_dataset.csv
```

---

## Step 3: Push Updated Dataset to S3

```bash
dvc push
```

---

# 📝 Track Updated Dataset Metadata in Git

```bash
git add data/wine_dataset.csv.dvc
```

OR

```bash
git add data/.gitignore data/wine_dataset.csv.dvc
```

OR

```bash
git add .
```

---

# 💾 Commit Changes

```bash
git commit -m "Track DVC dataset changes"
```

---

# 🌿 Push Project to GitHub

Rename branch:

```bash
git branch -M main
```

Add remote repository:

```bash
git remote add origin git@github.com:MaheshKr8/data-versioing-control-01.git
```

Push code:

```bash
git push -u origin main
```

---

# 🔍 Check Which DVC Remote Repository is Configured

Run:

```bash
cat .dvc/config
```

Example output:

```ini
[core]
    remote = myremotedev

['remote "myremotedev"']
    url = s3://mlops-mahesh-dvc
```

---

# 📌 Important Concept

## Git vs DVC

| Tool | Responsibility |
|---|---|
| Git | Tracks small metadata files and code |
| DVC | Tracks large datasets and ML models |
| AWS S3 | Stores actual dataset files |

---

# ✅ Source of Truth

```text
Git repository is the Source of Truth
```

Git tracks:

- Dataset pointers (`.dvc` files)
- Code
- Configuration

DVC tracks:

- Actual dataset versions

AWS S3 stores:

- Real dataset artifacts

---

# 🛠️ Useful DVC Commands

## Check DVC Status

```bash
dvc status
```

## Pull Dataset from Remote

```bash
dvc pull
```

## Remove Cached Files

```bash
dvc gc
```

## List DVC Remotes

```bash
dvc remote list
```

---

# 🎯 Benefits of DVC

- Dataset Versioning
- Reproducibility
- Large File Management
- Team Collaboration
- Cloud Storage Integration
- ML Experiment Tracking

---

# 📚 Technologies Used

- Python
- DVC
- AWS S3
- Git
- GitHub

---

# 👨‍💻 Author

Mahesh Kumar  
DevOps & MLOps Engineer

=====================
Wine Prediction
DVC + S3 + GIT

## Setup DVC for wine predication Dataset
python -m pip install dvc

dvc init

dvc add data/wine_dataset.csv

git add data/.gitignore data/wine_dataset.csv.dvc

## Use S3 as Remote cloud storage service
create access keys on right corner security credentials
 aws configure
 dvc remote add -d myremotedev s3://mlops-mahesh-dvc
 python -m pip install  dvc-s3
 dvc push

 To do any changes then run 

## and Git to track pointer to Dataset
Do some changes at data/wine_dataset.csv
dvc add data/wine_dataset.csv
dvc push

track pointer to Dataset
git add data/wine_dataset.csv.dvc
or
git add data/.gitignore data/wine_dataset.csv.dvc

git add .

git commit -m "track the dvc changes"

git branch -M main
git remote add origin git@github.com:MaheshKr8/data-versioing-control-01.git
git push -u origin main

# how to check which repository is used

cat .dvc/config

(mlopsEnv) Maheshs-MacBook-Air:Dvc-data-versioning maheshkumar$ cat .dvc/config
[core]
    remote = myremotedev
['remote "myremotedev"']
    url = s3://mlops-mahesh-dvc

Git repository is source of truth