# MULTI-COLOR-BALANCE-FOR-COLOR-CONSTANCY

_By Oscar Agyei and Alena Iureva_


Based on the paper **ICIP 3 - MULTI-COLOR BALANCE FOR COLOR CONSTANCY [^11]**

[^11]: Akazawa, Teruaki, Yuma Kinoshita, and Hitoshi Kiya. "Multi-color balance for color constancy." arXiv preprint arXiv:2105.10228 (2021).

## How to use

Load `Process.ipynb` from the repository root. Ensure that all libraries are imported and run all the function definitions.

To prepare the data: 
* Put the ground truth and the other pictures one wants to test the tool into a single folder, anywhere on the computer.
* Load the folder's content to https://imglab.in/, select the colors to be the target colors with the rectangle tool on each picture.
* Give a color category to each rectangle. Do not forget to press Enter once the category is set! It is also assumed that the number of rectangles is identical on each picture, and every label is unique within a picture.
* Download the labeling in COCO JSON format, put it into the same folder, and name the file `images.json`.

To do the color correction:
* Create a directory in which one would like the results to be put
* Run a cell with `process_folder(imdir, gt, resdir)`, where `imdir` is the path to the directory of your pictures, `gt` is the filename of the ground truth image, and `resdir` is the path to the output directory
* Wait -- every image takes around a minute to process

To evaluate the result:
* Copy the ground truth image to the results directory.
* With https://imglab.in/, create a labeling, similar to "To prepare the data" steps, but with all colors you want to evaluate.
* Put the resulting COCO JSON labeling to the same directory, names `images.json`.
* Run a cell with `res=eval_result(imdir, gt)`, where `imdir` is the path to the directory of your pictures, and `gt` is the filename of the ground truth image
* The variable `res` will contain the mean angle between ground truth and the rest for every color labeled and the standard deviation of this angle.


## References