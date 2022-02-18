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


## Codes_details
### Positional Encoding

        pe[0::4, :, :] = torch.sin(x_position * div_term)
        pe[1::4, :, :] = torch.cos(x_position * div_term)
        pe[2::4, :, :] = torch.sin(y_position * div_term)
        pe[3::4, :, :] = torch.cos(y_position * div_term)
Here are the codes for postions encoding; 0::4 means that taking the indexs which is divisible by 4, 1::4 means the indexs dividing 4 left 1
### Calculating Sim Matrix
     # normalize
        feat_c0, feat_c1 = map(lambda feat: feat / feat.shape[-1]**.5,
                               [feat_c0, feat_c1])

        if self.match_type == 'dual_softmax':
            sim_matrix = torch.einsum("nlc,nsc->nls", feat_c0,
                                      feat_c1) / self.temperature
            if mask_c0 is not None:
                sim_matrix.masked_fill_(
                    ~(mask_c0[..., None] * mask_c1[:, None]).bool(),
                    -INF)
            conf_matrix = F.softmax(sim_matrix, 1) * F.softmax(sim_matrix, 2)

        elif self.match_type == 'sinkhorn':
            # sinkhorn, dustbin included
            sim_matrix = torch.einsum("nlc,nsc->nls", feat_c0, feat_c1)
            if mask_c0 is not None:
                sim_matrix[:, :L, :S].masked_fill_(
                    ~(mask_c0[..., None] * mask_c1[:, None]).bool(),
                    -INF)
python中map(func,iterable)代表的是迭代式地调用函数func，在上述例子中，map(lambda feat:feat/feat.shape[-1]**.5,[feat_c0,feat_c1])，迭代地调用了lamdba中定义的函数 

