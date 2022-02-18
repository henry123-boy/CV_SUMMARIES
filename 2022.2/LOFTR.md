# LoFTR: Detector-Free Local Feature Matching with Transformers
## abstract 
We present a novel method for local image feature
matching. Instead of performing image feature detection,
description, and matching sequentially, we propose to first
establish pixel-wise dense matches at a coarse level and
later refine the good matches at a fine level. In contrast
to dense methods that use a cost volume to search correspondences, we use self and cross attention layers in Transformer to obtain feature descriptors that are conditioned on
both images. The global receptive field provided by Transformer enables our method to produce dense matches in
low-texture areas, where feature detectors usually struggle to produce repeatable interest points. The experiments
on indoor and outdoor datasets show that LoFTR outperforms state-of-the-art methods by a large margin. LoFTR
also ranks first on two public benchmarks of visual localization among the published methods. Code is available at
our project page: https://zju3dv.github.io/loftr/.

## Insights
+ using the coarse to fine scheme, globale receptive by transformer and local receptive by CNN

## Architecture
![Pipeline](https://user-images.githubusercontent.com/62553342/154661662-d59f170f-b5c8-4df0-9ba7-21daa4dad725.png)

