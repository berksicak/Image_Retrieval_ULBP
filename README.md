# Image_Retrieval_ULBP
METHOD:
The problem is to fetch the most similar images in the train folder of a given image. This method is the uniform local binary pattern method. 
We don't need the color information of the image for this process, so we just need to get the Y value in YCbCr space from the image in RGB space.
Then the local binary pattern is applied and the histogram is created. The histograms are normalized and written to a file for comparison with other
images. While looking at the similarity of the two images, the manhattan distance and the distance are found on the histograms and the closest ones
are brought.

a) Converting images under the 'train' folder from RGB to gray:
Here, the 'rgbToGray' function converts the given color image to gray. For each pixel value, the luminance value is found with the formula
'16 + (65.738*red[i,j] + 129.057*green[i,j] + 25.064*blue[i,j])/256' and new gray level pixels are created and added to the matrix. is discarded.

b) Applying Uniform Local Binary Pattern on the gray image and obtaining histogram:
Here, the 'uniform_local_binary_pattern' function returns a uniform local binary pattern histogram from the gray level image it takes as a parameter.
It creates an 8-bit binary number for each center pixel by comparing it with the 8 pixels around it. In the comparison process,
if the central value is large, 1 is written, if it is small, 0 is written. Then, if there are more than 2 '0-1' or '1-0' transitions in the bit array,
there is no pattern here, so the histogram is written as 0, if less than 2, the index of the 8-bit number in the decimal value of the histogram
is incremented by 1. Then the histogram normalization process is applied and the histogram is returned.

c) Train operation:
Here, the 'train' method filename parameter is taken. The 'rgbToGray' function is applied to all the photos under the Train folder, 
and the 'uniform_local_binary_pattern' is applied to the gray image obtained. All histograms obtained are thrown into the array and a file named 
filename is created, and the array is written to that file with the pickle library.

d) Test process:
Here, the 'uniform_local_binary_pattern' is applied to all images under the test folder with the 'test_all' method as in the 'train' method.
For each of the images in the test folder, manhattan distance and histogram similarity are checked. The distances and paths of the 3 images 
with the lowest histogram distances are returned. At the same time, achievements are displayed for each class and for each image.

Accuracies :
Banded :%66
Bubbly :%66
Chequered :%33
Cobebbed :%33
Crystalline : %66
Dotted : %0
Honeycombed : %66
Striped : %33
zigzagged : %66

Result:
When the success rates are examined, the accuracy is 77,777 for the images in the testForDocument, and 48,148 for the images in the test folder.
There is 66% accuracy for banded, bubbly, crystalline, honeycombed, zigzagged classes. Checkered, cobwebbed, striped classes have 33% accuracy.
Finally, there is 0% success for the dotted class. Although the dotted class in the test was 0, the dotted class image in the test images prepared for
the report was able to bring the correct image. Increasing the number of images to be trained will increase the accuracy of the program. An accuracy of 
close to 50% in overall success shows that tissue similarity is a good method in Content Based Image Retrieval. Although machine learning with higher 
accuracy rates performs lower than deep learning methods, it is more successful in terms of processing load and process speed.
