# Aerial_Drone_Segmentation

The dataset consists of 3,269 images in 12 classes (including background). All images were taken from drones in a variety of scales. Samples are shown below:
![data_montage](https://github.com/user-attachments/assets/a9a180cd-4e4e-4595-989e-231705ff3405)

The dataset consists of landscape images taken from drones in a variety of scales.
This competition is evaluated on the mean Dice coefficient. The Dice coefficient can be used to compare the pixel-wise agreement between a predicted segmentation and its corresponding ground truth.
Calculated a combined loss function comprising the Naive Dice coefficient loss and cross-entropy loss.
I have used deeplabv3_resnet101.
The train_model(...) method has been used to handle the model outputs and calculate the loss. The loss function used for the main branch is dice_coeff_loss(...), and we use a simple Cross-entropy loss for the auxiliary branch. There are no restrictions as to which loss should be for the auxiliary branch.

The metric functions dice coefficient loss.

When using Torchvision models, we need to make a small change to access the outputs from the forward pass. The forward pass of the model returns a dictionary containing two keys, out & aux. The out key holds the output from the main branch path of the model, while the aux key holds the output from the auxiliary branch.

The validate(...) function remains almost unchanged except for the method to access the model outputs. As the auxiliary is not used during inference, the loss is calculated only on outputs of the main branch.

![image](https://github.com/user-attachments/assets/c7a2e7ac-9332-4bdb-97d5-dc88eb4b9078)


Convert masks to Run Length encoded values. To generate the Run-Length Encoding (RLE) for a multi-class prediction mask (i.e., not binary), you'll need to create RLE strings for each class separately. Each class in the mask will have its own RLE string.


