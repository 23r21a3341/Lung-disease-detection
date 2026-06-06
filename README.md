🫁 PneumoScan — Lung Disease Detection Using Deep Learning
Show Image
Show Image
Show Image
Show Image
Show Image

An AI-powered web application for automatic chest X-ray classification into COVID-19, Normal, Pneumonia, and Tuberculosis using VGG16 Transfer Learning and Grad-CAM explainability.


👤 Developer
Prasad
Roll No: 23R21A3341
B.Tech — Computer Science & Information Technology
MLR Institute of Technology (Autonomous), Hyderabad

📌 Table of Contents

About the Project
Key Features
Tech Stack
Project Structure
Getting Started
How to Run
Training the Model
API Endpoints
Results
Future Scope
License


📖 About the Project
Lung diseases such as COVID-19, Pneumonia, and Tuberculosis are among the most life-threatening respiratory conditions worldwide. Traditional diagnosis relies on manual chest X-ray interpretation by radiologists — which is slow, expensive, and error-prone.
PneumoScan solves this by using deep learning to automatically classify chest X-ray images into 4 categories with ~94% accuracy, while providing Grad-CAM heatmaps to visually explain the AI's decision — making it transparent and clinically trustworthy.

✨ Key Features

🧠 VGG16 Transfer Learning — Pretrained on ImageNet, fine-tuned on chest X-ray data
🔬 4-Class Classification — COVID-19, Normal, Pneumonia, Tuberculosis
🌡️ Grad-CAM Heatmaps — Visual explainability showing regions the model focused on
📊 Confidence Scores — Probability distribution across all 4 classes
🌐 Flask Web App — Drag-and-drop upload with real-time results
🏥 Clinical Recommendations — Auto-suggested action based on detected condition
📈 Model Evaluation — Confusion matrix, F1-score, AUC-ROC metrics
🔄 Data Augmentation — Rotation, flip, zoom, dropout to prevent overfitting


🛠️ Tech Stack
LayerTechnologyDeep LearningTensorFlow, Keras, VGG16ExplainabilityGrad-CAM (OpenCV)BackendFlask (Python)FrontendHTML, CSS, JavaScriptImage ProcessingPillow, NumPy, OpenCVEvaluationScikit-learn, Matplotlib, Seaborn

📁 Project Structure
PneumoScan/
├── app.py                    # Flask backend — main application
├── train.py                  # Model training script
├── evaluate.py               # Confusion matrix & metrics
├── download_dataset.py       # Kaggle dataset downloader
├── requirements.txt          # Python dependencies
├── README.md                 # Project documentation
│
├── templates/
│   └── index.html            # Frontend UI
│
├── static/
│   ├── css/                  # Stylesheets
│   └── js/                   # JavaScript files
│
├── model/
│   └── vgg16_lung_disease.h5 # Trained model (after training)
│
└── dataset/                  # Dataset folder (after download)
    ├── train/
    │   ├── COVID-19/
    │   ├── Normal/
    │   ├── Pneumonia/
    │   └── Tuberculosis/
    └── val/
        ├── COVID-19/
        ├── Normal/
        ├── Pneumonia/
        └── Tuberculosis/

⚡ Getting Started
Prerequisites

Python 3.10 or above
pip package manager
Git

1. Clone the Repository
bashgit clone https://github.com/your-username/PneumoScan.git
cd PneumoScan
2. Create Virtual Environment
bash# Windows
python -m venv venv
venv\Scripts\activate

# Mac / Linux
python3 -m venv venv
source venv/bin/activate
3. Install Dependencies
bashpip install -r requirements.txt

🚀 How to Run
bashpython app.py
Open your browser and go to:
http://localhost:5000
Upload any chest X-ray image (PNG/JPG) and click Analyze Scan to get instant results.

⚠️ Without a trained model, the app runs in demo mode (random predictions). Train the model first for real results.


🏋️ Training the Model
Step 1 — Download Dataset
bashpip install kaggle
# Place kaggle.json in ~/.kaggle/
python download_dataset.py
Or manually download from:
👉 COVID-19 Radiography Database — Kaggle
Step 2 — Train
bashpython train.py --data_dir ./dataset --epochs 20
Best model is automatically saved to model/vgg16_lung_disease.h5
Step 3 — Evaluate
bashpython evaluate.py --model model/vgg16_lung_disease.h5 --data_dir ./dataset
Outputs:

confusion_matrix.png
Per-class Precision, Recall, F1-Score
Macro AUC-ROC Score


🌐 API Endpoints
MethodEndpointDescriptionGET/Loads the PneumoScan web UIPOST/predictUpload X-ray → returns prediction JSONGET/model-infoReturns model architecture details
Sample API Response
json{
  "prediction": "COVID-19",
  "confidence": 87.4,
  "probabilities": {
    "COVID-19": 87.4,
    "Normal": 4.1,
    "Pneumonia": 5.6,
    "Tuberculosis": 2.9
  },
  "gradcam": "<base64_encoded_heatmap>",
  "demo_mode": false
}

📊 Results
ClassPrecisionRecallF1-ScoreCOVID-1994%92%93%Normal98%97%97%Pneumonia91%90%90%Tuberculosis94%93%93%
MetricScoreOverall Accuracy~94%AUC-ROC Score~0.96Avg F1-Score~93.3%Training Images21,000+

🔭 Future Scope

Expand detection to Lung Cancer, COPD, and Pleural Effusion
Integrate CT scan support alongside chest X-rays
Add patient history tracking with a database backend
Develop Android/iOS mobile application
Integrate DICOM format for hospital PACS systems
Apply federated learning for privacy-preserving training


⚠️ Disclaimer

This project is developed for academic and educational purposes only.
PneumoScan is not intended for clinical or medical use.
Always consult a qualified medical professional for diagnosis and treatment.


📄 License
This project is licensed under the MIT License.

🙏 Acknowledgements

Kaggle — COVID-19 Radiography Database
VGG16 — Karen Simonyan & Andrew Zisserman, 2014
Grad-CAM — Selvaraju et al., 2017
MLR Institute of Technology, Hyderabad


<p align="center">Made with ❤️ by Prasad | MLRIT | 23R21A3341</p>
