---
layout: default
title: IV.11 BESA (outdated)
parent: IV. Appendix
grand_parent: Tutorials
nav_order: 11
---

{ {Backward_Forward\|A10:_MI-clust\|A10:
MI-clust\|A12:_Quick_Tutorial_on_Rejection\|A12: Quick Tutorial on
Rejection} }

Equivalent dipole source localization of independent components using BESA
--------------------------------------------------------------------------

#### Component localization by equivalent dipoles: A simple example

Equivalent dipole source localization by BESA (MEGIS Software GmbH,
Munich) can be applied to independent component maps under EEGLAB. The
following window shows five independent component scalp maps from five
different subjects. Each of these components was labelled by the
experimenters as representing a left-occipital alpha rhythm generator.


![Image:Besaexample2.jpg](/assets/images/Besaexample2.jpg)



BESA dipole localization applied to these component maps, accounted for
each map with a single equivalent dipole in a three-shell spherical
model with low residual variance (R.V.) Note that unlike in many BESA
analyses, we rarely need to ignore signals at some scalp electrodes
since ICA typically isolates artifactual signals into separate
independent components, and independent components likely account mainly
for activity with a connected synchronous cortical domain whose scalp
projection should match that of a single equivalent dipole. (Note: This
does not mean, however, that some independent components may be
generated by tightly linked bilateral activity in domains joined through
e.g. corpus callosum. In this case, the source may often be well modeled
by two symmetrically placed equivalent dipoles).


![Image:Besaexample1.jpg](/assets/images/Besaexample1.jpg)


#### How to localize components using BESA

