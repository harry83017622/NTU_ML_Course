## **Note** ##
---
### Task ###
* Classify 11 kinds of food with label (2k) and unlabel (6k) data.  

### Sample code ###
* Use default model, and train from scratch.
* Only use label data

### What I tried ###
> * Data augmentation
> * Resnet18 w/o pretrain (pretrained is prohibited)  
> * Some hyperparameters  

This makes me pass the medium baseline. (~52% acc)

> * Take advantage of unlabel data with semi-supervise
> * Adjust threshold of semi-supervise using 0.46-0.002*epoch
> * Early stop, then use the previous ckpt to start training (w/ some change of hyperparameters)  

This makes me increasing acc to ~78%

> * https://arxiv.org/pdf/1911.04252.pdf
> * https://storage.googleapis.com/pub-tools-public-publication-data/pdf/93696f26a973dd0fc6fe20dcfd9b56634702f341.pdf
> * not tried dropout/ stochastic depth
> * tried balanced sampling (ignore label-wise distribution) but didn't see any improvement. (ex. 2k label + 2k unlabel during semi-supervise sampling)
> * label and unlabel order during training matters, otherwise, need to fuse them together use cocatdataset and dataloader  

Above didn't see any improvement, furthermore distroyed my model from 78% acc to ~60%  

> * Future worth try
> * balanced sampling (follow label distribution ex. class1 5% class2 30% ... when sampling during semi-supervise)