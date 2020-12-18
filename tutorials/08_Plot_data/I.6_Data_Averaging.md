---
layout: default
title: a. Plotting ERPs
parent: 8. Plot data
grand_parent: Tutorials
---

Plotting averaged data
==================

*Note*: Previously, in Makeig et al.,
[2002](http://www.sccn.ucsd.edu/science2002.html) and
[2004](http://www.sccn.ucsd.edu/papers/TICS04.html), we have discussed
ways in which the event-related EEG dynamics occurring in a set of data
epochs time locked to some class of events are not limited to nor
completely expressed in features of their time-locked trial average or
Event-Related Potential (ERP). 

EEGLAB contains several functions for
plotting 1-D ERP averages of dataset trials (ie. epochs). EEGLAB also
features functions for studying the EEG dynamics expressed in the single
trials. This may be visualized, in large part, via 2-D (potential time
series by trials) ERP image transforms of a dataset of single-trial epochs (a.k.a., epoched data).
See the [ERP-image](/tutorials/single-subject/plotting-erp-images) page of this tutorial for more details.



Plotting the ERP data on a single axis with scalp maps
-------------------------------------------------------- 

We use here the tutorial dataset as it was after the last [tutorial section](/tutorials/single-subject/extracting-data-epochs).

### Plotting all-channel ERPs

To plot the average ERP of all dataset epochs, plus ERP scalp maps at
selected latencies, select <span style="color: brown>Plot → Channel ERPs\">With scalp maps.</span> As a simple illustration using the sample
dataset, we retain the default settings in the resulting [pop_timtopo.m](http://sccn.ucsd.edu/eeglab/locatefile.php?file=pop_timtopo.m) window, entering only a plot title and
pressing *OK*.


![Image:Pop_timtopo.png]({{ site.baseurl }}/assets/images/Pop_timtopo.png)


A [timtopo.m](http://sccn.ucsd.edu/eeglab/locatefile.php?file=timtopo.m) figure (below) appears. Each trace plots the
averaged ERP at one channel. The scalp map shows the topographic
distribution of average potential at 430 ms (the latency of maximum
ERP data variance). Alternatively, one or more exact scalp map
latencies may be specified in the pop-window above.


![Image:Erpplot1.png]({{ site.baseurl }}/assets/images/Erpplot1.png)


Function [timtopo.m](http://sccn.ucsd.edu/eeglab/locatefile.php?file=timtopo.m) plots the relative time courses of the
averaged ERP at all channels, plus ‘snapshots’ of the scalp potential
distribution at various moments during the average ERP time course.
Note that to visualize the ERP scalp map at *all* latencies -- as an
ERP movie (i.e., to view the play of the ERP on the scalp), call
function [eegmovie.m](http://sccn.ucsd.edu/eeglab/locatefile.php?file=eegmovie.m) from the command line.


### Plotting ERPs in a Topographic Map

Here we will plot the ERPs of an epoched dataset as single-channel
traces in their 2-D topographic arrangement. 
Select <span style="color: brown>Plot → Channel ERPs \"> In scalp array/rect. array</span>. Using the default settings and pressing *OK* in the
resulting [pop_topoplot.m](http://sccn.ucsd.edu/eeglab/locatefile.php?file=pop_topoplot.m) window (below)


![Image:Pop_plottopo.png]({{ site.baseurl }}/assets/images/Pop_plottopo.png)


produces the following [plottopo.m](http://sccn.ucsd.edu/eeglab/locatefile.php?file=plottopo.m) figure.


![Image:Erpplot2.png]({{ site.baseurl }}/assets/images/Erpplot2.png)


Note that if called from the command line, the [plottopo.m](http://sccn.ucsd.edu/eeglab/locatefile.php?file=plottopo.m)
function *geom* option can also be used to plot channel waveforms in a
rectangular grid. You may visualize a specific channel time course by
clicking on its trace (above), producing a pop-up sub-axis view. For
example, click on the ERP trace marked *POz* (above) to call up a
full-sized view of this trace (as below).


![Image:Zoom1.png]({{ site.baseurl }}/assets/images/Zoom1.png)


Many EEGLAB plotting routines use the toolbox function {
{File\|axcopy.m} } to pop up a sub-axis plotting window whenever the
users clicks on the main plot window. Sub-axis windows, in turn, do
not have [axcopy.m](http://sccn.ucsd.edu/eeglab/locatefile.php?file=axcopy.m) enabled, allowing the user to use the
standard Matlab mouse 'Zoom In/Out' feature.


### Plotting ERPs in a Column Array


To plot (one or more) average ERP data traces in two column array,
select menu item <span style="color: brown> Plot → Channel ERPs \"> In scalp/rect. array</span>. To use the default settings in the resulting
[pop_topoplot.m](http://sccn.ucsd.edu/eeglab/locatefile.php?file=pop_topoplot.m) window, check the "Plot in rect. array"
checkbox and press *OK*.


![Image:Pop_topoplotrectarray.png]({{ site.baseurl }}/assets/images/Pop_topoplotrectarray.png)


The resulting [pop_topoplot.m](http://sccn.ucsd.edu/eeglab/locatefile.php?file=pop_topoplot.m) figure (below) appears.


![Image:Erpplot3.png]({{ site.baseurl }}/assets/images/Erpplot3.png)


As in the previous plot, clicking on a trace above pops up a full
window sub-axis view.

Plotting a series of 2-D ERP scalp maps
----------------------------------------
Here we will plot ERP data for a series of 2-D scalp maps representing
potential distributions at a selected series of trial latencies.


Select <span style="color: brown"> Plot → ERP map series → In 2-D</span>. In
the top text box of the resulting [pop_topoplot.m](http://sccn.ucsd.edu/eeglab/locatefile.php?file=pop_topoplot.m) window
(below), type the epoch latencies of the desired ERP scalp maps.

Note that in this or any other numeric text entry box, you may enter
any numeric Matlab expression. 

For example, instead of *0 100 200 300
400 500*, try *0:100:500*. Even more complicated expressions, for
example *-6000+3\*(0:20:120)*, are interpreted correctly.


![Image:641pop_topoplot.png]({{ site.baseurl }}/assets/images/641pop_topoplot.png)


The [topoplot.m](http://sccn.ucsd.edu/eeglab/locatefile.php?file=topoplot.m) window (below) then appears, containing ERP
scalp maps at the specified latencies. Here, the plot grid has 3
columns and 2 rows; other plot geometries can be specified in the gui
window above via the '' Plot geometry'' text box.


![Image:2dscalpmap.png]({{ site.baseurl }}/assets/images/2dscalpmap.png)


Plotting a series of 3-D ERP scalp maps
----------------------------------------

To plot ERP data as a series of 3-D scalp maps, go to the menu
<span style="color: brown">Plot → ERP map series → In 3-D</span> The query
window (below) will pop up, asking you to create and save a new 3-D
head map *3-D spline file*. This process must be done only once for
every montage (and proceeds much more quickly in EEGLAB v4.6-). Click
*OK* to begin this process.


![Image:3dscalpmessage.png]({{ site.baseurl }}/assets/images/3Dscalpmessage.png)


The window below will pop up. 
Here, you have two choices: 
- If you have
already generated a spline file for this channel location structure,
you may enter it here in the first edit box (first click on the *Use
existing spline file or structure* to activate the edit box, then
browse for a datafile. 

- If you have not made such a file, you will need
generate one.

However, first your channel locations must be co-registered with the
3-D head template to be plotted. 

Note that if you are using one of the
template channel location files, for example, the (v4.6+) tutorial
dataset, the *Talairach transformation matrix* field (containing
channel alignment information) will be filled automatically. 

Enter an
output file name (in the second edit box), trial latencies to be
plotted (0:100:500 below indicating latencies 0, 100, 200, 300, 400,
and 500 ms) and press *OK*.


![575px]({{ site.baseurl }}/assets/images/Pop_headplot3.png)


Now, the 3-D plotting function [pop_headplot.m](http://sccn.ucsd.edu/eeglab/locatefile.php?file=pop_headplot.m), will create
the 3-D channel locations spline file. A progress bar will pop up to
indicate when this process will be finished. When the 3-D spline file
has been generated, select <font color=brown>Plot → ERP map series \>
In 3-D</font>. Now that a spline file has been selected, another gui
window will appear. As for plotting 2-D scalp maps, in the first edit
box type the desired latencies, and press *OK*. The {
{File\|headplot.m} } figure (below) will appear.


![525px]({{ site.baseurl }}/assets/images/642headplot.jpg)


As usual, clicking on a head plot will make it pop up in a sub-axis
window in which it can be rotated using the mouse. Note that to select
(for other purposes) a head plot or other object in a figure that has
the [axcopy.m](http://sccn.ucsd.edu/eeglab/locatefile.php?file=axcopy.m) pop-up feature activated, click on it then
delete the resulting pop-up window.

To plot the heads at a specified angle, select the <span style="color: brown"> Plot → ERP map series → In 3-D</span> menu item. Note that now by
default the function uses the 3-D spline file you have generated
above. Enter latencies to be displayed and the [headplot.m](http://sccn.ucsd.edu/eeglab/locatefile.php?file=headplot.m)
'view' option (as in the example below), and press *OK*.


![575px]({{ site.baseurl }}/assets/images/Pop_headplot2.png)


The [headplot.m](http://sccn.ucsd.edu/eeglab/locatefile.php?file=headplot.m) window (below) will then appear. You may
also rotate the individual heads using the mouse. This is often
necessary to show the illustrated spatial distribution to best effect.


![400px]({{ site.baseurl }}/assets/images/642headplot_view.jpg)

### Co-registration with actual channel locations

We will now briefly describe the channels-to-head model
co-registration process. If your dataset contains specific channel
locations, for example locations that you may have measured on the
subject head using a Polhemus system, and you want to use these
electrode locations for 3-D plotting, [headplot.m](http://sccn.ucsd.edu/eeglab/locatefile.php?file=headplot.m) must
first determine the positions of your electrode locations relative to
a template head surface. A generic transformation cannot be performed
because the origin (\[0 0 0\]) in your electrode location system does
not necessarily correspond to the center of the template head (.e.g.,
the intersection of the fiducial points: nasion and pre-auricular
points) used by [headplot.m](http://sccn.ucsd.edu/eeglab/locatefile.php?file=headplot.m). Even if this were the case,
heads have different shapes, so your scanned electrode locations might
need to be scaled or warped in 3-D to match the template head mesh.

The co-registration window begins this operation. Call back the {
{File\|headplot.m} }. gui window using menu item <font color=brown>
Plot → ERP map series \> In 3-D</font>. Set the checkbox labeled *Or
recompute a new spline file named:*, and then click the *Manual
coreg.* push button. A window appears explaining how to perform the
co-registration.


![550px]({{ site.baseurl }}/assets/images/Coregister.gif)


Pressing *OK* will cause the co-registration window below to open.


![475px]({{ site.baseurl }}/assets/images/Coregister2.gif)


In the window above, the red electrodes are those natively associated
with the template head mesh. Rather than directly aligning your
electrode locations (shown in green) to the head mesh, your montage
will be aligned to template electrode locations associated with the
head mesh by scanning on the same subject's head (here shown in red).
For the sample dataset, this alignment has already been performed.
(Click the *Labels on* push button to display the electrode labels).

When you have finished the co-registration, simply click *OK* and a
vector of 9 new channel alignment values (shift, in 3-D; rotation, in
3-D; scaling, in 3-D) will be copied back to the interactive {
{File\|headplot.m} } window. For more information about channel
co-registration, see the [DIPFIT tutorial](/A08:_DIPFIT "wikilink").

Note that it is possible, and relatively easy, to generate custom {
{File\|headplot.m} } head meshes. Let us know by email if you are
interested in learning how to do this.

Computing Grand Mean ERPs
---------------------------

Normally, ERP researchers report results on grand mean ERPs averaged
across subjects. As an example, we will use EEGLAB functions to compute
the ERP grand average of the two condition ERPs above.


Select <span style="color: brown>Plot → Sum/Compare ERPs</span>. In the top text-entry boxes of the resulting [pop_comperp.m](http://sccn.ucsd.edu/eeglab/locatefile.php?file=pop_comperp.m) window (below), enter the indices of datasets ‘3’ and ‘4’. On the first row, click the *avg.* box to display grand average, the *std.* box to display standard deviation, and the *all ERPs* box to display ERP averages for each dataset. Finally *0.05* for the t-test significance probability (p) threshold. Then press *OK*.

![575px](/assets/images/I72pop_comperp().gif)


The plot below appears.


![450px](/assets/images/Pop_comperp3.gif)


Now, click on the traces at electrode position *FPz*, calling up the image below. You may remove the legend by deselecting it under the <span style="color: brown>Insert \"> Legend</span> menu.


![450px](/assets/images/Pop_comperp4.gif)

*Note*: If you prefer to use positive up view for the y-axis scale, type
*ydir', 1* in the *Plottopo options* field. This can be set as a global
or project default in *icadefs.m*. See the [Options tutorial](/A3:_Maximizing_Memory "wikilink").

The ERPs for datasets 3 and 4 are shown in blue and red. 

The grand
average ERP for the two conditions is shown in bold black, and the
standard deviation of the two ERPs in dotted black.
 
Regions
significantly different from 0 are highlighted based on a two-tailed
t-test at each time point. 

This test compares the current ERP value
distribution with a distribution having the same variance and a 0 mean.

Note that this t-test has not been corrected for multiple comparisons.
The p values at each time point can be obtained from a command line call
to the function [pop_comperp.m](http://sccn.ucsd.edu/eeglab/locatefile.php?file=pop_comperp.m).