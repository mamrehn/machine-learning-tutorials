
# Libraries

A short [overview](http://www.pyimagesearch.com/2014/01/12/my-top-9-favorite-python-libraries-for-building-image-search-engines/) of the libraries mentioned.

At [http://pythonvision.org](http://pythonvision.org/basic-tutorial) there are some basic python computer vision introductions on counting, segmentation, seed points and watershed. BEWARE that they are rather old and may not work with python 3.x.
## Numpy
Numpy is the base of scientific libraries such as SciPy, scikit-learn, scikit-image and OpenCV. 

- [Introduction into NumPy](http://www.python-course.eu/numpy.php)
- [Array Indexing](http://docs.scipy.org/doc/numpy/reference/arrays.indexing.html)

## SciPy
Library for scientific computing with python. The `ndimage` API for example can be found at [docs.scipy.org](http://docs.scipy.org/doc/scipy-0.14.0/reference/ndimage.html).

[Tutorials](http://scipy-lectures.github.io/advanced/index.html) from their website
- [Image manipulation and processing](http://scipy-lectures.github.io/advanced/image_processing/)

## Matplotlib
Matplotlib's API is similar to Matlab plotting.

- [How-Tos compilation](http://matplotlib.org/faq/howto_faq.html)

## Scikit-image
Written in python and cython, focussed on image processing in general (denoising, segmentation, ...).
It is part of the scikit (short for SciPy toolkits) [packages](http://scikits.appspot.com/scikits).

- [API](http://scikit-image.org/docs/dev/api/api.html) for image [io](http://scikit-image.org/docs/dev/api/skimage.io.html), i.e. loading and converting one or multiple images

## OpenCV
Written in C++ (python wrapper cv2 exists), focussed primarily on computer vision (feature detection and extraction, classification, ...). Differentialisation to scikit-learn in the [newsgroup](https://groups.google.com/forum/#!topic/scikit-image/IKp_odGWwlE).

Preprocessing and feature extraction
- [Histogram](http://opencv-python-tutroals.readthedocs.org/en/latest/py_tutorials/py_imgproc/py_histograms/py_table_of_contents_histograms/py_table_of_contents_histograms.html#table-of-content-histograms)
- [Image Gradients](http://opencv-python-tutroals.readthedocs.org/en/latest/py_tutorials/py_imgproc/py_gradients/py_gradients.html)
- [Canny Edge Detection](http://opencv-python-tutroals.readthedocs.org/en/latest/py_tutorials/py_imgproc/py_canny/py_canny.html)

Segmentation
- [Hough Line Transform](http://opencv-python-tutroals.readthedocs.org/en/latest/py_tutorials/py_imgproc/py_houghlines/py_houghlines.html)
- [Hough Circle Transform](http://opencv-python-tutroals.readthedocs.org/en/latest/py_tutorials/py_imgproc/py_houghcircles/py_houghcircles.html)

- [Watershed Image Segmentation](http://opencv-python-tutroals.readthedocs.org/en/latest/py_tutorials/py_imgproc/py_watershed/py_watershed.html)
- [Interactive Foreground Extraction using GrabCut ](http://opencv-python-tutroals.readthedocs.org/en/latest/py_tutorials/py_imgproc/py_grabcut/py_grabcut.html), Video on [Youtube](http://www.youtube.com/watch?v=kAwxLTDDAwU)
- [Contour](http://opencv-python-tutroals.readthedocs.org/en/latest/py_tutorials/py_imgproc/py_contours/py_table_of_contents_contours/py_table_of_contents_contours.html#table-of-content-contours)

## MedPy

- [Graph-cut (max-flow/min-cut)](http://pythonhosted.org/MedPy/graphcut.html)
- Github [wiki](https://github.com/loli/medpy/wiki/Basic-image-manipulation)

## More
- [tutorials](http://opencv-python-tutroals.readthedocs.org/en/latest/py_tutorials/py_imgproc/py_table_of_contents_imgproc/py_table_of_contents_imgproc.html) ([github](https://github.com/abidrahmank/OpenCV2-Python-Tutorials/tree/master/source/py_tutorials/py_imgproc))

# Examples
Some further examples of the libraries in action

- [openCV and scikit-image](http://dimitri-christodoulou.blogspot.de/2014/04/mixing-opencv-and-scikit-image.html)
