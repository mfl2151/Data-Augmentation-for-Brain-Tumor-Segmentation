# Data-Augmentation-for-Brain-Tumor-Segmentation

This project proposes testing different augmentation techniques to improve tumor segmentation performance.

Using the BraTS 2019 Dataset, we used a U-Net to segment the images and develop masks of the tumor from the given images. 
From this segmentation process, we determined the Dice coefficient. 

We then applied image transformations like flips and rotations to the images. 
All of these methods increased the dataset by providing different tumors from which the model could learn. 
However, based on previous work, these methods are sometimes insufficient in creating training data that is variable enough to be useful. 
Therefore, we included elastic distortions in our transformations to create brain tumor training data with arbitrary but physiologically similar shapes. 

Four trials of the data augmentation were tested: 
1) In the first trial, all of the images were either rotated 180 degrees, flipped along the horizontal axis, or flipped along 
the vertical axis, with an elastic deformation (alpha = 100, sigma = 10) then being applied to all the images. 
2) In the second trial, the images were flipped vertically with the elastic distortion applied to the transformed images.  
3) The third trial was conducted like the first with the notable exception that the parameters for elastic deformation were 
changed to alpha = 720 and sigma = 24 (resulting in a much more deformed image). 
4) In the fourth trial, all of the images were only flipped (along both axes)  or rotated without any elastic deformation.   
 
Once the augmentation process is completed, the new images, along with the previous dataset, were ran through the 
tumor segmentation algorithm again. The Dice coefficient was again determined for the second segmentation process. 
If the Dice coefficient of the segmentation process after augmentation is larger than the original Dice coefficient, 
we can conclude that the data augmentation methods were successful in adding new data that will help train the model. 
