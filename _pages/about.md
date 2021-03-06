---
permalink: /
title: "academicpages is a ready-to-fork GitHub Pages template for academic personal websites"
excerpt: "About me"
author_profile: true
redirect_from: 
  - /about/
  - /about.html
---

What is out-of-distribution generalization?
======
Let us begin with a motivating example. Imagine that you are a farmer living in a remote village. For the whole life, you have been farming sheep on the grassland owned by your family. To you, sheep and grasslands are two inseparable notions. You would immediately think of the other when trying to picture either of the two. One day, you received a postcard from your friend traveling around the world. In the picture on the postcard, there is a strange creature standing on a vast land of sands. It had taken you some time before the two nouns, camel and desert, that you once read in a book suddenly occurred to you. Like sheep and grasslands, they are also two inseparable notions from your limited view. Under this impression, whenever you are given a picture and asked to tell whether it is a sheep or a camel, you could immediately tell by judging from the background of the picture. In usual cases, this simple solution works almost perfectly, however, it would also fail unexpectedly when something unusual happens, e.g., sheep in desert and camels on grassland. In this respect, learning machines are like human and are also prone to make similar mistakes when the test data are not or rarely sampled from the training data distribution.

Generalizing outside of the training distribution is an open challenge for current machine learning systems. As its name suggests, out-of-distribution generalization aims to overcome such challenge, where a model must generalize to new distributions at test time without seeing any training data from them. <!-- Quoted from "Out-of-Distribution Generalization via Risk Extrapolation" -->
Because of the generality of this notion, the idea behind out-of-distribution generalization is not entirely new. Over the years, it has taken on various forms in multiple branches of machine learning research. To name a few, we have domain generalization, stable learning, adversarial robustness, and zero-shot learning.
Recently, it has gain an increasing amount of attention, primarily due to significant performance drops observed in state-of-the-art deep learning models when evaluated on non-i.i.d. test sets.
While neural networks often exhibit super-human generalization performance on the training distribution, they can be extremely sensitive to minute changes in distribution that are often insusceptible to human. <!-- Quoted from "Out-of-Distribution Generalization via Risk Extrapolation" -->
From this perspective, out-of-distribution generalization seeks to alleviate the impact caused by the changes in distribution and thus improve the general robustness of learning machines.

In a broader sense, we are also concerned with the particular assumptions that have to be made for out-of-distribution generalization to be theoretically possible.
One of the most common assumptions requires a fixed underlying task, and access to labeled data from multiple training environments. Moreover, the variation in these environments is assumed to be somewhat representative of the variations we will see at test time. <!-- Quoted from "Out-of-Distribution Generalization via Risk Extrapolation" -->
To put it differently, this assumption guarantees the existence of some statistical invariances which can be exploited by a model to obtain equally good performance across all environments. Hence, we must carefully restrict the type and magnitude of the distribution shift exhibited in our data if we want to study out-of-distribution generalization effectively. Following this insight, we propose a general definition to characterize the distribution shift constructed by existing out-of-distribution datasets.


Characterizing distribution shift
======
On a high level, our characterization consists of two components, each quantifies a typical kind of distribution shift between the training and test environments of any given dataset. These two kinds of distribution shift, namely _correlation shift_ and _diversity shift_, separate datasets by their own characteristics on a two-dimensional plane (as shown in Fig.??).
Informally, correlation shift exists when the statistical correlation between features and labels is different across the environments. On the other hand, diversity shift often exists when data exhibits great variation in features across the environments. With this characterization, we hope to shed some light on the following important questions:
1. With an increasing number of out-of-distribution benchmarks, what are the innate characteristics of them?
2. Can we categorize the out-of-distribution benchmarks in a principled way?
3. How do distribution shifts in data distributions affect the performance of out-of-distribution generalization algorithms?

Now to make things more formal, we start by describing the following causal graph (Causal Bayesian Network):

\[Causal graph here\]

