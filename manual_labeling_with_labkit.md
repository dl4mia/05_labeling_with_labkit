# DL4MIA 2023: 05a - Manual image labeling with Labkit

**[Return to the Welcome page](https://tinyurl.com/33y2b2hk)**

Paper: [https://www.frontiersin.org/articles/10.3389/fcomp.2022.777728/full](https://www.frontiersin.org/articles/10.3389/fcomp.2022.777728/full)

Extensive documentation and tutorials provided here: [https://imagej.net/plugins/labkit/](https://imagej.net/plugins/labkit/).

I2K talk with a quick demo: [https://youtu.be/UZjZtmm7adU](https://youtu.be/UZjZtmm7adU)

## **Learning Objectives**

- Get familiar with Labkit interface
- Use *slice-by-slice* labeling to generate manual labels

## Prerequisites

- Basic understanding of Fiji
- 

# **Exercise #0 Data download & Installation**

Download example 3D dataset:

[https://bbbc.broadinstitute.org/BBBC032](https://bbbc.broadinstitute.org/BBBC032)

Install Labkit via update site:

***Help > Update...***

In the ImageJ Updater click ***Manage Update sites***.

In the pop up menu activate ***Labkit*** - ([https://sites.imagej.net/Labkit/](https://sites.imagej.net/Labkit/)) update site:

[https://lh5.googleusercontent.com/x4Io3Odq_IphqwjOKEpmaO5eRxMjBm9-rlcylU73shO3-iN55EXo1FUy8o7Z_C3UqE8s98p-0WwSVfrhUCAI5kpUdbHqwtjl77c09PvVX4777-aFAXMzns16Y85CQGejucpsfkNz1PNInXirsYUrtqE](https://lh5.googleusercontent.com/x4Io3Odq_IphqwjOKEpmaO5eRxMjBm9-rlcylU73shO3-iN55EXo1FUy8o7Z_C3UqE8s98p-0WwSVfrhUCAI5kpUdbHqwtjl77c09PvVX4777-aFAXMzns16Y85CQGejucpsfkNz1PNInXirsYUrtqE)

Install dependencies for GPU acceleration (if a good GPU is available at your machine - which is the case for the VDIs):

Activate ***clij*** and ***clij2*** update sites

[https://lh6.googleusercontent.com/0aFftN98SuTo99fkz4y7IV-4z5wG0-M8_Wdttmc1kkrZbKbWF8JV1pmT5sBE6zHVuCO6Eo5lni4Bwr8-6XIsoc6GUaHZl4NNLKb2sb0cMK9SUevj4P3f1-yhoeQxUrG0bwZ0SCRW5CL6TIL4KXRvJfE](https://lh6.googleusercontent.com/0aFftN98SuTo99fkz4y7IV-4z5wG0-M8_Wdttmc1kkrZbKbWF8JV1pmT5sBE6zHVuCO6Eo5lni4Bwr8-6XIsoc6GUaHZl4NNLKb2sb0cMK9SUevj4P3f1-yhoeQxUrG0bwZ0SCRW5CL6TIL4KXRvJfE)

Click ***Close***.

In the ImageJ then select ***Apply changes***. Restart Fiji.

**NOTE:** In order to benefit from the performance boost that BigDataViewer (BDV) offers particularly for rapid visualization you should re-save the data as BDV XML/HDF5: [https://imagej.net/plugins/bdv/#exporting-datasets-for-the-bigdataviewer](https://imagej.net/plugins/bdv/#exporting-datasets-for-the-bigdataviewer)

In Fiji:

***Plugins > BigDataViewer > Export Current Image as XML/HDF5***

# **Exercise #1 Open data and navigate**

Unzip the example dataset. We will have a look at channel 3 of this dataset:

**BMP4blastocystC3.tif**

Open the example dataset in Fiji by ***drag & drop***.

[https://lh5.googleusercontent.com/1CNEPq40kAeEW4ccWkvx1stXRrhpzSsAg_iG0DAx7d1IYTKWndyBxnxh6qn13q6pCv-5BTN1JsvktcTWVfknBLUAF4NbEBQ_yPZbYqnpprBjfItmfhhaEjOpHAYC7yGaGab2jfQh17OCHUFO1meLL0s](https://lh5.googleusercontent.com/1CNEPq40kAeEW4ccWkvx1stXRrhpzSsAg_iG0DAx7d1IYTKWndyBxnxh6qn13q6pCv-5BTN1JsvktcTWVfknBLUAF4NbEBQ_yPZbYqnpprBjfItmfhhaEjOpHAYC7yGaGab2jfQh17OCHUFO1meLL0s)

Load the image volume into Labkit:

***Plugins > Labkit > Open Current Image in Labkit***

The image gets opened in Labkit:

[https://lh4.googleusercontent.com/hK5oubgb6o1jBwprVq1G42KTvLPyjXmJFcsUoy851RO_9ReOyJtrgXuWkNndaY_ehXzCjg4FrbnB8MpDcfGjwmKq8ZdXfDk3GK_VvNmHghJW99-VqfH1X4ABQ_PFHcsZcK10a4cl8j1tW9hB5WOy_LU](https://lh4.googleusercontent.com/hK5oubgb6o1jBwprVq1G42KTvLPyjXmJFcsUoy851RO_9ReOyJtrgXuWkNndaY_ehXzCjg4FrbnB8MpDcfGjwmKq8ZdXfDk3GK_VvNmHghJW99-VqfH1X4ABQ_PFHcsZcK10a4cl8j1tW9hB5WOy_LU)

Adjust the contrast by pressing: ***auto contrast***.

[https://lh5.googleusercontent.com/FFutfEa0cnI5Upwbu8n_GD9z2yUtRuXatZSFmqbTtyU_7XUBXktDztFmiTbSP3Pmlo0DSq31yQVGn7hV71mm0I5wjw5AWy0Ozgmm-spbSzfom_HFXz6v74s5ylPUtgDmHlkmiJMtZ5XUofqg44R4cP8](https://lh5.googleusercontent.com/FFutfEa0cnI5Upwbu8n_GD9z2yUtRuXatZSFmqbTtyU_7XUBXktDztFmiTbSP3Pmlo0DSq31yQVGn7hV71mm0I5wjw5AWy0Ozgmm-spbSzfom_HFXz6v74s5ylPUtgDmHlkmiJMtZ5XUofqg44R4cP8)

**The Labkit interface:**

[https://lh5.googleusercontent.com/Jy-lutT0eTP2Nb9qQw1XY8URE2iiOHbWg08tFfjHPCVq-24lu_h4_v8SaRXiCCzWm8alo3Q0Crnqohmo-l7DO0ehg6nxlQKUW9Rp_CetLKMyNj2n6_YMkTNcG-29NgEcDeMQPbRf2_BsKbEkJB6Go_w](https://lh5.googleusercontent.com/Jy-lutT0eTP2Nb9qQw1XY8URE2iiOHbWg08tFfjHPCVq-24lu_h4_v8SaRXiCCzWm8alo3Q0Crnqohmo-l7DO0ehg6nxlQKUW9Rp_CetLKMyNj2n6_YMkTNcG-29NgEcDeMQPbRf2_BsKbEkJB6Go_w)

Which consists of the BigDataViewer interface (1). The Labeling classes (2). The labeling tool box (3) as well as the pixel classifier setting (4). We will introduce these now in more detail. 

## **(1) The BigDataViewer interface.**

This allows rapid interaction with the 3D volume. The interaction works via the mouse and keyboard. For all the interactions have a look here: [https://imagej.net/plugins/bdv/](https://imagej.net/plugins/bdv/)

You see in the field-of-view a slice through the image volume. In the top left corner the green/magenta wire diagram visualizes the entire volume. The gray slices corresponds to the visualized slice in this volume

The most relevant mouse and keyboard interactions for BDV are the:

***Mouse wheel:*** scroll through the volume

***Right mouse click & hold and drag***: pan the image

***Left mouse click & hold and drag***: rotate around the mouse pointer

***Up & down arrow keys (Ctrl + Shift + Mouse scroll)***: zoom in and out

***Right & left arrow keys:*** rotate around a selected axis (select axis by pressing x,y or z)

***Shift & x, y or z:*** rotate 90 degrees around a specific axis

**TIP:** speed up interactions by pressing and holding SHIFT

## **(2) Labeling classes**

This box allows you to define and adjust the labeling classes. You can turn on/off the labeling by pressing the “eye” symbol. You can add and remove labels by *Add label* and *Remove all*. You can change the color of the class by pressing on the color. To rename a label, click the down arrow box to enter the options and choose ***Rename*.**

[https://lh6.googleusercontent.com/khe_eUJV9CsvGJC9OwgVHKehq5pFsNk1xcz1vOY6JmkY9NYVsoAVTSQciemimq2PrxhOjGWAh1dU3xZ1MtaCIv7e8FBEhkogCfdSqpxyZJSZKmAyv9JZte-gr4eShaLiUKGZ4Bp7GHpe-ZDdPLyjH9Y](https://lh6.googleusercontent.com/khe_eUJV9CsvGJC9OwgVHKehq5pFsNk1xcz1vOY6JmkY9NYVsoAVTSQciemimq2PrxhOjGWAh1dU3xZ1MtaCIv7e8FBEhkogCfdSqpxyZJSZKmAyv9JZte-gr4eShaLiUKGZ4Bp7GHpe-ZDdPLyjH9Y)

## **(3) Labeling tool box**

Pressing the arrow cross activates the interaction mode in BDV so you can navigate the data with the mouse.

[https://lh5.googleusercontent.com/cyMJM4riA2xvNgj5hVVvGINrCN9F0-O2XiQPn15xe-DPH0re0OlIiWcb9LBeFq1LUhYy4bGCIWinR3T3tTUWVcz3bA6HFVIc9zE5iOnmeSSzXe0aL2enBzxqY5w9VJTBuJTlQJGdLi-8VNvCBXKEs2w](https://lh5.googleusercontent.com/cyMJM4riA2xvNgj5hVVvGINrCN9F0-O2XiQPn15xe-DPH0re0OlIiWcb9LBeFq1LUhYy4bGCIWinR3T3tTUWVcz3bA6HFVIc9zE5iOnmeSSzXe0aL2enBzxqY5w9VJTBuJTlQJGdLi-8VNvCBXKEs2w)

You can select the pencil (**Ctrl-D**) for labeling the images. Change the brush size on the right. You can fill a closed (!) outline using the fill function (**Ctrl-F**). You can use the eraser (**Ctrl-E**) to modify the labels. Finally you can delete entire connected components (**Ctrl-R**).

[https://lh4.googleusercontent.com/NuA0vtD1T1gFwFG-WW6w_3A1_S8V5EOeiN4MfUthhvOX9uGi3S7bFd-eX5uWtIf3WkSHkS0bYg1PMuRJYtBCcNzV--FfAAUKYXE_8L6rWh-OLnDheu3llOAO1J56s2FYsfXPm4LKEU3xX586Npf9Rzs](https://lh4.googleusercontent.com/NuA0vtD1T1gFwFG-WW6w_3A1_S8V5EOeiN4MfUthhvOX9uGi3S7bFd-eX5uWtIf3WkSHkS0bYg1PMuRJYtBCcNzV--FfAAUKYXE_8L6rWh-OLnDheu3llOAO1J56s2FYsfXPm4LKEU3xX586Npf9Rzs)

Draw the labels on the BDV canvas.

**NOTE:** You can switch between different visualization modes using the slice mode button on the far right side of the labeling toolbox.

With the 3D-box it is in 3D mode:

[https://lh5.googleusercontent.com/SUicCzhxVAN6Yp8SxPt5Y164J7MvX4igbS7UB1en4uy_yss6I3_HfmuEarX8ubFjoZPDvNMwJXqnc-BN9rNhkx9t4txiSgacfT0RoqyYrpJ4UMTHMXtDDjHdmw2zrEcYhXv59v1vebgcIjUhXJQd3RE](https://lh5.googleusercontent.com/SUicCzhxVAN6Yp8SxPt5Y164J7MvX4igbS7UB1en4uy_yss6I3_HfmuEarX8ubFjoZPDvNMwJXqnc-BN9rNhkx9t4txiSgacfT0RoqyYrpJ4UMTHMXtDDjHdmw2zrEcYhXv59v1vebgcIjUhXJQd3RE)

With the slice-box visible Labkit is in the *slice-by-slice* mode: 

[https://lh6.googleusercontent.com/clvq1Fhdo7lrfSDB_pUT1N8JA-s-He8tcTb4IbwQrHrJBlz9KX3BSygQOVX9Und0lN6Hws1X5r-0ak11qytYPKZjugr24ZGf88zgiSD34MgRGAPb51CHFNJcvNdjHh-Q5ahjFHsM_3hYkyUClHd-7SE](https://lh6.googleusercontent.com/clvq1Fhdo7lrfSDB_pUT1N8JA-s-He8tcTb4IbwQrHrJBlz9KX3BSygQOVX9Und0lN6Hws1X5r-0ak11qytYPKZjugr24ZGf88zgiSD34MgRGAPb51CHFNJcvNdjHh-Q5ahjFHsM_3hYkyUClHd-7SE)

In the *slice-by-slice* mode the image volume will be locked into an xy visualization. Like a typical stack in Fiji. You can scroll through the slices using the mouse wheel. Or the slider on the right.

The *slice-by-slice* mode is helpful if you want to generate and curate dense manual labels

## **(4) Pixel Classifier setting**

[https://lh4.googleusercontent.com/3OUG5SxvTYL-JyEcWnGX6kWjLUZPr_Tj6IzdNIn1CkbcA_2-DB_B905ILCr7x621Kiv3l2vqtQleyuHYvrqxf3oz_fJd0MXUB3nL0AwCpZnjjBvxfGEXPhDTDQnXH3hOqqnZ0sbfiG9BlCf41r0LNBw](https://lh4.googleusercontent.com/3OUG5SxvTYL-JyEcWnGX6kWjLUZPr_Tj6IzdNIn1CkbcA_2-DB_B905ILCr7x621Kiv3l2vqtQleyuHYvrqxf3oz_fJd0MXUB3nL0AwCpZnjjBvxfGEXPhDTDQnXH3hOqqnZ0sbfiG9BlCf41r0LNBw)

Here you can add pixel classifiers by pressing on the ***Labkit Pixel Classification*** button:

[https://lh5.googleusercontent.com/aNQ2z4_mtpeUYfhDVoh5rHV5zDcYw9CKHX9MYHp9tf1s3f1QJLniumAZvu0pNYQYBKrknQ8KnsANnhExjh9tBGiLdory2Rkz7_zX0qMAODOyNdvF0Sg4BetzlSFBf_Q5oiUQNCxMbd0k1pdyc9SgQSU](https://lh5.googleusercontent.com/aNQ2z4_mtpeUYfhDVoh5rHV5zDcYw9CKHX9MYHp9tf1s3f1QJLniumAZvu0pNYQYBKrknQ8KnsANnhExjh9tBGiLdory2Rkz7_zX0qMAODOyNdvF0Sg4BetzlSFBf_Q5oiUQNCxMbd0k1pdyc9SgQSU)

# **Exercise #2 Generate dense manual labels**

For creating the dense manual labels you need to first activate the *slice-by-slice* labelling mode. Press the BDV mode button by pressing on the 3D box:

![Slice.png](DL4MIA%202023%2005a%20-%20Manual%20image%20labeling%20with%20Labki%20f87e922394194ef9907a25913d109193/Slice.png)

The *slice-by-slice* labelling mode will be activated. The button will change to the slice box:

![SliceMode.png](DL4MIA%202023%2005a%20-%20Manual%20image%20labeling%20with%20Labki%20f87e922394194ef9907a25913d109193/SliceMode.png)

The image volume will be locked into an *xy* visualization. Like a typical stack in Fiji. You can scroll through the slices using the mouse wheel. Or the slider on the right:

![SliceMode.png](DL4MIA%202023%2005a%20-%20Manual%20image%20labeling%20with%20Labki%20f87e922394194ef9907a25913d109193/SliceMode%201.png)

Labkit uses the following data labeling tools:

![Figure_curation.png](DL4MIA%202023%2005a%20-%20Manual%20image%20labeling%20with%20Labki%20f87e922394194ef9907a25913d109193/Figure_curation.png)

For drawing on the canvas first select the pencil (D). For drawing dense labels you would like to draw with a larger brush (this is in contrast to what you will do with the labeling for the automatic segmentation later). The brush size can be changed with the slider to the right. For dense labels the best strategy is to first draw the outline of the object. 

![dense1.png](DL4MIA%202023%2005a%20-%20Manual%20image%20labeling%20with%20Labki%20f87e922394194ef9907a25913d109193/dense1.png)

Then you can fill the remaining hole using the fill function (F). 

![dense2.png](DL4MIA%202023%2005a%20-%20Manual%20image%20labeling%20with%20Labki%20f87e922394194ef9907a25913d109193/dense2.png)

The objects can be adjusted using the eraser (E). The eraser size is also adjusted with the brush size. You can easily delete entire connected components with the delete blob function (R). 

Draw the labels on the BDV canvas. Go through all slices and label all relevant parts. You can verify if all slices have been labeled by activating the 3D interaction mode again:

[https://lh5.googleusercontent.com/SUicCzhxVAN6Yp8SxPt5Y164J7MvX4igbS7UB1en4uy_yss6I3_HfmuEarX8ubFjoZPDvNMwJXqnc-BN9rNhkx9t4txiSgacfT0RoqyYrpJ4UMTHMXtDDjHdmw2zrEcYhXv59v1vebgcIjUhXJQd3RE](https://lh5.googleusercontent.com/SUicCzhxVAN6Yp8SxPt5Y164J7MvX4igbS7UB1en4uy_yss6I3_HfmuEarX8ubFjoZPDvNMwJXqnc-BN9rNhkx9t4txiSgacfT0RoqyYrpJ4UMTHMXtDDjHdmw2zrEcYhXv59v1vebgcIjUhXJQd3RE)

You can then rotate the image volume (***Shift + x or shift + y***). A complete dense labelled volume looks like this:

![Complete.png](DL4MIA%202023%2005a%20-%20Manual%20image%20labeling%20with%20Labki%20f87e922394194ef9907a25913d109193/Complete.png)

Whereas with missing slices it will look like this:

![Missing.png](DL4MIA%202023%2005a%20-%20Manual%20image%20labeling%20with%20Labki%20f87e922394194ef9907a25913d109193/Missing.png)

## Semantic vs instance segmentation

An important aspect is to understand the difference between instance and semantic segmentation. A semantic segmentation will not differentiate between individual objects within one class. Thus, even if you manually label individual cell separately they will all be labeled with the same label identity. An instance segmentation will differentiate individual objects with a separate label. 

By default Labkit is setup to primarily support semantic segmentation, especially in the automatic segmentation mode. You can label individual objects by using one class and then use a different tool to generate label mask afterwards. However, in this case you need to make sure the labeled objects are **well separated** (could be hard in 3D). Afterwards one could use other tools to generate individual labels for the well separated labeled objects. 

The alternative to this is to use per object one class. This is also supported in Labkit but might be a bit awkward to use.

![instances.png](DL4MIA%202023%2005a%20-%20Manual%20image%20labeling%20with%20Labki%20f87e922394194ef9907a25913d109193/instances.png)

# **Exercise #3 Save labeling**

When you are happy with the labels save them by:

***Labkit > Labeling > Save Labeling ...***

You can also load labelings:

***Labkit > Labeling > Open Labeling ...***

You can save the labels also as a new image by selecting the correct labeling class in the labeling interface and then:

***Labkit > Labeling > Export Selected Label as Bitmap***

The image volume exported shows for the label class as binary mask with 1 being the exported label. 

[https://lh6.googleusercontent.com/lu2YMDfcYBUDFWpOlgk_9luFJH2LuhId765HCcJ4xonS4wFLBMr4yXU2vAyGqZNr17_CHiZuealkdyktUd79qLYHkuQpPjZyeQxBPafYcVjh91AMINozC2ixFtrk8eWrpzfzadx4rEKEsh0lKkT0azc](https://lh6.googleusercontent.com/lu2YMDfcYBUDFWpOlgk_9luFJH2LuhId765HCcJ4xonS4wFLBMr4yXU2vAyGqZNr17_CHiZuealkdyktUd79qLYHkuQpPjZyeQxBPafYcVjh91AMINozC2ixFtrk8eWrpzfzadx4rEKEsh0lKkT0azc)

In order to use this in Fiji we need to convert the 0 1 binary image to a Fiji binary image with 0 and 255 value. You can do this using the thresholding method:

***Image > Adjust > Threshold ...***

The thresholding applet opens. Then press ***Set*** in the thresholding applet. A new window will pop up that allows you to set manual thresholds. Set a lower and upper threshold level to select the specific class you want to work on further. Then press ***ok*** in the ***Set Threshold Levels***.

[https://lh6.googleusercontent.com/k6Zo_vZg2dF2OoEYWyqU7lcsstbwIq7ZAY3PHMvhjxQU5hrFilwLWOrRz6kklqTiMBo-vZg4F-zBHgtrCSJURlz2M_2yD-5FSOdpx0gVJIXpMUeQIilS8AUdpp3I26twp8YZUKbGc4-GFwyGTmd7WkA](https://lh6.googleusercontent.com/k6Zo_vZg2dF2OoEYWyqU7lcsstbwIq7ZAY3PHMvhjxQU5hrFilwLWOrRz6kklqTiMBo-vZg4F-zBHgtrCSJURlz2M_2yD-5FSOdpx0gVJIXpMUeQIilS8AUdpp3I26twp8YZUKbGc4-GFwyGTmd7WkA)

Then press ***Apply.*** A new window will pop up with ***Convert Stack to Binary***. Untick Calculate threshold for each image to take in the manual settings. Click ok to apply the threshold, which results in a binary image that you can use for any further processing.

[https://lh3.googleusercontent.com/AaMouc_3QjMRGWrpy5T0acnCfth8Ulrmw1OSDhkXcrp7Q4f6kH3_3Qme6-ghmGA99hMVwD7_58tmMonxHC7bggW_pjEjXieddH7tAFqo9wZZ8aifi7LxCyEUDKyZS6tIn16VAtMna0_zI0YhkUHygbs](https://lh3.googleusercontent.com/AaMouc_3QjMRGWrpy5T0acnCfth8Ulrmw1OSDhkXcrp7Q4f6kH3_3Qme6-ghmGA99hMVwD7_58tmMonxHC7bggW_pjEjXieddH7tAFqo9wZZ8aifi7LxCyEUDKyZS6tIn16VAtMna0_zI0YhkUHygbs)

You can then further process the binary mask in Fiji. For example you could create an instance segmentation. 

### Turning the binary mask into an instance segmentation

For an instance segmentation you need to create individual labels per object. If you did not label each individual object with a different class label you can use other tools to generate individually labeled objects from the semantic segmentation: [https://imagej.net/plugins/morpholibj#connected-component-labeling](https://imagej.net/plugins/morpholibj#connected-component-labeling)

You need to install MorphoLibJ for this: [https://imagej.net/plugins/morpholibj#installation](https://imagej.net/plugins/morpholibj#installation)

In MorphoLibJ apply then on a binary mask the connected component labeling:

***Plugins > MorphoLibJ > Binary Images > Connected Components labeling*** 

This will give each connected component a different grey value. 

![cellMask.png](DL4MIA%202023%2005a%20-%20Manual%20image%20labeling%20with%20Labki%20f87e922394194ef9907a25913d109193/cellMask.png)

![cellMask-lbl.png](DL4MIA%202023%2005a%20-%20Manual%20image%20labeling%20with%20Labki%20f87e922394194ef9907a25913d109193/cellMask-lbl.png)

If your labels should have pretty colors instead of the grey values you can use:

***Plugins > MorphoLibJ > Label Images > Labels to RGB***

**NOTE:** make sure you set the background color to your liking

![cellMask-lbl-rgb.png](DL4MIA%202023%2005a%20-%20Manual%20image%20labeling%20with%20Labki%20f87e922394194ef9907a25913d109193/cellMask-lbl-rgb.png)
