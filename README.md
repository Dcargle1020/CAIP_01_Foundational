# CAIP_01_Foundational
# 🗣️ Amazon Polly CI/CD Audio Pipeline  

This project automates **Text-to-Speech (TTS)** generation using **Amazon Polly**, uploads the audio to **S3**, and integrates with **GitHub Actions** for CI/CD automation.

---

## 🚀 Overview  

| Trigger | Output File | Purpose |
|----------|--------------|----------|
| Pull Request → main | `polly-audio/beta.mp3` | Beta test audio |
| Push → main | `polly-audio/prod.mp3` | Production audio |

**Flow:**  
`speech.txt` ➜ `synthesize.py` ➜ Amazon Polly ➜ `.mp3` ➜ S3 Bucket (`polly-audio/`)

---

## ⚙️ Setup  

1️⃣ **Create S3 Bucket**  
- Example: `my-polly-bucket`  
- Add folder prefix: `polly-audio/`

2️⃣ **Add GitHub Secrets**  
`AWS_ACCESS_KEY_ID`, `AWS_SECRET_ACCESS_KEY`, `AWS_REGION`, `S3_BUCKET_NAME`

IAM Policy must include:
```json
{
  "Action": ["polly:SynthesizeSpeech","s3:PutObject"],
  "Resource": "*",
  "Effect": "Allow"
}
