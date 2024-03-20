# Overview
This project will use neural networks to analyze and predict the presence of pneumonia in pediatric chest X-rays.

Iterative analysis of thousands of healthy and unhealthy lung scans using deep learning yields predictive capabilities that may be accurate enough for supplemental or academic use. Our final model has an 89% accuracy rate, particularly excelling in the prediction of positive cases. Adding speed to routine diagnoses would be exceedingly helpful for any healthcare system, allowing doctors to deliver effective care to more patients and freeing up more time to focus on individual concerns or serious complications.

# Business Problem
Medicine is a cornerstone of society. Not only are advances in patient care vital to raising life expectancies worldwide, but they are essential to the global economy, representing more than 12 trillion dollars every year.

Both in the United States and abroad, however, clinicians are facing a crisis. As doctors increasingly become spread more and more thin, they will need the assistants of advanced tools to correctly diagnose more patients in a timely manner. The model created in this project is a step towards making that a reality. This project will examine over 5500 X-rays from real pediatric patients, using deep learning techniques to extract key indicators of pneumonia and, through doing so, teach our models to "read" an X-ray just like a person would. Positive results could set the stage for a myriad of uses that range all the way from classrooms to hospitals.

# Data Understanding
The data for this project is a set of 5863 anterior-posterior chest X-ray images. They feature both healthy lungs and lungs that are infected with either viral or bacterial pneumonia. They are split into two subset and labeled "Normal" or "Pneumonia". The images come from cohorts of pediatric patients of one to five years old from Guangzhou Women and Children’s Medical Center in China.

The images have also already been split into training, validation, and test sets, with the training set containing the vast majority of the images. The validation set is poorly constructed and only has 16 images, something we will adress during preprocessing.

Our target for this project will be optimizing the accuracy of our neural networks. In other words, we want our models to be able to accurately predict whether or not a given chest X-ray indicates pneumonia or not. Having the preset labels is handy, because we already know the true value of each image (e.g. whether or not the lung is healthy). The positive case today will be class 1, meaning that the patient in the image has pneumonia. The negative case will be class 0, or that the patient is healthy.

There are no initial features to begin with here, as the model will be learning to read important parts of the images during training.

## Limitations
As is often the case, our dataset is fairly small and imbalanced. While the images are high-quality, there are not too many of them, especially when it comes to "Normal" images of healthy lungs.

This could affect our model's ability to generalize to unseen data. For medical images, extremely accurate generalization is especially important if machine learning models hope to be feasible for clinical use.

# Methods
This analysis uses various deep learning techniques. Namely, it focuses on different variations of neural networks. We employ multi-layer perceptrons, convolutional neural networks, and transfer learning using MobileNet-v2. Each model is tuned to improve performance on target metrics.

# Results
Our final model features transfer learning using a large pre-trained model. The base layers of this model were frozen and not trainable, but multiple Dense layers and a pooling layer were added to help tune the model to our particular dataset. As before, the model was optimized for accuracy. 

The table below shows how the models improved over iterations:

| Model Type         | Train Accuracy | Validation Accuracy | Test Accuracy | Test Recall | Time To Run |
|--------------------|----------------|---------------------|---------------|-------------|-------------|
| Baseline MLP       | 90.8%          | 91.5%               | 71%           | 62%         | 10 min.     |
| Dropout MLP        | 92.9%          | 94%                 | 78%           | 71%         | 22 min.     |
| CNN                | 95%            | 93.7%               | 83%           | 79%         | 5 min.      |
| Tuned MobileNet-v2 | 92.2%          | 90.6%               | 89%           | 88%         | 4 min.      |

The final product saw large improvements in performance almost all the way across the board. We saw a solid in our accuracy score, as well as improved recall for the negative case, had been a problem to optimize for previously.

# Conclusions
Our iterative modeling process has yielded a model with solid performance gains and generalization capabilities. Using transfer learning was the most effective tool, achieving 89% accuracy and a huge bump in recall for the negative class. As the our final confusion matrix confirms, we are really starting to move the needle on false positives, which has proved problematic throughout. We have maintained excellent recall on the positive case, meaning our false negatives remain quite low overall.

While the model may not yet be ready for heavy use in a clinical setting, the foundation is there and it looks very promising. With larger datasets and more fine-tuning methods, our model could one day save physicians and patients precious time by quickly and accurately diagnosing a common yet potentiall deadly illness.

Based on this project's findings, our recommendations are:

- **Limit clinical use without strict supervision**
- **Use as second opinion for suspected positive cases**
- **Use for physician training**

Our recommendations focus on this model's use within a larger supervised structure, as it is not accurate enough to be trusted alone. In the hands of a skilled medical staff, however, it can be a powerful tool, especially when pneumonia is already suspected. It can also be used in medical schools or for resident training, as it could prove a quick and effective way to test a trainee's ability to read chest X-rays themselves.

## Next Steps
While our model is performing well, many improvements can still be made. Namely, more data is vital to achieving better generalization outcomes, as we have shown a consistent ability to optimize for loss using various architectures. Seeing a larger variety of X-rays and more presentations of sick and healthy lungs would allow for large leaps in predictive capabilites on unseen data. Further analysis could include:

- Prediction explainability using LIME
- Complex CNNs that require more compute
- Image augmentation during training

## Contact Information
- Email: apell7591@gmail.com
- Phone: 917-434-6615
- GitHub: apell7594
- LinkedIn: Adam Pell
