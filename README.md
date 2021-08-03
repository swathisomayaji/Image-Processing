# Image-Processing
BaggageAI Computer Vision 

Given two sets of images:- background and threat objects. Background images are the background x-ray images of baggage that gets generated after passing through a X-ray machine at airport. Threat images are the x-ray images of threats that are prohibited at airport while travelling.
## Task:
•Cut the threat objects, scale it down, rotate with 45 degree and paste it into the background images using image processing techniques in python.
• Threat objects should be translucent, means it should not look like that it is cut pasted. It should look like that the threat was already there in the background images. Translucent means the threat objects should have shades of background where it is pasted.
• Threat should not go outside the boundary of the baggage. **difficult**
• If there is any background of threat objects, then it should not be cut pasted into the
background images, which means while cutting the threat objects, the boundary of a threat object should be tight-bound.

## Demonstration:

Threat Item

![alt text](https://drive.google.com/file/d/1YsMj3jLTM4Z61D-EKOBgj6YdHuXgkCW\_/view?usp=sharing)

Background

![alt text](https://github.com/swathisomayaji/Image-Processing/blob/main/background_images/BAGGAGE_20180811_175323_83216_B_1.jpg)

Result

![alt text](https://drive.google.com/file/d/1rQor9uybjZo\_kT9qYcqn-eB5-M0O7Xjl/view?usp=sharing)

## Algorithms

### Overall implementation:

1.Load threat objects and background images

2.Cut the threat object

3.Scale it down according to background image

4.Rotate the threat abject by 45 degree

5.Paste it into the background.

### Cut the object:

1.Convert to Grey and find Threshold

2.Morph-op to remove noise

3.Find the max-area contour

4.Crop and add border/padding around the cropped image

5.To make the image background transparent, we first need to change "RGB" to "RGBA"

6.Then we first take out the pixel value of this picture and determine whether the pixel is white (255, 255, 255)  
  
7.Only white pixels are transformed 

### Rotating:
```python
img=img.rotate(45, resample=0, expand=1)   
```
is used.

Applying the positive of the angle to anti-rotate clockwise.Extend=1 because we don't want to crop the outliers.

### OverLaying of image:
```python
overlay_image_alpha(img, img_overlay, x, y, alpha_mask) 
```
is used.

1.img should not contain an alpha channel. (e.g. If it is RGBA, convert to RGB first.)

2.img_overlay has the same number of channels as img.

3.Overlay `img_overlay` onto `img` at (x, y) and blend using `alpha_mask`.

4..`alpha_mask` must have same HxW as `img_overlay` and values in range [0, 1]

5.Blend overlay within the determined ranges

6.Alpha mask is make translucent so that it bends properly with background.


## Output

Accuracy of 88% was achieved with the given data. some object could not be fit into the bag section completely.

More Outputs are attached.
