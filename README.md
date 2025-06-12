# HealthQR

## Digital Health Passport (MDR-4)
A HIPAA-compliant, LLM-powered health summary QR generator for clinics and patients.




## Tech Stack

| Layer     | Technology                                                  |
|-----------|-------------------------------------------------------------|
| Frontend  | React Native (Expo), Redux Toolkit                          |
| Backend   | Node.js, Express, Firebase Auth                             |
| Database  | Firestore (EHR cache), SQLite (Offline)                     |
| AI        | Llama 2 (Fine-tuned), Python FastAPI                        |
| Security  | JWT, AES-256, HIPAA-compliant masking                       |
| QR Encoding | Base45 + Protocol Buffers                                 |










## Project Structure

```bash
mdr-4/  
├── 📁 app/                      # React Native (Expo) Frontend  
│   ├── 📁 assets/               # Static files (fonts, images)  
│   ├── 📁 components/           # Reusable UI components  
│   │   ├── QRGenerator.js       # QR generation logic  
│   │   ├── Scanner.js           # Clinic-side QR scanner  
│   │   └── EmergencyView.js     # Paramedic read-only view  
│   ├── 📁 navigation/           # Role-based routing  
│   ├── 📁 screens/              # App screens  
│   │   ├── Patient/             # Patient flows  
│   │   │   ├── HomeScreen.js    # Dashboard  
│   │   │   └── EditSummary.js   # LLM output review  
│   │   └── Clinic/              # Clinic flows  
│   ├── 📁 store/                # Redux state (auth, EHR data)  
│   └── App.js                   # Entry point  

├── 📁 backend/                  # Node.js API  
│   ├── 📁 controllers/          # Business logic  
│   │   ├── qrController.js      # QR generation/validation  
│   │   └── fhirController.js    # EHR data fetcher  
│   ├── 📁 middlewares/          # Auth/HIPAA checks  
│   ├── 📁 routes/               # API endpoints  
│   ├── 📁 utils/                # Helpers (AES, Base45)  
│   └── server.js                # Express server  

├── 📁 ai/                       # LLM and data processing  
│   ├── 📁 data/                 # Synthetic training data  
│   ├── model_training.py        # Fine-tuning script  
│   └── api.py                   # FastAPI endpoint for LLM  

├── 📁 docs/                     # Compliance and manuals  
│   ├── HIPAA_CHECKLIST.md       # Privacy requirements  
│   └── FHIR_INTEGRATION.md      # EHR API specs  

├── 📁 scripts/                  # Dev/deployment scripts  
│   ├── deploy_firebase.sh       # Cloud functions  
│   └── protobuf_compile.sh      # QR payload compiler  

├── .env.example                 # Environment variables  
├── .gitignore                   
├── LICENSE.md                   # Apache 2.0  
└── README.md                    # This file  
```


## Setup

### Prerequisites
Node.js v18+, Python 3.10+, Firebase CLI


### Installation

1. Clone the repo:
```bash
git clone https://github.com/your-repo/mdr-4.git  
cd mdr-4  
```

2. Set up frontend:
```bash
cd app  
npm install  
cp .env.example .env  # Add Expo/Firebase keys  
```

3. Run backend:
```bash
cd ../backend  
npm install  
node server.js  
```

4. AI service (optional):
```bash
cd ../ai  
pip install -r requirements.txt  
uvicorn api:app --reload  
```





