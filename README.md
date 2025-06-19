### Commentary on Model Tuning and Design Decisions

This section explains the rationale behind the architectural, regularization, and training choices used in the neural network model:

---

### 1. Model Architecture
- **Deeper and wider layers**: Increased the model capacity with two hidden layers (`256` and `128` units respectively) to capture complex patterns in the tabular data.
- **Activation Function**: Used `LeakyReLU` instead of traditional `ReLU` to avoid the "dying ReLU" problem where neurons stop activating entirely.

---

### 2. Regularization
- **Dropout**: Applied dropout (`0.4` and `0.3`) after each hidden layer to prevent overfitting by randomly dropping neurons during training.
- **L2 Regularization**: Added to Dense layers to penalize large weights, encouraging simpler models that generalize better.
- **Batch Normalization**: Inserted after each Dense layer to stabilize and accelerate training by normalizing layer inputs.

---

### 3. Optimizer and Learning Rate Strategy
- **Optimizer**: Used `Adam` for adaptive learning rate adjustment, which performs well across a variety of tasks with minimal tuning.
- **ReduceLROnPlateau**: Automatically decreases the learning rate when validation performance plateaus, allowing fine-tuning of weights toward convergence.

---

### 4. Training Management
- **EarlyStopping**: Stops training when the validation loss does not improve for 5 epochs to prevent overfitting and save time.
- **Batch Size**: A moderate batch size (`512`) was chosen to balance convergence speed and memory usage.

---

### 5. Evaluation and Comparison
- **Evaluation Metrics**: Accuracy alone is insufficient due to class imbalance. Macro and weighted Precision, Recall, and F1-score were used to better understand model performance.
- **Confusion Matrix**: Provided to visualize per-class prediction performance.
- **Random Forest Classifier**: Used as a baseline ensemble method. It often performs well on structured data due to its ability to naturally capture feature interactions without requiring much preprocessing.

---

These decisions reflect best practices in deep learning for tabular datasets and aim to balance bias-variance tradeoff while ensuring interpretability and reproducibility.
