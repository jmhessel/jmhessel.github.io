This is version 1.0 of the multimodal wikipedia dataset to accompany 

@inproceedings{hessel2018concreteness,
  title={Quantifying the visual concreteness of words and topics in multimodal datasets},
  author={Hessel, Jack and Mimno, David and Lee, Lillian},
  booktitle={NAACL},
  year={2018}
}

If you encounter any bugs or have feedback, please contact:

jhessel@cs.cornell.edu

In total, there are 354202 Wikipedia articles and 549312 images
contained within them included in this set. The data is extracted from
an early March 2016 data dump. We followed Benjamin Wilson's
popularity filtering technique
(https://blog.lateral.io/2015/06/the-unknown-perils-of-mining-wikipedia/)
and only considered articles with at least 50 views on March 5th,
2016. In accordance with the terms/conditions of distributing textual
content form wikipedia
(https://en.wikipedia.org/wiki/Wikipedia:Copyrights#Re-use_of_text),
links to all articles are included in a file. The raw image files are
not included, because redistribution of images varies between images
according to their licensing. We include image features extracted from
the final layer of ResNet50, in addition to the URLs where the images
can be found and downloaded, if the raw pixel information is required.

The files are as follows:

- wiki_text.txt: the text of all the wikipedia articles we
  consider. The first tab-separated token of each line indicates the
  wikipedia id of the corresponding article.

- wiki_urls.txt: an ordered text file containing the url of each
  included article.

- images.txt:
  - the first column is a comma-separated list of wiki article ids that contain the image.
  - the second column is the name of the image file on the wikipedia commons.

- image_urls.txt: the urls of the wikipedia commons images used in
  this study. This file might be useful if you want to re-scrape the
  images for your own use, though please use a respectful rate limit
  if you choose to do so.

- resnet50_wiki_features.tsv: a tsv file containing the 2048 extracted
  image features from the pre-softmax layer of ResNet50. The ordering
  of features in this file corresponds to the image.txt file, i.e.,
  the 10th line of the images.txt file represents the image that
  corresponds to the features listed on the 10th line of
  resnet50_wiki_features.tsv.