BESA is a commercial software ([www.besa.de](http://www.besa.de))
developed by Michael Scherg and colleagues for localizing brain source
equivalent dipoles using a three-shell spherical model.
We have developed Matlab functions to automatically export/import and
display BESA dipole information. To localize components, you must run
BESA 2.x, 3.x, 99 or BESA 2000 Since BESA 99 and 2000 do not support
macro files, if you use these versions you must also download BESA 3.0
(the previous version running macros) from the BESA web site (see below)
.

<u>BESA 3.0 installation for BESA 2000 and BESA 99 users</u>

> 1 - Download [BESA30 DOS-Window Upgrade from
> 2.x](ftp://ftp.besa.de/updates/besa_version_3.0/besa30-dos-windows_upgrade_from_2x.exe)
> from the BESA web site (*even if you don't have BESA 2.x*)
>
> 2 - Install the hardlock driver for BESA 2000 (on the BESA 2000 CD.
> Note: you must usually go through the whole installation of BESA 2000
> to install the hardlock driver).
>
> 3 - Download the [BESA30 for
> BESA2000-Hardlock](ftp://ftp.besa.de/updates/besa_version_3.0/besa30_for_besa2000-hardlock.exe)
> file and *place it in the BESA 3.0 directory* (if you only have a BESA
> 99 license, you should download [BESA30 for
> BESA99-EEG-Hardlock](ftp://ftp.besa.de/updates/besa_version_3.0/besa30_for_besa99-eeg-hardlock.exe)
> or [BESA30 for
> BESA99-MEG+EEG-Hardlock](ftp://ftp.besa.de/updates/besa_version_3.0/besa30_for_besa99-meg+eeg-hardlock.exe)).
>
> 4 - Click on the file downloaded in (3) to start BESA3.0
>
> 5 - The BESA3.0 manual is not provided on the Internet. We use the
> [BESA 2.2
> Manual](ftp://ftp.besa.de/updates/besa_version_3.0/besa22_manuals.exe)
> and find that most of the commands also work in version 3.0.

<u>Install EEGLAB plugin</u>

> Then download the BESA plugin for EEGLAB (go to the [plugin
> page](http://sccn.ucsd.edu/eeglab/plugins.html), download the BESA
> plugin, and uncompress it in the EEGLAB plugin folder). EEGLAB BESA
> functions can also be used with BESA 2.x. However, BESA 2.x cannot
> import more than 66 channels, and has some restrictions about path
> lengths under Windows, we strongly recommend the use of BESA 3.0.

#### Exporting component information

You must first restart EEGLAB with the BESA-function menu included by
typing:

> \>\> eeglab besa

Note that this call will not erase your current dataset(s), but will
simply add a new item to the 'Tools' menu: <font color=brown">Tools \>
Localize dipoles using BESA</font>.

After ICA components have been computed, select menu item
<font color=brown>Tools \> Localize dipoles using BESA \> Export
components to BESA</font>. This calls the function
[besaexport()](http://sccn.ucsd.edu/eeglab/allfunctions/besaexport.html).
The following window will appear:


![Image:Besaexport.gif](/assets/images/Besaexport.gif)



In the first edit box, enter the indices of the components to be
localized using BESA. The other edit boxes are self explanatory. In case
you choose to export the electrode locations from EEGLAB (by leaving
blank the 4th edit box), it is very important to check that the polar
coordinates have not been shrunk by any other program (e.g., the Fz
radius value should be 0.25). If you imported a file with 3-D
coordinates into EEGLAB, that should not be an issue. Note that under
Windows the last edit box will not appear. After pressing *OK*, the
following text will be displayed on the command line:

``` matlab
Accessing directory...
Exporting electrode locations …
Exporting component maps...
Exporting parameter file...
Writing macro file...
NOW RUN BESA, PRESS "A" (for automatic processing) and enter filename "E:\besatmp\macro"
```

Now, run BESA on your Windows machine. In BESA, type *A* and then enter
the filename given above (*E:\\besatmp\\macro*). Dipole localization
will be performed automatically. Since the number of characters in each
BESA macro file is limited, the EEGLAB Matlab function generates many
macro files that are called by parent macro files. In this way, up to
900 components can be localized at a time. Also note that minimizing the
BESA window will greatly speed up the computation. Occasionally BESA
will not optimize the dipole location (e.g., when residual variance
remains 98% or more). If this happens, simply rerun the macro
corresponding to the badly localized component (for instance
**macro10.aut** for component 10).

#### Importing BESA component locations

Select menu item<font color=brown>Tools \> Localize dipoles using BESA\>
Import dipoles from BESA</font>(calling the function
[besaimport()](http://sccn.ucsd.edu/eeglab/allfunctions/besaimport.html)).
The following interactive window will pop up.


![Image:Besaimport.gif](/assets/images/Besaimport.gif)



In the upper edit box, you must provide the location of the directory in
which the dipole information has been saved by BESA. In the lower edit
box, you can either (1) import dipoles and erase all previous
information (*no* option), (2) append the newly computed information
(*yes* option), or (3) only import dipoles for components that do not
have yet associated dipoles (*componly* option). Press *OK* and the
function will return information about the components that have been
imported:

``` matlab
Reading component 1 (1 dipoles) residual variance 2.09 %
Reading component 2 (1 dipoles) residual variance 15.67 %
Reading component 3 (1 dipoles) residual variance 1.94 %
Reading component 4 (1 dipoles) residual variance 1.23 %
Reading component 5 (1 dipoles) residual variance 3.49 %
Reading component 6 (1 dipoles) residual variance 12.88 %
```

Note: We usually only trust dipole locations with low residual variance
(e.g., below 5%, though this figure may vary with number of channels,
montage, etc.).

Visualizing dipole locations
----------------------------

There are four menu items that visualize equivalent dipole locations.
They all call the same function
[dipplot()](http://sccn.ucsd.edu/eeglab/allfunctions/dipplot.html) with
different options. Here, we illustrate two of these four menu items:
First, <font color=brown>Tools \> Localize dipoles using BESA \> Plot
dipoles on BESA head</font>.


![Image:Besaplot1.gif](/assets/images/Besaplot1.gif)



Here, the dipoles are plotted in 3-D (Note: Use the buttons on the
bottom-left to select a specific view). Note that the background images
were captured from BESA and the scaling was adjusted manually using
visual fitting of a sphere mesh and of the BESA images (press the *Mesh
on* button (lower left) to display the mesh sphere). Note that the
barlength of the dipole varies with the absolute component amplitude.

We also fit the head sphere model to an average-brain MRI average images
(available for download from the
[ICBM](http://www.bic.mni.mcgill.ca/cgi/icbm_view/) project). MRI images
were first shrunk along the X or Y axis to match the 3-D sphere mesh. We
then changed the aspect ratio of the axis so that the MRI images'
original aspect ratio was preserved (and the sphere mesh became an
ellipsoid). A dipole location summary, plotted on the top of the MRI
image, can be shown using menu item <font color=brown>Tools \> Localize
dipoles using BESA \> Plot dipoles on BESA head.</font>


![Image:Besaplot2.gif](/assets/images/Besaplot2.gif)



Finally, by calling the plotting function from the command line


> \>\> dipplot(EEG.sources);


many more options can be specified and one or more equivalent dipoles
can be plotted individually for each component.

#### Miscellaneous

*Using other dipole localization software:* You may use the
[besaexport()](http://sccn.ucsd.edu/eeglab/allfunctions/besaexport.html)
function to export the electrode localization file and the component
activations, then try to localize dipoles using some other localization
software. If you succeed in doing this, or if you write dedicated
functions for this, please [contact us](mailto:eeglab@sccn.ucsd.edu).
*Localizing dipoles from ERP averages or continuous EEG:* Because of the
theoretical and practical advantages of using ICA for source
localization, we have only implemented equivalent dipole localization
for independent components. However, localizing ERP or EEG time series
would simply involve exporting the data to BESA. For instance, to export
an ERP raw data file that BESA can read, type in:

> \>\> ERP = mean(EEG.data,3);
> \>\> save -ascii ERP.raw ERP

You may also use the electrode location file generated by
[besaexport()](http://sccn.ucsd.edu/eeglab/allfunctions/besaexport.html).

[Category:IV. Appendix](/Category:IV._Appendix "wikilink") {
{Backward_Forward\|A10:_MI-clust\|A10:
MI-clust\|A12:_Quick_Tutorial_on_Rejection\|A12: Quick Tutorial on
Rejection} }