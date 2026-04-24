🧠 CycleGAN for Unpaired Image-to-Image Translation
Generative AI Assignment 03 – Question 3
📌 Project Overview

This project implements a CycleGAN (Cycle-Consistent Generative Adversarial Network) to perform unpaired image-to-image translation between two domains:

✏️ Sketch → Photo
📷 Photo → Sketch

Unlike traditional supervised models, CycleGAN learns mappings without paired datasets, ensuring structural consistency using cycle consistency loss.

🎯 Objectives
Learn domain translation without paired data
Preserve structural information across transformations
Generate realistic outputs using adversarial learning
Ensure reversibility using cycle consistency
🗂️ Dataset

We used the following datasets as required:

TU-Berlin Sketch Dataset (Sketch Domain)
Sketchy Dataset (Sketch + Photo)
Google QuickDraw Dataset (Optional for augmentation)

📌 All datasets were:

Resized to 128 × 128
Normalized to [-1, 1]
Loaded using separate DataLoaders for each domain
🏗️ Model Architecture
🔁 Generators (ResNet-Based)
Generator	Task
G_AB	Sketch → Photo
G_BA	Photo → Sketch
Architecture: ResNet Generator
ResNet Blocks: 6 blocks (optimized for Kaggle GPU)
Activation: ReLU / Tanh
Goal: Learn bidirectional mappings
🕵️ Discriminators (PatchGAN)
Discriminator	Domain
D_A	Sketch
D_B	Photo
Uses PatchGAN
Classifies image patches instead of full image
Improves texture-level realism
⚙️ Training Details
🔧 Hyperparameters
Parameter	Value
Optimizer	Adam
Learning Rate	0.0002
Betas	(0.5, 0.999)
Batch Size	4–8
Image Size	128 × 128
📉 Loss Functions
Adversarial Loss
Ensures generated images look realistic
Cycle Consistency Loss
Enforces:
Sketch → Photo → Sketch ≈ Original Sketch
Photo → Sketch → Photo ≈ Original Photo
Identity Loss
Preserves color/composition when input already belongs to target domain
🔄 Training Pipeline
Load unpaired datasets (Sketch & Photo)
Forward Pass:
Sketch → Photo → Reconstructed Sketch
Photo → Sketch → Reconstructed Photo
Compute:
Adversarial Loss
Cycle Loss
Identity Loss
Update:
Generators
Discriminators
Save checkpoints every few epochs
⚡ Optimization Techniques

To efficiently train on Kaggle T4 ×2 GPUs:

✅ Mixed Precision Training (torch.cuda.amp)
✅ Reduced ResNet blocks (6 instead of 9)
✅ Small batch size (4–8)
✅ Dataset subset usage
✅ Frequent checkpointing
📊 Results & Visualization

The model generates:

✔️ Sketch → Realistic Photo
✔️ Photo → Clean Sketch
✔️ Reconstructed Images (Cycle Output)
🔍 Visualization Includes:
Input Image
Translated Output
Reconstructed Image
📈 Evaluation Metrics
SSIM (Structural Similarity Index)
PSNR (Peak Signal-to-Noise Ratio)
Visual comparison (qualitative analysis)
🚀 Application (Deployment)

A simple Gradio / Streamlit app is built to:

Upload image (Sketch or Photo)
Perform domain translation
Display real-time results
📁 Project Structure
CycleGAN/
│── data/
│── models/
│   ├── generator.py
│   ├── discriminator.py
│── training/
│   ├── train.py
│   ├── losses.py
│── utils/
│   ├── dataloader.py
│   ├── visualization.py
│── app/
│   ├── streamlit_app.py
│── checkpoints/
│── results/
│── README.md
🧪 How to Run
# Clone repository
git clone <repo-link>

# Install dependencies
pip install -r requirements.txt

# Train model
python train.py

# Run app
streamlit run app/streamlit_app.py
📌 Key Learnings
CycleGAN removes dependency on paired datasets
Cycle consistency is crucial for stable training
PatchGAN improves texture-level realism
Training GANs requires careful balancing
⚠️ Challenges Faced
Mode instability during early training
High GPU memory usage
Maintaining balance between generators and discriminators
👥 Contributors
Bushra Abad
[Partner Name]
📎 Submission Links
🔗 GitHub Repo: [Add link]
✍️ Medium Blog: [Add link]
💼 LinkedIn Post: [Add link]
📚 References
CycleGAN Paper (Zhu et al., 2017)
PyTorch Documentation
Kaggle Datasets
