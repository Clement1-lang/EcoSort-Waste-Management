# EcoSort Waste Management Assistant

A powered waste management assistant developed as part of the **Summative Lab: NNs and Similar Models** assignment. The project combines image classification, text classification, and retrieval-augmented generation (RAG) to help users identify waste materials and obtain disposal guidance.

## Project Overview

EcoSort is designed to support waste sorting by allowing users to identify waste through an image or a written description. The system predicts the waste category and uses waste management policy documents to generate recycling and disposal instructions.

The project addresses three main tasks:

1. **Image-based waste classification:** Identify waste materials from images using a deep learning model.
2. **Text-based waste classification:** Predict waste categories from written descriptions.
3. **Recycling instruction generation:** Retrieve relevant policy information and generate disposal guidance using a language model.

## Project Objectives

- Explore and preprocess image, text, and policy datasets.
- Build and evaluate an image classification model using transfer learning.
- Develop a text classification model for waste descriptions.
- Implement a RAG-based system for policy-informed recycling instructions.
- Integrate the components into a unified waste management assistant.
- Evaluate the performance and limitations of the resulting system.

## System Components

### 1. Image Classification

The image classification component uses **MobileNetV2 transfer learning** to classify waste images into the nine categories used in the notebook.

Key steps include:
- Image resizing to 224 × 224 pixels.
- Image preprocessing and normalization.
- Transfer learning with a pretrained MobileNetV2 model.
- Training and fine-tuning the classification model.
- Evaluation using test accuracy and classification performance analysis.

**Reported test accuracy: 83.13%**

### 2. Text Classification

The text classification component predicts a waste category from a written description.

The implemented pipeline uses:
- Text descriptions from `waste_descriptions.csv`.
- TF-IDF to convert text into numerical features.
- Multinomial Naive Bayes to classify the descriptions.
- Test-set evaluation to measure predictive performance.

**Reported test accuracy: 99.50%**

This component uses a traditional machine-learning approach, which is one of the alternatives permitted by the assignment.

### 3. Recycling Instruction Generation with RAG

The RAG component combines document retrieval with language generation to produce recycling and disposal guidance.

The implementation uses:
- Policy documents stored in `waste_policy_documents.json`.
- TF-IDF-based document retrieval to find potentially relevant policy information.
- `google/flan-t5-small` as the text generation model.
- Retrieved policy context to help generate waste disposal instructions.

The purpose of this component is to ground generated guidance in the available reference documents rather than relying entirely on the language model's general knowledge.

**Important limitation:** The generated instructions were not consistently accurate or relevant in the integrated tests. The retrieval process and generated responses therefore require further evaluation and improvement before real-world use.

## Integrated Waste Management Assistant

The project brings the three components together into one workflow:

1. A user supplies a waste image or written description.
2. The relevant classifier predicts the waste category.
3. The predicted category is used to request recycling or disposal guidance.
4. The RAG component retrieves relevant policy information and generates a response.
5. The assistant returns the classification and generated guidance.

The integrated workflow demonstrates how multiple AI and machine-learning components can be combined to address a practical waste management problem.

## Datasets

The project uses three supporting datasets:

| File or directory | Purpose |
|---|---|
| `realwaste-main/` | Image dataset used for waste classification |
| `waste_descriptions.csv` | Text descriptions and corresponding waste categories |
| `waste_policy_documents.json` | Waste management policies and disposal guidance |

The image dataset contains thousands of waste images. The generated text dataset contains approximately 5,000 descriptions, while the policy document collection provides reference material for recycling instruction generation.

**Dataset availability:** The `realwaste-main/` directory is excluded from this GitHub repository because of its size. You must obtain the RealWaste dataset separately and place it in the location expected by the notebook. The CSV and JSON files are included in this repository.

## Technologies Used

- **Python** — core programming language
- **Jupyter Notebook / Google Colab** — development and experimentation
- **TensorFlow / Keras** — image classification and deep learning
- **MobileNetV2** — pretrained image classification backbone
- **scikit-learn** — TF-IDF vectorization and Naive Bayes classification
- **Hugging Face Transformers** — FLAN-T5 text generation model
- **Pandas and NumPy** — data preparation and manipulation
- **Matplotlib** — visualizing model performance
- **Git and GitHub** — version control and project hosting

## Model Performance

The following results were reported in the project notebook:

| Component | Method | Reported result |
|---|---|---:|
| Image classification | MobileNetV2 transfer learning | 83.13% test accuracy |
| Text classification | TF-IDF + Multinomial Naive Bayes | 99.50% test accuracy |
| Policy-based generation | TF-IDF retrieval + FLAN-T5-small | Qualitative evaluation required |

The classification accuracies measure the performance of the respective classifiers on their test sets. They do not represent the accuracy of the entire integrated assistant.

The RAG component needs additional testing because its generated instructions were not consistently aligned with the retrieved policy information.

## Limitations and Future Improvements

Potential areas for improvement include:

- Improving image classification accuracy and examining commonly confused waste categories.
- Testing the text classifier on descriptions that differ from the generated training data.
- Improving policy document chunking, retrieval relevance, and query matching.
- Ensuring generated instructions accurately reflect the retrieved policy documents.
- Adding citations or references to the specific policy passages supporting each response.
- Evaluating the full assistant on a larger set of realistic user inputs.
- Developing a user-friendly interface for residents.

The system is a prototype developed for an academic assignment. Its generated disposal guidance should be checked against authoritative local waste management instructions before being used for actual disposal decisions.

## Repository Structure

```text
EcoSort-Waste-Management/
├── .gitignore
├── README.md
├── waste_descriptions.csv
├── waste_management_summative.ipynb
└── waste_policy_documents.json
```

The `realwaste-main/` image dataset is intentionally not included in the repository.


## Author

**Clement1-lang**

GitHub: [Clement1-lang](https://github.com/Clement1-lang)