The graph depicts the causal associations among four random variables which can be interpreted as follows:
1. <i>Z</i><sub>1</sub> and <i>Z</i><sub>2</sub> are the latent variables generating the input variable <i>X</i>.
2. The class label variable <i>Y</i> is solely determined by <i>Z</i><sub>1</sub>.
3. <i>Z</i><sub>1</sub> and <i>Z</i><sub>2</sub> are independent (when <i>X</i> is not conditioned on).

For image recognition tasks, <i>X</i> can be seen as images, <i>Y</i> can be seen as labels, <i>Z</i><sub>1</sub> can be seen as features for determining <i>Y</i> such as object structures, and <i>Z</i><sub>2</sub> can be seen as other features such as image backgrounds and lighting conditions. Denote by _**X**_, _**Y**_, <i><b>Z</b></i><sub>1</sub> and <i><b>Z</b></i><sub>2</sub> the corresponding sample spaces of these random variables. Now suppose we have a dataset consisting of a training environment and a testing environment, generated by mixed joint probability density functions _**p**_ and _**q**_ respectively. Both _**p**_ and _**q**_ are defined over space <i><b>X</b></i>×<i><b>Y</b></i>×<i><b>Z</b></i><sub>1</sub>×<i><b>Z</b></i><sub>2</sub> and are compatible with the causal graph. 


Then we can capture the existence of statistical invariance by assuming that _**p**_(**y**|**z**) = _**q**_(**y**|**z**) for every outcome **y** of <i>Y</i> and every outcome **z** of <i>Z</i><sub>1</sub>

introducing basic notations, then derive the mathematical definition for correlation shift and diversity shift. Given a dataset _**D**_ consists of a training environment and a test environment, generated by two distributions with mixed joint probability density function _**p**_ and over space _**X×Y×Z**_ where <i><b>Z</b></i>=<i><b>Z</b></i><sub>1</sub>×<i><b>Z</b></i><sub>2</sub>, the causal relation among the respective random variables over the same space are depicted by the following 













