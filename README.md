# Augmented_Reality
Augmented Reality with Python, Numpy and OpenCV

## Usage

- Place the image of the surface to be tracked inside the `reference` folder.
- On line 36 of `src/ar_main.py` replace `'model.jpg'` with the name of the image you just copied inside the `reference` folder.
- On line 40 of `src/ar_main.py` replace `'fox.obj'` with the name of the model you want to render. To change the size of the rendered model change the scale parameter (number `3`) in line 103 of `src/ar_main.py` by a suitable number. This might require some trial and error.
- Open a terminal session inside the project folder and run `python src/ar_main.py`
- `feature_matching.py` will show the images with their features drawn on them. It will also show the comparison between the matched features of a reference and a target image.
  - On line 9, replace `book.jpg` with a picture that you copy to `reference` folder and whose features you would like to see drawn on it
  - On line 29, replace `book.jpg` with your reference image and on line 31, replace `video_screenshot.png` with your target image to see the matched features in both images.
  - Open terminal and run `feature_matching.py` to see image features, matched features between reference and target image, and a rectangle drawn around the target image based on features detected.


## Troubleshooting

**If you get the message**:

```
Unable to capture video
```
printed to your terminal, the most likely cause is that your OpenCV installation has been compiled without FFMPEG support. Pre-built OpenCV packages such as the ones downloaded via pip are not compiled with FFMPEG support, which means that you have to build it manually.

**If you get the error**:

```
Traceback (most recent call last):
File "src/ar_main.py", line 174, in
main()
File "src/ar_main.py", line 40, in main
obj = OBJ(os.path.join(dir_name, 'models/fox.obj'), swapyz=True)
File "[...]/augmented-reality/src/objloader_simple.py", line 16, in init
v = v[0], v[2], v[1]
TypeError: 'map' object is not subscriptable
```
The most likely cause is that you are trying to execute the code with Python 3 and the code is written in Python 2. The `map` function in Python 3 returns an iterable object of type map, and not a subscriptible list. To fix it, change the calls to `map()` by `list(map())` on lines 14, 19 and 24 of `src/objloader_simple.py`. 

## Explanation

See this blog entries for an in-depth explanation of the logic behind the code:

* [Part 1](https://bitesofcode.wordpress.com/2017/09/12/augmented-reality-with-python-and-opencv-part-1/)
* [Part 2](https://bitesofcode.wordpress.com/2018/09/16/augmented-reality-with-python-and-opencv-part-2/)

## Source
https://github.com/juangallostra/augmented-reality

