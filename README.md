# Smart Recycling Helper

ITAI 1378  
Midterm Project: The Blueprint

## Team Members

- Viktoriya Kurmisheva
- Tien Manh Nguyen

## Project Tier

**Tier 1: Core Project**

Our project uses one image-classification model to perform one main task: predicting the waste category of a single item in a photo.

## Problem Statement

People may be unsure which waste category an item belongs to. Students, households, schools, and businesses could benefit from a tool that identifies common waste categories before they check local disposal rules.

## Solution Overview

Smart Recycling Helper will accept a photo of one waste item and predict its category using a fine-tuned EfficientNet-B0 model. It will display the predicted category and a confidence score. The system identifies waste categories, it does not determine whether a local recycling program accepts an item.

## Solution Workflow

Upload a photo → resize and normalize the image → run the fine-tuned EfficientNet-B0 model → select the category with the highest model score → display the category and confidence.

## Technical Approach

- **CV technique:** Image classification
- **Model architecture:** Convolutional Neural Network (CNN)
- **Model:** EfficientNet-B0 (PyTorch)
- **Usage method:** Transfer learning
- **Framework:** PyTorch and Torchvision
- **Compute:** Google Colab free tier

EfficientNet-B0 is a convolutional neural network designed for image classification. It learns visual patterns in images and uses them to predict a category. Torchvision provides the model with pretrained weights, which we will adapt for our waste-classification task (PyTorch).

We will start with pretrained weights, replace the final classifier with six outputs, and train the model using TrashNet. Transfer learning gives us a starting point instead of training a model from scratch. One classifier keeps the project focused and fits our Tier 1 scope.

## Data Plan

- **Dataset:** TrashNet
- **Source:** Original TrashNet repository
- **Size:** 2,527 images
- **Labels:** Cardboard, glass, metal, paper, plastic, and trash
- **Existing labels:** Images are already organized into category folders
- **Link:** https://github.com/garythung/trashnet

TrashNet contains the following class counts (Thung and Yang):

| Category | Images |
|---|---:|
| Cardboard | 403 |
| Glass | 501 |
| Metal | 410 |
| Paper | 594 |
| Plastic | 482 |
| Trash | 137 |
| **Total** | **2,527** |

### Planned Preparation

We will inspect the images for unreadable files, duplicates, and labeling issues before creating separate training, validation, and test sets. Our proposed split is approximately 70% training, 15% validation, and 15% testing, with each category represented in all three sets.

We will resize and normalize images for the model. We may apply augmentation to training images to introduce variation. We will use validation data for tuning and keep the test set untouched until final evaluation.

## Success Metrics

These are proposed targets, not achieved results.

| Metric | Target |
|---|---|
| Test accuracy | At least 90% |
| Macro F1-score | At least 0.85 |
| Average inference time | No more than 1 second per image on the Colab runtime used |

We will report the runtime hardware and measure inference time after loading and warming up the model. We will use a confusion matrix and per-class precision, recall, and F1-scores to understand mistakes.

## Milestone Plan

| Phase | Planned Work | Week |
|---|---|---|
| Blueprint | Complete the proposal, README, data plan, and initial AI usage log | Week 10 |
| First Working Demo | Run pretrained EfficientNet-B0 on sample images to verify the input-to-output pipeline | Week 11 |
| Make It Yours | Prepare TrashNet, train the six-category classifier, and display predictions | Weeks 12–13 |
| Improve and Measure | Tune using validation data, evaluate the untouched test set, and record metrics | Week 14 |
| Package and Present | Complete the demo video, final slides, README, and documentation | Week 15 |

The first demo will check that the pipeline runs. The standard pretrained model will need adaptation and training before it can predict our six waste categories.

## Risks and Mitigation

| Risk | Plan B |
|---|---|
| Similar-looking materials may cause incorrect predictions | Review the confusion matrix, apply training augmentation, and adjust training using validation results |
| Phone photos may have different lighting, angles, and backgrounds from the dataset | Evaluate a separate set of phone photos and consider adding new training examples without reusing evaluation images |

TrashNet photos use a white posterboard background, which may limit performance on more varied backgrounds (Thung & Yang, n.d.).

## Resources and Cost

- **Training and testing:** Google Colab free tier
- **Model and framework:** EfficientNet-B0, PyTorch, and Torchvision
- **Dataset:** TrashNet
- **Version control and documentation:** GitHub
- **Expected project cost:** $0

We will use free-tier or open-source resources. If Colab GPU access is unavailable, we will use a CPU for small pipeline checks and resume training when free compute is available.

## Repository Structure

- `README.md` — Project Blueprint
- `data/README.md` — Dataset source and preparation plan
- `docs/proposal.pdf` — Midterm proposal slides
- `docs/AI_usage_log.md` — Each team member's AI assistance entries
- `notebooks/` — Notebooks added as implementation begins

## Team Contributions

- **Viktoriya:** Prepared proposal slides 1–4 and created the GitHub repository.
- **Tien:** Prepared proposal slides 5–8.

We will update this section as we complete additional work.

## AI Usage Log

We will document AI assistance, our decisions, and what we learned in [docs/AI_usage_log.md](docs/AI_usage_log.md). Each team member will record their own AI use.

## Demo Video

The final demo video link will be added when the working system is ready.

## Current Status

- [x] Project idea and Tier 1 selected
- [x] Planned dataset and model selected
- [x] GitHub repository created
- [ ] Proposal completed and submitted
- [ ] Data README added
- [ ] AI usage log added
- [ ] First working demo completed
- [ ] Six-category model trained
- [ ] Metrics measured
- [ ] Final deliverables submitted

## References

Thung, G., & Yang, M. (n.d.). *TrashNet* [Dataset and source code]. GitHub. https://github.com/garythung/trashnet

PyTorch. (n.d.). *efficientnet_b0*. Torchvision documentation. https://docs.pytorch.org/vision/stable/models/generated/torchvision.models.efficientnet_b0.html
