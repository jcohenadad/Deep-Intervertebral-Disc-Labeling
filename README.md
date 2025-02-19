# [Stacked Hourglass Network with a Multi-level Attention Mechanism: Where to Look for Intervertebral Disc Labeling]()

Automatic labeling of the intervertebral disc is a difficult task, due to the many challenges such as complex background, the similarity between discs and bone area in MRI imaging, blurry image, and variation in an imaging modality. Precisely localizing spinal discs plays an important role in intervertebral disc labeling. Most of the literature work consider the semantic intervertebral disc labeling as a post-processing step, which applies on the top of the disc localization algorithm. Hence, the semantic intervertebral labeling highly depends on the disc localization algorithm and mostly fails when the localization algorithm cannot detect discs or falsely detects a background area as a disc. In this work, we aimed to mitigate this problem by reformulating the semantic intervertebral disc labeling using the pose estimation technique. If this code helps with your research please consider citing the following papers:
</br>
> [R. Azad](https://scholar.google.com/citations?hl=en&user=Qb5ildMAAAAJ&view_op=list_works&sortby=pubdate), [xx](), and [xx]() "Stacked Hourglass Network with a Multi-level Attention Mechanism: Where to Look for Intervertebral Disc Labeling", MICCAI Workshop, 2021, download [link]().


#### Please consider starring us, if you found it useful. Thanks

## Updates
- 11-8-2021: Source code is available. </br>


## Prerequisties and Run
This code has been implemented in python language using Pytorch libarary and tested in ubuntu, though should be compatible with related environment. The required libraries are included in the requiremetns.txt file. Please follow the bellow steps to train and evaluate the model. </br>

1- Download the [Spine Generic Public Database (Multi-Subject)](https://github.com/spine-generic/data-multi-subject#spine-generic-public-database-multi-subject).</br>
2- Run the `create_dataset.py` to gather the required data from the Spin Generic dataset. </br>
4- Run `prepare_trainset.py` to creat the training and validation samples. </br>
**Notice: To avoid the above steps we have provided the processed data for all train, validation and test sets [here](https://drive.google.com/file/d/1z_mcIEoT_doyh_Hl53OaYWyplUel_-RT/view?usp=sharing) (should be around 150 MB)** you can simply download it and continue with the rest steps. </br>
5- Run the `main.py` to train and evaluate the model. Use the following command with the related arguments to perform the required action:</br>
A- Train and evaluate the model `python src/main.py`. You can use `--att true` to use the attention mechanisim. </br>
B- Evaluate the model `python src/main.py --evaluate true ` it will load the trained model and evalute it on the validation set. </br>
C- You can run `make_res_gif.py` to creat a prediction video using the prediction images generated by `main.py` for the validation set.  </br>
D- You can change the number of stacked hourglass by `--stacks ` argument. For more details check the arguments section in `main.py`.  </br>
6- Run the `test.py` to evaluate the model on the test set alongside with the metrics. </br>


## Quick Overview
![Diagram of the proposed method](https://github.com/rezazad68/Deep-Intervertebral-Disc-Labeling/blob/main/images/Proposed_method.png)

#### Visualzie the attention channel

To extract and show the attention channel for the related input sample, we registered the attention channel by the forward hook. Thus with the following command, you can visualize the input sample, estimated vertebral disc location, and the attention channel. </br>
`python src/main.py --evaluate true --attshow true `. </br>

![Attention visualization](https://github.com/rezazad68/Deep-Intervertebral-Disc-Labeling/blob/main/images/attention_visualization.png)


#### Sample of detection result on the test set
Below we illustrated a sample of vertebral disc detection on the test set. 

![Test sample](https://github.com/rezazad68/Deep-Intervertebral-Disc-Labeling/blob/main/images/Sample_results.png)

### Model weights
You can download the learned weights for each modality in the following table. 

Method | Modality |Learned weights
------------ | -------------|----
Proposed model without attention | T1w | [download](https://drive.google.com/file/d/102U8NlSIelkEmSu4J-Qw-djKsKi6dudt/view?usp=sharing)
Proposed model without attention | T2w | [download](https://drive.google.com/file/d/1pzGDRwFSWb6FN3o8GZD2xrH3gNcPjImt/view?usp=sharing)
Proposed model with    attention | T1w | [download](https://drive.google.com/file/d/1o5DWzHlhMDic5eynrEQMupjZwsmCr5XP/view?usp=sharin)
Proposed model with    attention | T2w | [download](https://drive.google.com/file/d/1zvBbiCVH1gnrYUbzVF6JAUpcpQg7I2dn/view?usp=sharing)