This is the front page of a website that is powered by the [academicpages template](https://github.com/academicpages/academicpages.github.io) and hosted on GitHub pages. [GitHub pages](https://pages.github.com) is a free service in which websites are built and hosted from code and data stored in a GitHub repository, automatically updating when a new commit is made to the respository. This template was forked from the [Minimal Mistakes Jekyll Theme](https://mmistakes.github.io/minimal-mistakes/) created by Michael Rose, and then extended to support the kinds of content that academics have: publications, talks, teaching, a portfolio, blog posts, and a dynamically-generated CV. You can fork [this repository](https://github.com/academicpages/academicpages.github.io) right now, modify the configuration and markdown files, add your own PDFs and other content, and have your own site for free, with no ads! An older version of this template powers my own personal website at [stuartgeiger.com](http://stuartgeiger.com), which uses [this Github repository](https://github.com/staeiou/staeiou.github.io).

A data-driven personal website
======
Like many other Jekyll-based GitHub Pages templates, academicpages makes you separate the website's content from its form. The content & metadata of your website are in structured markdown files, while various other files constitute the theme, specifying how to transform that content & metadata into HTML pages. You keep these various markdown (.md), YAML (.yml), HTML, and CSS files in a public GitHub repository. Each time you commit and push an update to the repository, the [GitHub pages](https://pages.github.com/) service creates static HTML pages based on these files, which are hosted on GitHub's servers free of charge.

Many of the features of dynamic content management systems (like Wordpress) can be achieved in this fashion, using a fraction of the computational resources and with far less vulnerability to hacking and DDoSing. You can also modify the theme to your heart's content without touching the content of your site. If you get to a point where you've broken something in Jekyll/HTML/CSS beyond repair, your markdown files describing your talks, publications, etc. are safe. You can rollback the changes or even delete the repository and start over -- just be sure to save the markdown files! Finally, you can also write scripts that process the structured data on the site, such as [this one](https://github.com/academicpages/academicpages.github.io/blob/master/talkmap.ipynb) that analyzes metadata in pages about talks to display [a map of every location you've given a talk](https://academicpages.github.io/talkmap.html).

Getting started
======
1. Register a GitHub account if you don't have one and confirm your e-mail (required!)
1. Fork [this repository](https://github.com/academicpages/academicpages.github.io) by clicking the "fork" button in the top right. 
1. Go to the repository's settings (rightmost item in the tabs that start with "Code", should be below "Unwatch"). Rename the repository "[your GitHub username].github.io", which will also be your website's URL.
1. Set site-wide configuration and create content & metadata (see below -- also see [this set of diffs](http://archive.is/3TPas) showing what files were changed to set up [an example site](https://getorg-testacct.github.io) for a user with the username "getorg-testacct")
1. Upload any files (like PDFs, .zip files, etc.) to the files/ directory. They will appear at https://[your GitHub username].github.io/files/example.pdf.  
1. Check status by going to the repository settings, in the "GitHub pages" section

Site-wide configuration
------
The main configuration file for the site is in the base directory in [_config.yml](https://github.com/academicpages/academicpages.github.io/blob/master/_config.yml), which defines the content in the sidebars and other site-wide features. You will need to replace the default variables with ones about yourself and your site's github repository. The configuration file for the top menu is in [_data/navigation.yml](https://github.com/academicpages/academicpages.github.io/blob/master/_data/navigation.yml). For example, if you don't have a portfolio or blog posts, you can remove those items from that navigation.yml file to remove them from the header. 

Create content & metadata
------
For site content, there is one markdown file for each type of content, which are stored in directories like _publications, _talks, _posts, _teaching, or _pages. For example, each talk is a markdown file in the [_talks directory](https://github.com/academicpages/academicpages.github.io/tree/master/_talks). At the top of each markdown file is structured data in YAML about the talk, which the theme will parse to do lots of cool stuff. The same structured data about a talk is used to generate the list of talks on the [Talks page](https://academicpages.github.io/talks), each [individual page](https://academicpages.github.io/talks/2012-03-01-talk-1) for specific talks, the talks section for the [CV page](https://academicpages.github.io/cv), and the [map of places you've given a talk](https://academicpages.github.io/talkmap.html) (if you run this [python file](https://github.com/academicpages/academicpages.github.io/blob/master/talkmap.py) or [Jupyter notebook](https://github.com/academicpages/academicpages.github.io/blob/master/talkmap.ipynb), which creates the HTML for the map based on the contents of the _talks directory).

**Markdown generator**

I have also created [a set of Jupyter notebooks](https://github.com/academicpages/academicpages.github.io/tree/master/markdown_generator
) that converts a CSV containing structured data about talks or presentations into individual markdown files that will be properly formatted for the academicpages template. The sample CSVs in that directory are the ones I used to create my own personal website at stuartgeiger.com. My usual workflow is that I keep a spreadsheet of my publications and talks, then run the code in these notebooks to generate the markdown files, then commit and push them to the GitHub repository.

How to edit your site's GitHub repository
------
Many people use a git client to create files on their local computer and then push them to GitHub's servers. If you are not familiar with git, you can directly edit these configuration and markdown files directly in the github.com interface. Navigate to a file (like [this one](https://github.com/academicpages/academicpages.github.io/blob/master/_talks/2012-03-01-talk-1.md) and click the pencil icon in the top right of the content preview (to the right of the "Raw | Blame | History" buttons). You can delete a file by clicking the trashcan icon to the right of the pencil icon. You can also create new files or upload files by navigating to a directory and clicking the "Create new file" or "Upload files" buttons. 

Example: editing a markdown file for a talk
![Editing a markdown file for a talk](/images/editing-talk.png)

For more info
------
More info about configuring academicpages can be found in [the guide](https://academicpages.github.io/markdown/). The [guides for the Minimal Mistakes theme](https://mmistakes.github.io/minimal-mistakes/docs/configuration/) (which this theme was forked from) might also be helpful.
