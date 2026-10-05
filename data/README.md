# Data Plan

## Dataset Source

We plan to use TrashNet, a public waste-image dataset available through its original repository:

https://github.com/garythung/trashnet

TrashNet contains 2,527 images across six labeled categories: cardboard, glass, metal, paper, plastic, and trash. The images are already organized into category folders (Thung and Yang).

## Planned Preparation

- Inspect images for unreadable files, duplicates, and labeling issues.
- Create an approximately 70% training, 15% validation, and 15% testing split, with all six categories represented.
- Keep duplicate or closely related images in the same split to avoid data leakage.
- Resize and normalize images for EfficientNet-B0 (PyTorch).
- Apply any data augmentation only to training images.
- Use validation data for tuning.
- Keep the test set untouched until final evaluation.

These are planned steps; we have not prepared or split the dataset yet.

## Limitations

Class sizes vary, with only 137 images in the trash category. The original photos use white posterboard backgrounds, so performance may differ on photos with more complex backgrounds (Thung & Yang, n.d.).

We will review performance for each category and evaluate a separate sample of phone photos.

## Data Storage

For the midterm, this repository documents the dataset source and preparation plan. We will download the images into our training environment when implementation begins.

## Reference

PyTorch. “Efficientnet_B0 — Torchvision 0.26 Documentation.” Pytorch.Org, 2024, docs.pytorch.org/vision/stable/models/generated/torchvision.models.efficientnet_b0.html. Accessed 5 Oct. 2026.

Thung, Gary, and Mindy Yang. “Garythung/Trashnet.” GitHub, 2 Dec. 2020, github.com/garythung/trashnet. Accessed 5 Oct. 2026.
