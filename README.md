# ImageToText
A project to detect and interpret text from images.

### Installing the environment
Note: You will need the Anaconda Package Manager to be able to run the code in this repo.
Run the following command from the root directory, to create a conda environment for the code (you can replace imgtotext with any other environment name):

``` conda create --name imgtotext --file spec-file.txt ```

Next, run the following command to activate your newly created environment:

``` conda activate imgtotext ```

Now, we want to download a model from spacy:

``` python -m spacy download en_core_web_md  ```

Now we are ready to run the text recognition program! Run the following command:

``` python text_recognition.py --east frozen_east_text_detection.pb --folder images/ -v ```

- The `east` flag takes in the text_detection pretrained model.
- The `folder` argument takes in the path to any folder containing images on which you want to perform text recognition.
- The `v` flag, short for visualize, lets you visialize the process of recognizing each word in each image. NOTE: it is recommended to run the code without this flag, in order to minimize runtime.

### Output
The program, in addition to visualizing, performs named entity recognition on the text extracted from the images. The results of ner are recorded in `counts.txt` as tuples, where each tuple consists of (the entity, its type, the number of times it occurs, and the images in which it occurs). The tuples are sorted in descending order by the counts of entity occurrences. 

### Hardware
This code was run on osx (mac OS Catalina 10.15.3), using python 3.6

### Benchmarks
The [EAST detector](https://arxiv.org/abs/1704.03155) used for text detection, when tested on the ICDAR 2015 Challenge 4 Incidental Scene Text Localization task, achieves `0.83` Precision, `0.78` Recall, and an F1 score of `0.8`. However, one must note that this system was trained for scene text localization, so your mileage may vary.

It takes about `7` seconds to process each image on my machine, but again, YMMV.