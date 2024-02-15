# Seedlings-Classification
Introduction
This project aims to classify seedling images into different plant species using machine learning techniques. The dataset consists of images of various plant species, captured under different conditions and growth stages.

Dataset Overview
The dataset contains images of seedlings belonging to multiple plant species, with a focus on wild plants such as loose silky-bent, common chickweed, scentless mayweed, small-flowered cransbill, fat hen, charlock, cleavers, black-grass, and shepherd's purse. However, species common in agriculture, such as sugar beet, maize, and common wheat, are less represented, leading to class imbalance.

Exploration of Image Files
The images are stored in the "nonsegmentedv2" directory, organized by species. The file names are numerical counters, with no apparent order or correlation to growth stage. Analysis reveals variability in image sizes, with some images zoomed in or out and additional elements like stones, measuring tape, or container walls present.

Image Size Analysis
An analysis of image sizes reveals a correlation between size and species, suggesting a potential target leakage. The distribution of image widths per species suggests distinct clusters of growth states, indicating that image size may inadvertently reveal species information.

Target Leakage Detection
Further investigation confirms target leakage, as the growth state inferred from image size correlates with species probabilities. This leakage poses a challenge for model training and evaluation, as models may exploit image size rather than plant features for classification.

Clustering of Growth States
Using k-means clustering, growth states are identified based on image sizes, with species probabilities visualized per cluster. This analysis highlights the relationship between image size, growth state, and species, reinforcing the presence of target leakage.

Training with Transfer Learning
To address the small dataset size and leverage pre-trained models, transfer learning with PyTorch is employed. A ResNet-18 architecture pretrained on ImageNet is fine-tuned for seedling classification, focusing on retraining the final fully connected layer.

Model Training
The training loop involves optimizing the model using weighted cross-entropy loss to account for class imbalance. The model is trained for multiple epochs, with learning rate scheduling and evaluation on a validation dataset.

Model Evaluation
The trained model achieves a validation accuracy of approximately 77.5%, demonstrating its ability to classify seedlings. However, the presence of target leakage may impact real-world applicability and generalization.

Explaining Predictions with LIME
Local Interpretable Model-Agnostic Explanations (LIME) is utilized to interpret model predictions and identify important image features. Analysis reveals that the model relies heavily on image size rather than plant characteristics for classification.
![Uploading image.png…]()


Conclusion and Recommendations
In conclusion, this project highlights the importance of thorough data exploration and consideration of potential target leakage in model development. To improve model robustness, future efforts should focus on addressing dataset biases, collecting diverse images representative of real-world scenarios, and developing interpretability techniques to ensure model transparency and reliability.

