

# ST-PIGT-DFR: Spatio-Temporal Physics-Informed Graph Transformer with Dynamic Flow Routing

## 📌 Overview

**ST-PIGT-DFR** is a novel hybrid deep learning architecture for **flood forecasting** in large and complex river networks.
It combines:

* **Graph Neural Networks (GAT)** for spatial dependency modeling
* **Transformers** for temporal sequence learning
* **Physics-Informed Neural Networks (PINNs)** for hydrological law enforcement
* **Dynamic Flow Routing** to adapt graph topology in real time
* **Uncertainty Quantification** for reliable operational forecasts

This framework is designed to improve **accuracy, interpretability, and robustness** in predicting river discharge, particularly during **extreme flood events**.

---

## 🚀 Key Features

* **Dynamic Graph Construction** – Adapts to real-time hydrological similarity between gauges.
* **Physics-Guided Transformer Attention** – Embeds mass and momentum constraints into temporal modeling.
* **Adaptive PINN Weighting** – Activates physical laws only when precipitation-driven dynamics are significant.
* **Flow-Type-Aware Multi-Task Learning** – Separate prediction heads for upstream, downstream, bidirectional, and isolated gauges.
* **Uncertainty Quantification** – Uses Monte Carlo Dropout for reliable prediction intervals.

---

## 📂 Repository Structure

```plaintext
├── data/                     # Datasets & preprocessing scripts
├── src/                      # Source code for model, training, and evaluation
│   ├── models/               # GAT, Transformer, and PINN modules
│   ├── utils/                # Helper functions
│   ├── train.py              # Training script
│   ├── evaluate.py           # Evaluation script
├── notebooks/                # Jupyter notebooks for experiments
├── results/                  # Output results, figures, and metrics
├── requirements.txt          # Python dependencies
└── README.md                 # Project documentation
```

---

## 📊 Dataset

The model was trained and evaluated on **real-world hydrological data** from multiple gauges in large river networks, such as the **LamaH-CE dataset**.
**Inputs**:

* Historical river discharge
* Estimated precipitation (via runoff ratio)
* Catchment attributes (area, slope, etc.)

**Outputs**:

* 1-day-ahead streamflow forecasts
* Prediction intervals for uncertainty estimation

---

## ⚙️ Methodology

1. **Dynamic Flow Routing Graph**

   * Builds a directed acyclic graph (DAG) of gauges
   * Updates edge weights based on hydrological similarity

2. **Directed Graph Attention Network (D-GAT)**

   * Propagates static catchment features through dynamic edges

3. **Physics-Guided Transformer**

   * Temporal modeling guided by flow direction & precipitation trends

4. **Physics-Informed Neural Network (PINN) Losses**

   * **Continuity loss** – mass conservation
   * **Momentum loss** – slope & channel flow dynamics
   * **Spatial consistency loss** – downstream flows ≤ upstream flows

5. **Multi-Task Prediction & Uncertainty Quantification**

   * Four prediction heads based on flow type
   * Monte Carlo Dropout for confidence intervals

---

## 📈 Performance

* **Nash–Sutcliffe Efficiency (NSE)**: **0.873**
* **RMSE**: **6.24 m³/s**
* **MAE**: **3.75 m³/s**
* **R²**: **0.891**

Physics-informed constraints improved stability during flood peaks and reduced implausible spikes.

---

## 🛠 Installation

```bash
git clone https://github.com/yourusername/ST-PIGT-DFR.git
cd ST-PIGT-DFR
pip install -r requirements.txt
```

---

## ▶️ Usage

**Training the model:**

```bash
python src/train.py --config configs/train_config.yaml
```

**Evaluating the model:**

```bash
python src/evaluate.py --model_path checkpoints/best_model.pth
```

---

## 📌 Citation

If you use this work in your research, please cite:

```bibtex
@article{STPIGTDFR2025,
  title={Spatio-Temporal Physics-Informed Graph Transformer with Dynamic Flow Routing for Flood Forecasting},
  author={Your Name et al.},
  year={2025}
}
```

---

If you want, I can also **add diagrams and a quick-start Colab link** to make the README more engaging and user-friendly for GitHub visitors. That would help your repo stand out visually.
