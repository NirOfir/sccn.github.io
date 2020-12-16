---
layout: default
title: c. Resampling
categories: preproc
parent: 5. Preprocess data
grand_parent: Tutorials
---
Changing the data sampling rate
---------------------------------

### Load the sample EEGLAB dataset

Select menu item <span style="color: brown">File</span> and press sub-menu item
<span style="color: brown">Load existing dataset</span>. Select the tutorial file "eeglab_data.set" which is distributed with
the toolbox, located in the "sample_data" folder of EEGLAB. Then press *Open*.

![Image:Pop_loadset.png]({{ site.baseurl }}/assets/images/Pop_loadset.png)

### Change the sampling rate

The most common use for <font color=brown>Tools → Change sampling
rate</font> is to reduce the sampling rate to save memory and disk
storage. A [pop_resample.m](http://sccn.ucsd.edu/eeglab/locatefile.php?file=pop_resample.m) window pops up, asking for the new
sampling rate. The function uses Matlab *resample()* (in the Signal
Processing toolbox-- if you do not have this toolbox, it will use the
slow Matlab function *griddata*).

![Image:pop_resample.png]({{ site.baseurl }}/assets/images/pop_resample.png)

For processing the tutorial data, you do need to change the sampling rate, since
it is already at an acceptable sampling rate.