# Copy and Paste-Augmentation

[![Generic badge](https://img.shields.io/badge/License-MIT-<COLOR>.svg?style=for-the-badge)](https://github.com/qubvel/segmentation_models.pytorch/blob/master/LICENSE)

Original paper by : [Simple Copy-Paste is a Strong Data Augmentation](https://arxiv.org/abs/2012.07177)


- This function is originated from above paper
- Scale Jittering is applied so that it could resemble more of the paper
- Not yet supported with bounding boxes. Only semantic segementation mask is available.

<!--Table-->

|Images||
|--|--|
|<img src="/home/junshick/Workspace/Personal_project/Copy-Paste-Augmentation/example_images/cute_dog.jpeg" height="200" width="250">|<img src="/home/junshick/Workspace/Personal_project/Copy-Paste-Augmentation/example_images/happy_people.jpeg" height="200" width="250">|<img src="/home/junshick/Workspace/Personal_project/Copy-Paste-Augmentation/example_images/dog&people1.png" height="200" width="200">|

</br>

|Copy and paste|||
|--|--|--|
|Image|<img src="/home/junshick/Workspace/Personal_project/Copy-Paste-Augmentation/example_images/dog&people1.png" height="200" width="250">|<img src="/home/junshick/Workspace/Personal_project/Copy-Paste-Augmentation/example_images/dog&people2.png" height="200" width="250">|
|Mask|<img src="/home/junshick/Workspace/Personal_project/Copy-Paste-Augmentation/example_images/dog&people1&mask.png" height="200" width="250">|<img src="/home/junshick/Workspace/Personal_project/Copy-Paste-Augmentation/example_images/dog&people2&mask.png" height="200" width="250">


</br>

### How To Use

Integrated with pytorch dataset format. 

1. First make an instance with two types of parameters
    - p : probability of applying the transform. (default=0.5)
    - scale_jittering : Scale range to use, `0`  means original scale and `-1` is 100% zoom in whereas `2` would be 100% zoom out. Parameters must be in shape of tuple (ex. (-2, 1)). Maximum range is (-5, 5) meaning (-500%, 500%). (default=(-2, 2))
    
    </br>
2. Pass in four key words (image1, mask1, image2, mask2)

    - image1 will be the image to paste in.
    - image2 is the image which implements scale jittering and expectes for the image1 to be pasted.

    |Image1|Image2|CopyPaste|
    |--|--|--|
    |<img src="/home/junshick/Workspace/Personal_project/Copy-Paste-Augmentation/example_images/cute_dog.jpeg" height="150" width="200">|<img src="/home/junshick/Workspace/Personal_project/Copy-Paste-Augmentation/example_images/happy_people.jpeg" height="150" width="200">|<img src="/home/junshick/Workspace/Personal_project/Copy-Paste-Augmentation/example_images/dog&people1.png" height="150" width="200">|

    ```python

        from copypaste import CopyPaste

        copy_paste = CopyPaste(p=0.5, scale_jittering=(-2, 2))
        self.copy_paste = copy_paste(image1, mask1, image2, mask2)
    ```
 
