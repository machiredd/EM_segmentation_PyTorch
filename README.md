# EM_segmentation_PyTorch

A ResUNet model to segment organelles in electron microscopy images

ResUNet is applied to 3D electron microscopy (EM) images of tumor biopsies obtained from patients with metastatic breast and pancreatic cancer to segment intra-cellular organelles. ResUNet is trained on a small subset of manually labeled images evenly distributed in the 3D EM image stack to efficiently segment the rest of the images in the stack.

EM images are typically of size around 6000x4000. Due to the memory limitations of GPU hardware, the images are cropped into tiles of 512x512 and fed into ResUNet. In order to include global information I take crops of size 2048x2048 and downsample them to 512x512. Model trained on these crops is used to predict organelles in test images. Test images are also cropped as overlapping tiles and the predictions are rescaled and stitched to form the final segmentation mask.
