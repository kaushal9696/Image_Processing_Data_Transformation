## [Image Processing] Image Transformation and Image Enhancement

- The goal of this project is data transformation / data representation with
    python.
- This project includes image processing such that performing histogram
    equalization on gray scale image and color image with different contrasted
    image like extreme dark and extreme light images.
- This project includes gradient finding of an image such that the gradient of
    image in x direction, gradient of image in y direction and gradient
    magnitude image. After finding the gradient magnitude of an image,
    applied a threshold on it to find the variance in the image edges.
- Libraries used in this project are NumPy, Scikit-image, Matplotlib and
    Pillow.

## Project

Explanation: -

1. Firstly, import all the necessary packages that mentioned above. In this
    whole scenario, took color image as an input. Here in this case, University’s
    building image is taken as an input and the shape of the image is (1365,
    2048, 3) because it is a color image, it has 3 dimensions. In python, scikit-
    image library is used to read the image by using io function of the package.
    For the gray scale image, this package has a built-in function which reads
    the image as a gray scale image by using io.imread(as_gray=True). So now
    you got both the images, one which is original and other one is a gray scale
    image.



2. The next step is to save both image original and grayscale image as
    original.jpg and grayscale.jpg. Now, Pillow library is being used to read both
    images. (Note: Pillow library read image as image object and Scikit image
    library read image as an array object) now, 2 more images are being
    developed by pillow ImageEnhance.Brightness function, the first is extreme
    light image and the other is extreme dark image. Follow this to get same
    kind of different 2 images from grayscale image such that now total of 6
    images you got.
3. Now when you got 6 different images as follow, original color image,
    extreme dark color image, extreme light color image, grayscale image,
    extreme dark grayscale image, extreme light grayscale image, now one by
    one apply histogram equalization on each image.


4. For histogram equalization, scikit image package is used, in which this code
    is used for histogram equalization, which is originally get histogram of an
    image from NumPy package and then perform histogram equalization.
       hist, bin_edges = np.histogram(image)
       bin_centers = (bin_edges[:-1] + bin_edges[1:]) / 2.
       img_cdf = hist.cumsum()
       img_cdf = img_cdf / float(img_cdf[-1])
       out = np.interp(image.flat, bin_centers, img_cdf )
       out.reshape(image.shape)

5. Next step is plotting, here Matplotlib’s pyplot function is used to plot a
    graph which shows 3 grayscale images as mentioned above and side images
    are histogram equalized images. Every plot is saved as a .png image and the
    explanation of each image is on the last page.
6. Now, as mentioned in step 5, graph has been plotted for 3 different color
    images. Here all the images are made from one single image so you can see
    some similarities of the histogram equalized image.


7. Next step is to find x-scale gradient and y-scale gradient, and gradient
    magnitude of a gray scale image, here gray-scale image is taken because it
    is 2 - dimensional. Here is a code for gradient finding.
       Gradient_X = filters.sobel(grayscale,axis=0) # axis 0 = X
       Gradient_Y = filters.sobel(grayscale,axis=1) # axis 1 = Y
       Gradient_Magnitude = np.sqrt(Gradient_X**2.0 + Gradient_Y**2.0)


8. The last part of this project is thresholding on gradient magnitude such that
    edges become clear. For that, mean of gradient magnitude is used. Here to
    find mean of gradient magnitude, np.mean function is used which is in our
    case is 0.066. so for the thresholding process, in python, there is a simple
    algorithm, Thresholding image = Gradient magnitude > 0.66 (in this case we
    took 0.66). when this formula is applied, all the values >0.66 will become 1 and 
    all the values <= 0.66 become 0. So, it will generate a binary image,    
    where you can see the edges clearly.

9. In last, by playing with the threshold I found out that, sketch image is
    directly made from the thresholding by the simple formula, Sketch of an
    image = grayscale image > Gradient Magnitude, that give us a sketch as
    shown below, this was the thing that I found out by playing around with the
    code.

# Project Output Files by Name

Here are the image’s name files which will be created after executing the code.
(file’s names are by the order of file creation time). That will be found in the same
folder where the script will be executed.

1. Original Color Image: - Original.jpg
2. Original Grayscale Image: - Grayscale.jpg
3. Extreme light Color Image: - Brighten_Original.jpg
4. Extreme light Grayscale Image: - Brighten_Gray.jpg
5. Extreme Dark Original Image: - Darken_Original.jpg
6. Extreme Dark Grayscale Image: - Darken_Gray.jpg
7. Histogram Equalization on all the Grayscale Images in one single plot: -
    Gray_Scale_Histogram_EQ_Figure.png
8. Histogram Equalization on all the Color Images in one single plot: -
    Color_Histogram_EQ_Figure.png
9. Gradient X, Y and Gradient Magnitude with the original Grayscale Image in
    one single plot: - Gradient_Magnitude_X_Y.png
10. Gradient Magnitude image with a Threshold: -
    Threashold_ON_Gradient_mg.png
11. Sketch image from grayscale image which was an amazing experiment: -
    Sketch_Image_Threshold.png

Note: - Every image mentioned above will be created after executing the script.
There Is already 1 image in the folder “Test_Image.jpg” which is the image I
performed all the tasks.

# Conclusion

This project is done with three main goals, first is to get histogram equalized
image of a grayscale image which has two different kinds, one is extreme dark
grayscale image and other one is extreme light grayscale image. Second part is


similar as the first part but here color image is taken as an input image and get
the histogram equalization on that color image. Also, in color image there are 2
different kinds, first is an extreme dark color image and other one is an extreme
light color image. In third part, goal was to get x directional gradient of an image
and y directional gradient of an image. With that two gradient there is a gradient
magnitude calculated with the magnitude equation. In extend to part three, there
is a thresholding implemented on the gradient magnitude image and get the
binary image.

# References

Scikit-image: - https://scikit-image.org/docs/dev/api/skimage.html

Scikit-Image Exposure: - https://scikit-
image.org/docs/dev/api/skimage.exposure.html

Scikit-Image Filter: - https://scikit-image.org/docs/dev/api/skimage.filters.html

Pillow: - https://pillow.readthedocs.io/en/stable/

Pillow Image-Enhance Module: -
https://pillow.readthedocs.io/en/stable/reference/ImageEnhance.html

Matplotlib: - https://matplotlib.org/


