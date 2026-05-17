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