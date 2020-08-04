## What's in here?

This folder contains data for "Cats and Captions vs. Creators and the
Clock: Comparing Multimodal Content to Context in Predicting Relative
Popularity." The bibtex for this article is:

```
@inproceedings{hessel2017cats,
    title={Cats and Captions vs. Creators and the Clock: Comparing Multimodal Content to Context in Predicting Relative Popularity},
    author={Hessel, Jack and Lee, Lillian and Mimno, David},
    booktitle={Proceedings of the 26th International Conference on World Wide Web},
    year={2017},
    organization={International World Wide Web Conferences Steering Committee}
}
```

More info is available at

http://www.cs.cornell.edu/~jhessel/cats/cats.html

if you have additional questions, feel free to contact

jhessel@cs.cornell.edu

## What files are here?

This folder contains image features and pairing information.

### Pairing data

Pairing data is distributed within the json files in pairs.zip. To
load this data in python, you can use something like:

```
import json
with open("aww_data.json") as f:
     data = json.loads(f.read())
```

This dataset contains a) sampling parameters for pairing b) a list of
pairs of reddit submissions. Each pair of reddit submissions contains
the first and second examples (ex1/ex2) and whether or not the example
falls in the training or test set for each split (test_set[i] == 1
means that the example was a test example for split i; indices i =
0-14 were used in the paper). Each reddit submission contains the
following information:

- url: an imgur url that the user submitted
- caption: the caption of the submission
- score: the raw reddit score of the submission (from a 2014 scrape)
- imgurid: the parsed imgur id of the submission
- id: the reddit id of the post (can be used to match against image features)
- time: the UTC timestamp of submission
- fname: the filename of the raw jpeg images were extracted from
- folder: the folder where the raw jpeg lives
- social: a list of social features for that reddit submission. NaNs mean that a statistic is undefined for that post. The 19 social features (more info in the paper) are indexed as

ACTIVITY FEATURES:
- 0: Num previous comments
- 1: Num previous posts
- 2: Hours since first interaction (logged)
- 3: Hours since previous interaction (logged)
- 4: Post to all interaction ratio

TYPE FEATURES:
- 5: Average comment length
- 6: Average comment token2type
- 7: Average comment depth
- 8: Proportion of previous threads with multiple interactions
- 9: Proportion of comments with replies
- 10: Median response time (hours) from thread start

QUALITY FEATURES:
- 11-14: k=5,10,50,100 rate for post score
- 15-18: k=5,10,50,100 rate for comment score

### Image features

Image features are distributed as raw text in image_features.zip. Each
dataset has its own text file. Each line of the text file represents a
different image, and values are seperated by tabs. The first column is
the reddit id of an image, and the next 2048 columns are the final
layer ResNet50 features extracted from the image associated with that
reddit id. It's possible to match images to pairing information using
the reddit id, which is stored in the 'id' field of the pairing data.

#### What if I need the raw jpegs?

While we've decided to not distribute the raw jpegs, there is a
download script for re-downloading the images from imgur included in
this release. To download all of the pics from /r/aww, unzip
pairs.zip, and from within the directory, run:

```
python download_urls.py aww
```

This script pulls images directly from imgur with a built-in rate
limit. Please, do not decrease the rate limit of 1 request per second.

Also, once this script finishes, included is a bash script that tests
for corrupted and duplicate images (i.e., images that have been
deleted from imgur).  While there are no duplicates in the original
dataset, imgur will sometimes return a generic "image not found" jpeg
if a file is deleted, which is why the duplicate checking script
exists. Calling

```
./get_corrupt aww
```

will output two files -- one indicates what jpegs are corrupted, and
one that indicates what jpegs are duplicates (the "image not found"
jpegs).