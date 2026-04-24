# Domain-Adaptation-and-Unpaired-Image-to--Image-Translation-using-CycleGAN
🎨 CycleGAN Implementation (Unpaired Image-to-Image Translation)
📌 Overview

This project implements a CycleGAN (Cycle-Consistent Generative Adversarial Network) for performing image-to-image translation without paired data. Unlike traditional supervised models, CycleGAN learns mappings between two domains using unpaired datasets.

Example tasks include:

Horse ↔ Zebra
Summer ↔ Winter
Monet Style ↔ Real Images
🚀 Features
✅ Unpaired image-to-image translation
✅ Two generators and two discriminators
✅ Cycle consistency loss
✅ Identity loss for color preservation
✅ Training visualization and results
🧠 Model Architecture

CycleGAN consists of:

🔹 Generators
G: X → Y
F: Y → X
🔹 Discriminators
Dx: Distinguishes real vs fake images in domain X
Dy: Distinguishes real vs fake images in domain Y
⚙️ Loss Functions
Adversarial Loss
Makes generated images realistic
Cycle Consistency Loss

Ensures:

X → Y → X ≈ X
Y → X → Y ≈ Y
Identity Loss
Preserves color and structure
🛠️ Technologies Used
Python 🐍
PyTorch 🔥
NumPy
Matplotlib
Jupyter Notebook
📂 Project Structure
AI_ASS03_CycleGAN.ipynb   # Main notebook
README.md                 # Project documentation
▶️ How to Run
1. Clone the repository
git clone <your-repo-link>
cd <repo-folder>
2. Install dependencies
pip install torch torchvision matplotlib numpy
3. Run the notebook
jupyter notebook

Open:

AI_ASS03_CycleGAN.ipynb
📊 Training Process
Load unpaired datasets (Domain X and Y)
Train generators and discriminators alternately
Optimize using:
Adversarial Loss
Cycle Loss
Identity Loss
🖼️ Results

The model learns to:

Convert images from one domain to another
Preserve structure while changing style

(👉 Add your generated images here for better presentation)

⚠️ Challenges
Mode collapse
Training instability
High computational cost
💡 Improvements
Use WGAN-GP for stability
Add attention mechanisms
Use larger datasets
Tune hyperparameters
📚 References
Original CycleGAN Paper:
Unpaired Image-to-Image Translation using Cycle-Consistent Adversarial Networks
👩‍💻 Author

Bushra Abad
FAST NUCES – Computer Science

⭐ Tip

For best results:

Train on GPU (Kaggle / Colab)
Use normalized datasets
Train for more epochs
