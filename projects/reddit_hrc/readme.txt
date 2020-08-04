Dataset to accompany "Science, AskScience, and BadScience: On the
Coexistence of Highly Related Communities" (ICWSM 2016).

If you use this dataset in your research, please give credit to Jason
Baumgartner of pushshift.io for his scraping work.

If you use the reconstructed discussion trees provided here, please
cite the following article:

@inproceedings{hessel2016science,
  title={Science, AskScience, and BadScience: On the Coexistence of Highly Related Communities},
  author={Hessel, Jack and Tan, Chenhao and Lee, Lillian},
  journal={The 10th International AAAI Conference on Web and Social Media},
  year={2016}
}

Update, April 2018: Version 1.0 -> 1.1

- A small amount of data was missing from this dataset. While we were
  aware of this fact when we published V1.0 (see the "stats" files
  below) recently the negligibility of this missing information has
  been called into question. More information is available here:

  http://devingaffney.com/caveat-emptor-computational-social-science-large-scale-missing-data-in-a-widely-published-reddit-corpus/

  To correct this, we re-scraped all post/comment gaps in March 2018
  (we scraped each possible missing ID 3 times to ensure that missing
  posts/comments were not missing due to intermittent API errors;
  compared to version 1.1, there are an additional 1.3M posts (missing
  rate of 1.1%) and 2.6M comments until 2015 (missing rate of .125%).

  We re-ran key experiments from this paper with the missing data
  incorporated (in particular -- re-doing the pairing experiments
  giving rise to Figures 6 and 7) and the results are robust. See
  http://www.cs.cornell.edu/~jhessel/reddit/gaps.html for more detail.

- Removed "score" from the meta files; it is not needed for any of the
  results in the paper, and its semantics have changed on reddit
  itself.

- Added *-dangling files, which describe the number of dangling
  references per community.

~~~

Files: (10GB)

ICWSM2016.tar.bz2 contains two files for each of ~5.7K subreddits. The
subreddits selected follow the filtration process detailed in "What do
Vegans do in their Spare Time? Latent Interest Detection in
Multi-Community Networks" (Hessel et al. 2015; NIPS networks
workshop). Specifically, communities are only included in this dataset
if at least 300 unique users have submitted text or link posts to that
subreddit.

- X.jsonlist-meta: one line per post/comment. Data on the line is of
  the form

  (spaces) username utc_timestamp post_id

  The number of leading spaces on a line indicates the depth of the
  post/comment. Normal reddit submissions have zero leading spaces,
  first level comments have one leading space, etc. Consider the
  following example:

SalamiJack 1333520401 t3_rsiqs
 alyvian 1333559101 t1_c48fmft
  sirhotalot 1333573483 t1_c48ixz5
 nonesaid 1333562944 t1_c48gie3

 In this case, /u/SalamiJack started a thread, to which /u/alyvian and
 /u/nonesaid replied directly. /u/sirhotalot replied to /u/alyvian's
 reply. A small number of reddit users may have a space in their name, so
 please keep this in mind when parsing these files.

- X.jsonlist-stats: a python prettytable formatted summary of
  estimates of extents of scraping errors. The posts and comments are
  from different data sources (posts are from Tan and Lee (WWW, 2015)
  comments are from Jason Baumgartner's reddit post (see below)). The
  posts dataset has a "num_comments" field that provides a noisy
  estimate of how many comments should be collected from the comments
  dataset. These are the number of "comments expected." The rest of
  this file contains statistics regarding the extent to which the
  number of comments we expect exceed the number of comments actually
  present. Most subreddits have negligible missing data.

- X.jsonlist-dangling: We count the number of "dangling references"
  per community. A dangling reference is discovered as follows: each
  comment has a pointer to the ID of its parent (which can be a post
  or a comment). If a comment's parent cannot be found, this means we
  are sure that it at one point existed, but cannot be recovered. Each
  *-dangling file contains two values -- the number of dangling
  comments due to missing posts, and then, the number of dangling
  comments due to missing comments. If a comment is dangling, it and
  (and all of its children) are discarded. A vast majority of
  subreddits we consider have zero dangling references.


History:

This dataset includes meta information from roughly 1 billion posts +
comments from the website www.reddit.com, dating back to reddit's
inception in 2006 to Nov. 2014. It was constructed using data provided
by Jason Baumgartner (pushshift.io) who has done an excellent job
scraping reddit. You can read more about the comments dataset here
(Baumgartner's reddit username is /u/Stuck_In_The_Matrix)

https://www.reddit.com/r/datasets/comments/3bxlg7/i_have_every_publicly_available_reddit_comment/

The data contributions of the authors are the reconstructions of the
entire discussion trees. While Baumgartner's dataset includes a list
of all comments, significant processing was required to reconstruct
entire discussion trees. In its raw form, each comment simply contains
a pointer to its parent.

The list of posts to reconstruct discussions for was taken from "All
Who Wander: On the Prevalence and Characteristics of Multi-community
Engagement" (WWW 2015). This version of the dataset has no
comments. However, please consider citing the following article
instead if you use only the post information from this dataset.

@inproceedings{tan+lee:15, 
     author = {Chenhao Tan and Lillian Lee}, 
     title = {All Who Wander: On the Prevalence and Characteristics of Multi-community Engagement}, 
     year = {2015}, 
     booktitle = {Proceedings of WWW} 
}

More information about Tan and Lee 2015 can be found here:

https://chenhaot.com/pages/multi-community.html

In 2018, Gaffney and Matias pointed out that there was potentially a
small amount of data missing from the set. In 2018, we re-scraped post
and comment gaps in accordance with the sequential reddit ID analysis
of Gaffney and Matias (https://arxiv.org/pdf/1803.05046.pdf). The
meaning of the score of posts changed on reddit since the initial
scraping period (http://redd.it/5gvd6b) and, as a result, we have
omitted scoring information from the version 1.1 release.

Additional Information:

This dataset contains only the meta-data for posts and
comments. However, the full text of each comment is also
available. The entire dataset is around 120GB compressed, and this
study uses none of the comment text.

If you're interested in gaining access to the whole dataset, contact
jhessel@cs.cornell.edu.
