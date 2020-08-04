This is version 1.0 of the multimodal wikipedia dataset to accompany

@inproceedings{hessel2018concreteness,
  title={Quantifying the visual concreteness of words and topics in multimodal datasets},
  author={Hessel, Jack and Mimno, David and Lee, Lillian},
  booktitle={NAACL},
  year={2018}
}

If you encounter any bugs or have feedback, please contact:

jhessel@cs.cornell.edu

This data was derived from the digital books collection released by
the british library. All data was released to the public domain (CC0
1.0); the details of the liscense can be found here:

https://creativecommons.org/publicdomain/mark/1.0/

The original download links can be found here:

The dataset's homepage is: https://data.bl.uk/digbks/
The text of the books is from: https://data.bl.uk/digbks/db14.html
The "plates" images are from: https://data.bl.uk/digbks/db19.html
The "medium" images are from: https://data.bl.uk/digbks/db18.html

@misc{British_Library_Labs_2016,
  title={Digitised Books},
  publisher={British Library}
  author={British Library Labs},
  howpublished={\url{https://data.bl.uk/digbks/}},
  year={2016}
}

If you use this dataset, please consider citing the digibooks dataset,
and/or the above NAACL paper describing the preprocessing.

The dataset included here consists of 404765 images coupled with the
OCR text in the +/- 3 pages surrounding them, i.e., if an image
appeared on page 17, all OCR text from page 14, 15, 16, 17, 18, 19,
and 20 would be included.

The following files are included:

- bl_image_release.zip: a zipfile containing 404765 jpg files. Many of
  these images have been resized so that the largest axis is no more
  than 600 pixels (the original aspect ratios are preserved)

- bl_images.tsv.bz2: a tsv file with 404765 lines where each line
  corresponds to an image with zero indexing, i.e., the information on
  line 10 corresponds to 9.jpg; 16391 volumes are represented, in total:
  - the first column is the title of the book in which an image
    appeared (used for the book-level holdout described in the NAACL
    paper)
  - the second column is the original path of the image in the british
    library data release, and, among other things, indicates the year
    of the image, and whether it was a "plate" or a "medium" image.

- bl_text.txt.bz2: a text file with 404765 lines containing the OCR text
  of the british library data. Like image_books.tsv, each line
  corresponds to an image with zero indexing, i.e., the information on
  line 10 corresponds to 9.jpg.
