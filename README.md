# Awesome Feed-Forward 3D Reconstruction and View Synthesis

[![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

A curated list of papers on feed-forward 3D reconstruction and view synthesis, organized by the taxonomy of the survey:

> **Advances in Feed-Forward 3D Reconstruction and View Synthesis: A Survey**
> Jiahui Zhang, Yuelei Li, Anpei Chen, Muyu Xu, Kunhao Liu, Jianyuan Wang, Xiao-Xiao Long, Hanxue Liang, Zexiang Xu, Hao Su, Christian Theobalt, Christian Rupprecht, Andrea Vedaldi, Kaichen Zhou, Hanspeter Pfister, Paul Pu Liang, Shijian Lu, Fangneng Zhan
> [📃 Paper](https://arxiv.org/abs/2503.24529) | [🌐 Project Page](https://fnzhan.com/projects/Feed-Forward-3D)

## Citation

If you find this work useful in your research, please consider citing:

```bibtex
@article{Zhang2025FF3D,
    author = {Jiahui Zhang and Yuelei Li and Anpei Chen and Muyu Xu and Kunhao Liu and
              Jianyuan Wang and Xiao-Xiao Long and Hanxue Liang and Zexiang Xu and Hao Su and
              Christian Theobalt and Christian Rupprecht and Andrea Vedaldi and Kaichen Zhou and
              Hanspeter Pfister and Paul Pu Liang and Shijian Lu and Fangneng Zhan},
    title = {Advances in Feed-Forward 3D Reconstruction and View Synthesis},
    journal = {Computer Graphics Forum},
    year = {2026}
}
```

---

## Table of Contents

Feel free to submit a Pull Request if you would like to update the list.

- [NeRF-Based Methods](#nerf-based-methods)
  - [1D Feature-Based](#1d-feature-based)
  - [2D Feature-Based](#2d-feature-based)
  - [3D Volume Feature-Based](#3d-volume-feature-based)
  - [3D Triplane Feature-Based](#3d-triplane-feature-based)
  - [Other NeRF Methods](#other-nerf-methods)
- [Pointmap-Based Methods](#pointmap-based-methods)
- [3D Gaussian Splatting Methods](#3d-gaussian-splatting-methods)
  - [Gaussian Map: General](#gaussian-map-general)
  - [Gaussian Map: Epipolar-Guided](#gaussian-map-epipolar-guided)
  - [Gaussian Map: Cost-Volume-Based](#gaussian-map-cost-volume-based)
  - [Gaussian Map: Pretrained-Model-Based](#gaussian-map-pretrained-model-based)
  - [Gaussian Volume](#gaussian-volume)
- [Other 3D Representations](#other-3d-representations)
  - [Mesh-Based Methods](#mesh-based-methods)
  - [Occupancy-Based Methods](#occupancy-based-methods)
  - [SDF-Based Methods](#sdf-based-methods)
- [3D-Free Models](#3d-free-models)
  - [Regression-Based](#regression-based)
  - [Image Diffusion-Based](#image-diffusion-based)
  - [Video Diffusion-Based](#video-diffusion-based)

---

## NeRF-Based Methods

### 1D Feature-Based

#### CodeNeRF ![](https://img.shields.io/badge/2021-ICCV-yellow)
**Authors**: Wonbong Jang, Lourdes Agapito

<details span>
<summary><b>Abstract</b></summary>
CodeNeRF is an implicit 3D neural representation that learns the variation of object shapes and textures across a category and can be trained, from a set of posed images, to synthesize novel views of unseen objects. Unlike the original NeRF, which is scene specific, CodeNeRF learns to disentangle shape and texture by learning separate embeddings. At test time, given a single unposed image of an unseen object, CodeNeRF jointly estimates camera viewpoint, and shape and appearance codes via optimization. Unseen objects can be reconstructed from a single image, and then rendered from new viewpoints or their shape and texture edited by varying the latent codes. We conduct experiments on the SRN benchmark, which show that CodeNeRF generalises well to unseen objects and achieves on-par performance with methods that require known camera pose at test time. Our results on real-world images demonstrate that CodeNeRF can bridge the sim-to-real gap.
</details>

[📃 Paper](https://arxiv.org/abs/2109.01750) | [🌐 Project Page](https://sites.google.com/view/wbjang/home/codenerf) | [⌨️ Code](https://github.com/wbjang/code-nerf)

---

#### ShaRF ![](https://img.shields.io/badge/2021-ICML-blue)
**Authors**: Konstantinos Rematas, Ricardo Martin-Brualla, Vittorio Ferrari

<details span>
<summary><b>Abstract</b></summary>
We present a method for estimating neural scenes representations of objects given only a single image. The core of our method is the estimation of a geometric scaffold for the object and its use as a guide for the reconstruction of the underlying radiance field. Our formulation is based on a generative process that first maps a latent code to a voxelized shape, and then renders it to an image, with the object appearance being controlled by a second latent code. During inference, we optimize both the latent codes and the networks to fit a test image of a new object. The explicit disentanglement of shape and appearance allows our model to be fine-tuned given a single image. We can then render new views in a geometrically consistent manner and they represent faithfully the input object. Additionally, our method is able to generalize to images outside of the training domain (more realistic renderings and even real photographs). Finally, the inferred geometric scaffold is itself an accurate estimate of the object's 3D shape. We demonstrate in several experiments the effectiveness of our approach in both synthetic and real images.
</details>

[📃 Paper](https://arxiv.org/abs/2102.08860)

---

#### Shap-E ![](https://img.shields.io/badge/2023-arXiv-red)
**Authors**: Heewoo Jun, Alex Nichol

<details span>
<summary><b>Abstract</b></summary>
We present Shap-E, a conditional generative model for 3D assets. Unlike recent work on 3D generative models which produce a single output representation, Shap-E directly generates the parameters of implicit functions that can be rendered as both textured meshes and neural radiance fields. We train Shap-E in two stages: first we train an encoder that deterministically maps 3D assets into the parameters of an implicit function, then we train a conditional diffusion model on outputs of the encoder. When trained on a large dataset of paired 3D and text data, our resulting models are capable of generating complex and diverse 3D assets in a matter of seconds.
</details>

[📃 Paper](https://arxiv.org/abs/2305.02463) | [⌨️ Code](https://github.com/openai/shap-e)

---

### 2D Feature-Based

#### PixelNeRF ![](https://img.shields.io/badge/2021-CVPR-green)
**Authors**: Alex Yu, Vickie Ye, Matthew Tancik, Angjoo Kanazawa

<details span>
<summary><b>Abstract</b></summary>
We propose pixelNeRF, a learning framework that predicts a continuous neural scene representation conditioned on one or few input images. The existing approach for constructing neural radiance fields involves optimizing the representation to every scene independently, requiring many calibrated views and significant compute time. We address this issue by introducing an architecture that conditions a NeRF on image inputs in a fully convolutional manner. Given one or few input images of a scene, pixelNeRF can render novel views in a feed-forward manner without any test-time optimization, enabling the model to generalize across diverse unseen scenes. The model is trained across multiple scenes to learn a scene prior while leveraging spatial image features that correspond to each pixel of the NeRF queries.
</details>

[📃 Paper](https://arxiv.org/abs/2012.02190) | [🌐 Project Page](https://alexyu.net/pixelnerf/) | [⌨️ Code](https://github.com/sxyu/pixel-nerf)

---

#### GRF ![](https://img.shields.io/badge/2021-ICCV-yellow)
**Authors**: Alex Trevithick, Bo Yang

<details span>
<summary><b>Abstract</b></summary>
We present a simple yet powerful neural network that implicitly represents and renders 3D objects and scenes only from 2D observations. The network models 3D geometries as a general radiance field, which takes a set of 2D images with camera poses and intrinsics as input, constructs an internal representation for each point of the 3D space, and then renders the corresponding appearance and geometry of that point viewed from an arbitrary position. The key to our approach is to learn local features for each pixel in 2D images and to then project these features to 3D points, thus yielding general and rich point representations. We additionally integrate an attention mechanism to aggregate pixel features from multiple 2D views, such that visual occlusions are implicitly taken into account. Extensive experiments demonstrate that our method can generate high-quality and realistic novel views for novel objects, unseen categories and challenging real-world scenes.
</details>

[📃 Paper](https://arxiv.org/abs/2010.04595) | [⌨️ Code](https://github.com/alextrevithick/GRF)

---

#### IBRNet ![](https://img.shields.io/badge/2021-CVPR-green)
**Authors**: Qianqian Wang, Zhicheng Wang, Kyle Genova, Pratul Srinivasan, Howard Zhou, Jonathan T. Barron, Ricardo Martin-Brualla, Noah Snavely, Thomas Funkhouser

<details span>
<summary><b>Abstract</b></summary>
We present a method that synthesizes novel views of complex scenes by interpolating a sparse set of nearby views. The core of our method is a network architecture that includes a multilayer perceptron and a ray transformer that estimates radiance and volume density at continuous 5D locations (3D spatial locations and 2D viewing directions), drawing appearance information on the fly from multiple source views. By drawing on source views at render time, our method hearkens back to classic work on image-based rendering (IBR), and allows us to render high-resolution imagery. Unlike neural scene representation work that optimizes per-scene functions for rendering, we learn a generic view interpolation function that generalizes to novel scenes. We render images using classic volume rendering, which is fully differentiable and allows us to train using only multi-view posed images as supervision. Experiments show that our method outperforms recent novel view synthesis methods that also seek to generalize to novel scenes. Further, if fine-tuned on each scene, our method is competitive with state-of-the-art single-scene neural rendering methods.
</details>

[📃 Paper](https://arxiv.org/abs/2102.13090) | [🌐 Project Page](https://ibrnet.github.io/) | [⌨️ Code](https://github.com/googleinterns/IBRNet)

---

#### NeRFormer ![](https://img.shields.io/badge/2021-arXiv-red)
**Authors**: Jeremy Reizenstein, Roman Shapovalov, Philipp Henzler, Luca Sbordone, Patrick Labatut, David Novotny

<details span>
<summary><b>Abstract</b></summary>
We introduce Common Objects in 3D (CO3D), a large-scale dataset for real-world object-centric multi-view capture, along with NerFormer, a novel neural rendering method that leverages the powerful Transformer architecture to reconstruct an object given a small number of its views. CO3D contains a total of 1.5 million frames from nearly 19,000 videos capturing objects from 50 MS-COCO categories and, as such, it is significantly larger than alternatives both in terms of the number of categories and objects. We exploit this new dataset to conduct one of the first large-scale "in-the-wild" evaluations of several new-view-synthesis and category-centric 3D reconstruction methods.
</details>

[📃 Paper](https://arxiv.org/abs/2109.00512) | [⌨️ Code](https://github.com/facebookresearch/co3d)

---

#### SRF ![](https://img.shields.io/badge/2021-CVPR-green)
**Authors**: Julian Chibane, Aayush Bansal, Verica Lazova, Gerard Pons-Moll

<details span>
<summary><b>Abstract</b></summary>
Recent neural view synthesis methods have achieved impressive quality and realism, surpassing classical pipelines which rely on multi-view reconstruction. State-of-the-Art methods, such as NeRF, are designed to learn a single scene with a neural network and require dense multi-view inputs. Testing on a new scene requires re-training from scratch, which takes 2-3 days. In this work, we introduce Stereo Radiance Fields (SRF), a neural view synthesis approach that is trained end-to-end, generalizes to new scenes, and requires only sparse views at test time. The core idea is a neural architecture inspired by classical multi-view stereo methods, which estimates surface points by finding similar image regions in stereo images. In SRF, we predict color and density for each 3D point given an encoding of its stereo correspondence in the input images. The encoding is implicitly learned by an ensemble of pair-wise similarities -- emulating classical stereo. Experiments show that SRF learns structure instead of overfitting on a scene. We train on multiple scenes of the DTU dataset and generalize to new ones without re-training, requiring only 10 sparse and spread-out views as input. We show that 10-15 minutes of fine-tuning further improve the results, achieving significantly sharper, more detailed results than scene-specific models.
</details>

[📃 Paper](https://arxiv.org/abs/2104.06935) | [🌐 Project Page](https://virtualhumans.mpi-inf.mpg.de/srf/) | [⌨️ Code](https://github.com/jchibane/srf)

---

#### GNT ![](https://img.shields.io/badge/2022-arXiv-red)
**Authors**: Guangcong Wang, Zhaoxi Chen, Chen Change Loy, Ziwei Liu

<details span>
<summary><b>Abstract</b></summary>
We present the Generalizable NeRF Transformer (GNT), a transformer-based architecture that reconstructs Neural Radiance Fields (NeRFs) and renders novel views on the fly from source views. While prior works on generalizable NeRFs condition on source views via feature extraction and point sampling, GNT achieves neural representation and rendering that generalizes across scenes using transformers at two stages. The view transformer leverages multi-view geometry as an inductive bias for attention-based scene representation, and predicts coordinate-aligned features by aggregating information from epipolar lines on the neighboring views. The ray transformer renders novel views using attention to decode the features from the view transformer along the sampled points during ray marching. Our experiments demonstrate that when optimized on a single scene, GNT can successfully reconstruct NeRF without an explicit rendering formula due to the learned ray renderer. When trained across multiple scenes, GNT consistently achieves state-of-the-art performance on multiple benchmarks for novel view synthesis.
</details>

[📃 Paper](https://arxiv.org/abs/2207.13298) | [⌨️ Code](https://github.com/VITA-Group/GNT)

---

#### GNT-MOVE ![](https://img.shields.io/badge/2023-CVPR-green)
**Authors**: Guangcong Wang, Zhaoxi Chen, Chen Change Loy, Ziwei Liu

<details span>
<summary><b>Abstract</b></summary>
Cross-scene generalizable NeRF models, which can directly synthesize novel views of unseen scenes, have become a new spotlight of the NeRF field. Several existing attempts rely on increasingly end-to-end "neuralized" architectures, i.e., replacing scene representation and/or rendering modules with performant neural networks such as transformers, and turning novel view synthesis into a feed-forward inference pipeline. While those feedforward "neuralized" architectures still do not fit diverse scenes well out of the box, we propose to bridge them with the powerful Mixture-of-Experts (MoE) idea from large language models (LLMs), which has demonstrated superior generalization ability by balancing between larger overall model capacity and flexible per-instance specialization. Starting from a recent generalizable NeRF architecture called GNT, we first demonstrate that MoE can be neatly plugged in to enhance the model. We further customize a shared permanent expert and a geometry-aware consistency loss to enforce cross-scene consistency and spatial smoothness respectively, which are essential for generalizable view synthesis. Our proposed model, dubbed GNT with Mixture-of-View-Experts (GNT-MOVE), has experimentally shown state-of-the-art results when transferring to unseen scenes, indicating remarkably better cross-scene generalization in both zero-shot and few-shot settings.
</details>

[📃 Paper](https://arxiv.org/abs/2308.11793) | [⌨️ Code](https://github.com/VITA-Group/GNT-MOVE)

---

#### MatchNeRF ![](https://img.shields.io/badge/2023-CVPR-green)
**Authors**: Lichen Chen, Liangjian Cheng, Wei Yin, Liuhua Peng, Chunhua Shen

<details span>
<summary><b>Abstract</b></summary>
We present a new generalizable NeRF method that can directly generalize to new unseen scenarios and perform novel view synthesis with as few as two source views. The key to our approach lies in explicitly modeled correspondence matching information, providing geometry priors for predicting NeRF color and density for volume rendering. The explicit correspondence matching is quantified with the cosine similarity between image features sampled at the 2D projections of a 3D point on different views, providing reliable cues about surface geometry. Unlike previous methods where image features are extracted independently for each view, we model cross-view interactions via Transformer cross-attention, which greatly improves feature matching quality.
</details>

[📃 Paper](https://arxiv.org/abs/2304.12294) | [⌨️ Code](https://github.com/donydchen/matchnerf)

---

#### ContraNeRF ![](https://img.shields.io/badge/2023-ICCV-yellow)
**Authors**: Gregor Köhler, Nassir Navab, Benjamin Busam

<details span>
<summary><b>Abstract</b></summary>
Although many recent works have investigated generalizable NeRF-based novel view synthesis for unseen scenes, they seldom consider the synthetic-to-real generalization, which is desired in many practical applications. In this work, we first investigate the effects of synthetic data in synthetic-to-real novel view synthesis and surprisingly observe that models trained with synthetic data tend to produce sharper but less accurate volume densities. For pixels where the volume densities are correct, fine-grained details will be obtained. Otherwise, severe artifacts will be produced. To maintain the advantages of using synthetic data while avoiding its negative effects, we propose to introduce geometry-aware contrastive learning to learn multi-view consistent features with geometric constraints. Meanwhile, we adopt cross-view attention to further enhance the geometry perception of features by querying features across input views. Experiments demonstrate that under the synthetic-to-real setting, our method can render images with higher quality and better fine-grained details, outperforming existing generalizable novel view synthesis methods in terms of PSNR, SSIM, and LPIPS. When trained on real data, our method also achieves state-of-the-art results.
</details>

[📃 Paper](https://arxiv.org/abs/2303.11052)

---

### 3D Volume Feature-Based

#### MVSNeRF ![](https://img.shields.io/badge/2021-ICCV-yellow)
**Authors**: Anpei Chen, Zexiang Xu, Fuqiang Zhao, Xiaoshuai Zhang, Fanbo Xiang, Jingyi Yu, Hao Su

<details span>
<summary><b>Abstract</b></summary>
We present MVSNeRF, a novel neural rendering approach that can efficiently reconstruct neural radiance fields for view synthesis. Unlike prior works on neural radiance fields that consider per-scene optimization on densely captured images, we propose a generic deep neural network that can reconstruct radiance fields from only three nearby input views via fast network inference. Our approach leverages plane-swept cost volumes (widely used in multi-view stereo) for geometry-aware scene reasoning, and combines this with physically based volume rendering for neural radiance field reconstruction. We train our network on real objects in the DTU dataset, and test it on three different datasets to evaluate its effectiveness and generalizability. Our approach can generalize across scenes (even indoor scenes, completely different from our training scenes of objects) and generate realistic view synthesis results using only three input images, significantly outperforming concurrent works on generalizable radiance field reconstruction. Moreover, if dense images are captured, our estimated radiance field representation can be easily fine-tuned; this leads to fast per-scene reconstruction with higher rendering quality and substantially less optimization time than NeRF.
</details>

[📃 Paper](https://arxiv.org/abs/2103.15595) | [🌐 Project Page](https://apchenstu.github.io/mvsnerf/) | [⌨️ Code](https://github.com/apchenstu/mvsnerf)

---

#### GeoNeRF ![](https://img.shields.io/badge/2022-CVPR-green)
**Authors**: Mohammad Mahdi Johari, Yann Lepoittevin, François Fleuret

<details span>
<summary><b>Abstract</b></summary>
We present GeoNeRF, a generalizable photorealistic novel view synthesis method based on neural radiance fields. Our approach consists of two main stages: a geometry reasoner and a renderer. To render a novel view, the geometry reasoner first constructs cascaded cost volumes for each nearby source view. Then, using a Transformer-based attention mechanism and the cascaded cost volumes, the renderer infers geometry and appearance, and renders detailed images via classical volume rendering techniques. This architecture, in particular, allows sophisticated occlusion reasoning, gathering information from consistent source views. Moreover, our method can easily be fine-tuned on a single scene, and renders competitive results with per-scene optimized neural rendering methods with a fraction of computational cost. Experiments show that GeoNeRF outperforms state-of-the-art generalizable neural rendering models on various synthetic and real datasets. Lastly, with a slight modification to the geometry reasoner, we also propose an alternative model that adapts to RGBD images. This model directly exploits the depth information often available thanks to depth sensors.
</details>

[📃 Paper](https://arxiv.org/abs/2111.13539) | [⌨️ Code](https://github.com/idiap/GeoNeRF)

---

#### NeuRay ![](https://img.shields.io/badge/2022-CVPR-green)
**Authors**: Xiaoshuai Zhang, Sai Bi, Kalyan Sunkavalli, Hao Su, Zexiang Xu

<details span>
<summary><b>Abstract</b></summary>
We present a new neural representation, called Neural Ray (NeuRay), for the novel view synthesis task. Recent works construct radiance fields from image features of input views to render novel view images, which enables the generalization to new scenes. However, due to occlusions, a 3D point may be invisible to some input views. On such a 3D point, these generalization methods will include inconsistent image features from invisible views, which interfere with the radiance field construction. To solve this problem, we predict the visibility of 3D points to input views within our NeuRay representation. This visibility enables the radiance field construction to focus on visible image features, which significantly improves its rendering quality. Meanwhile, a novel consistency loss is proposed to refine the visibility in NeuRay when finetuning on a specific scene. Experiments demonstrate that our approach achieves state-of-the-art performance on the novel view synthesis task when generalizing to unseen scenes and outperforms per-scene optimization methods after finetuning.
</details>

[📃 Paper](https://arxiv.org/abs/2107.13421) | [🌐 Project Page](https://liuyuan-pal.github.io/NeuRay/) | [⌨️ Code](https://github.com/liuyuan-pal/NeuRay)

---

#### ENeRF ![](https://img.shields.io/badge/2022-SIGGRAPH-blue)
**Authors**: Haotong Lin, Sida Peng, Zhen Xu, Yunzhi Yan, Qing Shuai, Hujun Bao, Xiaowei Zhou

<details span>
<summary><b>Abstract</b></summary>
This paper aims to tackle the challenge of efficiently producing interactive free-viewpoint videos. Some recent works equip neural radiance fields with image encoders, enabling them to generalize across scenes. When processing dynamic scenes, they can simply treat each video frame as an individual scene and perform novel view synthesis to generate free-viewpoint videos. However, their rendering process is slow and cannot support interactive applications. A major factor is that they sample lots of points in empty space when inferring radiance fields. We propose a novel scene representation, called ENeRF, for the fast creation of interactive free-viewpoint videos. Specifically, given multi-view images at one frame, we first build the cascade cost volume to predict the coarse geometry of the scene. The coarse geometry allows us to sample few points near the scene surface, thereby significantly improving the rendering speed. This process is fully differentiable, enabling us to jointly learn the depth prediction and radiance field networks from RGB images. Experiments on multiple benchmarks show that our approach exhibits competitive performance while being at least 60 times faster than previous generalizable radiance field methods.
</details>

[📃 Paper](https://arxiv.org/abs/2112.01517) | [🌐 Project Page](https://zju3dv.github.io/enerf/) | [⌨️ Code](https://github.com/zju3dv/ENeRF)

---

#### MuRF ![](https://img.shields.io/badge/2024-CVPR-green)
**Authors**: Haofei Xu, Anpei Chen, Yuedong Chen, Christoph Lassner, Zhidong Deng, Andreas Geiger, Marc Pollefeys, Wenjing Bian

<details span>
<summary><b>Abstract</b></summary>
We present Multi-Baseline Radiance Fields (MuRF), a general feed-forward approach to solving sparse view synthesis under multiple different baseline settings (small and large baselines, and different number of input views). To render a target novel view, we discretize the 3D space into planes parallel to the target image plane, and accordingly construct a target view frustum volume. Such a target volume representation is spatially aligned with the target view, which effectively aggregates relevant information from the input views for high-quality rendering. It also facilitates subsequent radiance field regression with a convolutional network thanks to its axis-aligned nature. The 3D context modeled by the convolutional network enables our method to synthesis sharper scene structures than prior works. Our MuRF achieves state-of-the-art performance across multiple different baseline settings and diverse scenarios ranging from simple objects (DTU) to complex indoor and outdoor scenes (RealEstate10K and LLFF). We also show promising zero-shot generalization abilities on the Mip-NeRF 360 dataset, demonstrating the general applicability of MuRF.
</details>

[📃 Paper](https://arxiv.org/abs/2312.04565) | [🌐 Project Page](https://haofeixu.github.io/murf/) | [⌨️ Code](https://github.com/autonomousvision/murf)

---

#### GeFu ![](https://img.shields.io/badge/2024-arXiv-red)
**Authors**: Zeyu Chen, Shijian Lu

<details span>
<summary><b>Abstract</b></summary>
Generalizable NeRF aims to synthesize novel views for unseen scenes. Common practices involve constructing variance-based cost volumes for geometry reconstruction and encoding 3D descriptors for decoding novel views. However, existing methods show limited generalization ability in challenging conditions due to inaccurate geometry, sub-optimal descriptors, and decoding strategies. We address these issues point by point. First, we find the variance-based cost volume exhibits failure patterns as the features of pixels corresponding to the same point can be inconsistent across different views due to occlusions or reflections. We introduce an Adaptive Cost Aggregation (ACA) approach to amplify the contribution of consistent pixel pairs and suppress inconsistent ones. Unlike previous methods that solely fuse 2D features into descriptors, our approach introduces a Spatial-View Aggregator (SVA) to incorporate 3D context into descriptors through spatial and inter-view interaction. When decoding the descriptors, we observe the two existing decoding strategies excel in different areas, which are complementary. A Consistency-Aware Fusion (CAF) strategy is proposed to leverage the advantages of both. We incorporate the above ACA, SVA, and CAF into a coarse-to-fine framework, termed Geometry-aware Reconstruction and Fusion-refined Rendering (GeFu). GeFu attains state-of-the-art performance across multiple datasets.
</details>

[📃 Paper](https://arxiv.org/abs/2404.17528)

---

#### WaveNeRF ![](https://img.shields.io/badge/2023-ICCV-yellow)
**Authors**: Muyu Xu, Fangneng Zhan, Jiahui Zhang, Yingchen Yu, Lingjie Liu, Shijian Lu, Christian Theobalt

<details span>
<summary><b>Abstract</b></summary>
Neural Radiance Field (NeRF) has shown impressive performance in novel view synthesis via implicit scene representation. However, it usually suffers from poor scalability as requiring densely sampled images for each new scene. Several studies have attempted to mitigate this problem by integrating Multi-View Stereo (MVS) technique into NeRF while they still entail a cumbersome fine-tuning process for new scenes. Notably, the rendering quality will drop severely without this fine-tuning process and the errors mainly appear around the high-frequency features. In the light of this observation, we design WaveNeRF, which integrates wavelet frequency decomposition into MVS and NeRF to achieve generalizable yet high-quality synthesis without any per-scene optimization. To preserve high-frequency information when generating 3D feature volumes, WaveNeRF builds Multi-View Stereo in the Wavelet domain by integrating the discrete wavelet transform into the classical cascade MVS, which disentangles high-frequency information explicitly. With that, disentangled frequency features can be injected into classic NeRF via a novel hybrid neural renderer to yield faithful high-frequency details, and an intuitive frequency-guided sampling strategy can be designed to suppress artifacts around high-frequency regions. Extensive experiments over three widely studied benchmarks show that WaveNeRF achieves superior generalizable radiance field modeling when only given three images as input.
</details>

[📃 Paper](https://arxiv.org/abs/2308.04826)

---

### 3D Triplane Feature-Based

#### LRM ![](https://img.shields.io/badge/2023-ICLR-blue)
**Authors**: Yicong Hong, Kai Zhang, Jiuxiang Gu, Sai Bi, Yang Zhou, Difan Liu, Feng Liu, Kalyan Sunkavalli, Trung Bui, Hao Tan

<details span>
<summary><b>Abstract</b></summary>
We propose the first Large Reconstruction Model (LRM) that predicts the 3D model of an object from a single input image within just 5 seconds. In contrast to many previous methods trained on small-scale datasets such as ShapeNet in a category-specific fashion, LRM adopts a highly scalable transformer-based architecture with 500 million learnable parameters to directly predict a neural radiance field (NeRF) from the input image. The model is trained end-to-end on massive multi-view data containing around 1 million objects, including both synthetic renderings from Objaverse and real captures from MVImgNet. This combination of a high-capacity model and large-scale training data empowers the model to be highly generalizable and produce high-quality 3D reconstructions from various testing inputs, including real-world in-the-wild captures and images created by generative models.
</details>

[📃 Paper](https://arxiv.org/abs/2311.04400) | [🌐 Project Page](https://scalei3d.github.io/LRM/)

---

#### Pf-LRM ![](https://img.shields.io/badge/2024-ECCV-yellow)
**Authors**: Peng Wang, Hao Tan, Sai Bi, Yinghao Xu, Fujun Luan, Kalyan Sunkavalli, Wenping Wang, Zexiang Xu, Kai Zhang

<details span>
<summary><b>Abstract</b></summary>
We propose a Pose-Free Large Reconstruction Model (PF-LRM) for reconstructing a 3D object from a few unposed images even with little visual overlap, while simultaneously estimating the relative camera poses in ~1.3 seconds on a single A100 GPU. PF-LRM is a highly scalable method utilizing self-attention blocks to exchange information between 3D object tokens and 2D image tokens; it predicts a coarse point cloud for each view, and then uses a differentiable Perspective-n-Point (PnP) solver to obtain camera poses. When trained on a large amount of multi-view posed data of ~1M objects, PF-LRM shows strong cross-dataset generalization ability, and outperforms baseline methods by a large margin in terms of pose prediction accuracy and 3D reconstruction quality on various unseen evaluation datasets. We also demonstrate the model's applicability in downstream text/image-to-3D tasks with fast feed-forward inference.
</details>

[📃 Paper](https://arxiv.org/abs/2311.12024) | [🌐 Project Page](https://totoro97.github.io/pf-lrm/)

---

#### TripoSR ![](https://img.shields.io/badge/2024-arXiv-red)
**Authors**: Dmitry Tochilkin, David Pankratz, Zexiang Liu, Zixuan Huang, Adam Letts, Yangguang Li, Ding Liang, Christian Laforte, Varun Jampani, Yan-Pei Cao

<details span>
<summary><b>Abstract</b></summary>
This technical report introduces TripoSR, a 3D reconstruction model leveraging transformer architecture for fast feed-forward 3D generation, producing 3D mesh from a single image in under 0.5 seconds. Building upon the LRM network architecture, TripoSR integrates substantial improvements in data processing, model design, and training techniques. Evaluations on public datasets show that TripoSR exhibits superior performance, both quantitatively and qualitatively, compared to other open-source alternatives. Released under the MIT license, TripoSR is intended to empower researchers, developers, and creatives with the latest advancements in 3D generative AI.
</details>

[📃 Paper](https://arxiv.org/abs/2403.02151) | [⌨️ Code](https://github.com/VAST-AI-Research/TripoSR)

---

#### LRM-Zero ![](https://img.shields.io/badge/2024-arXiv-red)
**Authors**: Desai Xie, Sai Bi, Zhixin Shu, Kai Zhang, Zexiang Xu, Yi Zhou, Sören Pirk, Arie Kaufman, Xin Sun, Hao Tan

<details span>
<summary><b>Abstract</b></summary>
We present LRM-Zero, a Large Reconstruction Model (LRM) trained entirely on synthesized 3D data, achieving high-quality sparse-view 3D reconstruction. The core of LRM-Zero is a procedural 3D dataset called Zeroverse, which is automatically synthesized from simple primitive shapes with random texturing and augmentations (e.g., height fields, boolean differences, and wireframes). Unlike previous 3D datasets (e.g., Objaverse) which are often captured or crafted by humans to approximate real 3D data, Zeroverse completely ignores realistic global semantics but is rich in complex geometric and texture details that are locally similar to or even more intricate than real objects.
</details>

[📃 Paper](https://arxiv.org/abs/2406.09371) | [🌐 Project Page](https://desaixie.github.io/lrm-zero/)

---

#### Instant3D ![](https://img.shields.io/badge/2023-ICLR-blue)
**Authors**: Jiahao Li, Hao Tan, Kai Zhang, Zexiang Xu, Feng Liu, Yanqing Jing, Sai Bi, Kalyan Sunkavalli, Mike Zheng Shou, Hao Su

<details span>
<summary><b>Abstract</b></summary>
Text-to-3D with diffusion models has achieved remarkable progress in recent years. However, existing methods either rely on score distillation-based optimization which suffers from slow inference, low diversity, and Janus problems, or are feed-forward methods that generate low-quality results due to the scarcity of 3D training data. We propose Instant3D, a novel method that generates high-quality and diverse 3D assets from text prompts in a feed-forward manner. We adopt a two-stage paradigm: first generating a sparse set of four structured and consistent views from text in one shot with a fine-tuned 2D text-to-image diffusion model, then directly regressing the NeRF from the generated images with a novel transformer-based sparse-view reconstructor. Through extensive experiments, we demonstrate that Instant3D can generate diverse 3D assets of high visual quality within 20 seconds, which is two orders of magnitude faster than previous optimization-based methods.
</details>

[📃 Paper](https://arxiv.org/abs/2311.06214) | [🌐 Project Page](https://jiahao.ai/instant3d/)

---

#### DMV3D ![](https://img.shields.io/badge/2024-ICLR-blue)
**Authors**: Yinghao Xu, Hao Tan, Fujun Luan, Sai Bi, Peng Wang, Jiahao Li, Zifan Shi, Kalyan Sunkavalli, Gordon Wetzstein, Zexiang Xu, Kai Zhang

<details span>
<summary><b>Abstract</b></summary>
We propose DMV3D, a novel 3D generation approach that uses a transformer-based 3D large reconstruction model to denoise multi-view diffusion. Our reconstruction model incorporates a triplane NeRF representation and can denoise noisy multi-view images via NeRF reconstruction and rendering, achieving single-stage 3D generation in ~30 seconds on a single A100 GPU. DMV3D is trained on large-scale multi-view image datasets of highly diverse objects using only image reconstruction losses, without accessing 3D assets. We demonstrate state-of-the-art results for the single-image reconstruction problem where probabilistic modeling of unseen object parts is required, and also show high-quality text-to-3D generation results outperforming previous 3D diffusion models.
</details>

[📃 Paper](https://arxiv.org/abs/2311.09217) | [🌐 Project Page](https://justimyhxu.github.io/projects/dmv3d/)

---

### Other NeRF Methods

#### VisionNeRF ![](https://img.shields.io/badge/2023-CVPR-green)
**Authors**: Jianfeng Yan, Zekun Hao, Hongyi Xu, Sergi Tulyakov, Jun Gao, Wenlong Liao, Stefano Petrangeli, Haoxiang Li, Huaizu Jiang

<details span>
<summary><b>Abstract</b></summary>
Although neural radiance fields (NeRF) have shown impressive advances for novel view synthesis, most methods typically require multiple input images of the same scene with accurate camera poses. In this work, we seek to substantially reduce the inputs to a single unposed image. Existing approaches condition on local image features to reconstruct a 3D object, but often render blurry predictions at viewpoints that are far away from the source view. To address this issue, we propose to leverage both the global and local features to form an expressive 3D representation. The global features are learned from a vision transformer, while the local features are extracted from a 2D convolutional network. To synthesize a novel view, we train a multilayer perceptron (MLP) network conditioned on the learned 3D representation to perform volume rendering. This novel 3D representation allows the network to reconstruct unseen regions without enforcing constraints like symmetry or canonical coordinate systems. Our method can render novel views from only a single input image and generalize across multiple object categories using a single model. Quantitative and qualitative evaluations demonstrate that the proposed method achieves state-of-the-art performance and renders richer details than existing approaches.
</details>

[📃 Paper](https://arxiv.org/abs/2207.05736)

---

#### MINE ![](https://img.shields.io/badge/2021-ICCV-yellow)
**Authors**: Jiaxin Li, Zijian Feng, Qi She, Henghui Ding, Changhu Wang, Gim Hee Lee

<details span>
<summary><b>Abstract</b></summary>
In this paper, we propose MINE to perform novel view synthesis and depth estimation via dense 3D reconstruction from a single image. Our approach is a continuous depth generalization of the Multiplane Images (MPI) by introducing the NEural radiance fields (NeRF). Given a single image as input, MINE predicts a 4-channel image (RGB and volume density) at arbitrary depth values to jointly reconstruct the camera frustum and fill in occluded contents. The reconstructed and inpainted frustum can then be easily rendered into novel RGB or depth views using differentiable rendering. Extensive experiments on RealEstate10K, KITTI and Flowers Light Fields show that our MINE outperforms state-of-the-art by a large margin in novel view synthesis. We also achieve competitive results in depth estimation on iBims-1 and NYU-v2 without annotated depth supervision.
</details>

[📃 Paper](https://arxiv.org/abs/2103.14910) | [⌨️ Code](https://github.com/vincentfung13/MINE)

---

## Pointmap-Based Methods

#### DUSt3R ![](https://img.shields.io/badge/2024-CVPR-green)
**Authors**: Shuzhe Wang, Vincent Leroy, Yohann Cabon, Boris Chidlovskii, Jerome Revaud

<details span>
<summary><b>Abstract</b></summary>
Multi-view stereo reconstruction (MVS) in the wild requires first estimating camera parameters, e.g., intrinsic and extrinsic parameters. These are usually tedious and cumbersome to obtain, yet they are mandatory to triangulate corresponding pixels in 3D space, which is the core of all best-performing MVS algorithms. In this work, we introduce DUSt3R, a radically novel paradigm for Dense and Unconstrained Stereo 3D Reconstruction of arbitrary image collections, operating without prior information about camera calibration nor viewpoint poses. We cast the pairwise reconstruction problem as a regression of pointmaps, relaxing the hard constraints of usual projective camera models, and show that this formulation smoothly unifies the monocular and binocular reconstruction cases. In cases where more than two images are provided, we further propose a simple yet effective global alignment strategy that expresses all pairwise pointmaps in a common reference frame.
</details>

[📃 Paper](https://arxiv.org/abs/2312.14132) | [🌐 Project Page](https://dust3r.europe.naverlabs.com/) | [⌨️ Code](https://github.com/naver/dust3r)

---

#### MASt3R ![](https://img.shields.io/badge/2024-ECCV-yellow)
**Authors**: Vincent Leroy, Yohann Cabon, Jérôme Revaud

<details span>
<summary><b>Abstract</b></summary>
Image Matching is a core component of all best-performing algorithms and pipelines in 3D vision. Yet despite matching being fundamentally a 3D problem, intrinsically linked to camera pose and scene geometry, it is typically treated as a 2D problem. We propose to cast matching as a 3D task with DUSt3R, a recent and powerful 3D reconstruction framework based on Transformers. Based on pointmaps regression, this method displayed impressive robustness in matching views with extreme viewpoint changes, yet with limited accuracy. The goal is to improve the matching capabilities of such an approach while preserving its robustness. We propose to augment the DUSt3R network with a new head that outputs dense local features, trained with an additional matching loss.
</details>

[📃 Paper](https://arxiv.org/abs/2406.09756) | [🌐 Project Page](https://europe.naverlabs.com/blog/mast3r-matching-and-stereo-3d-reconstruction/) | [⌨️ Code](https://github.com/naver/mast3r)

---

#### Fast3R ![](https://img.shields.io/badge/2025-CVPR-brightgreen)
**Authors**: Jianing Yang, Alexander Sax, Kevin J. Liang, Mikael Henaff, Hao Tang, Ang Cao, Joyce Chai, Franziska Meier, Matt Feiszli

<details span>
<summary><b>Abstract</b></summary>
Multi-view 3D reconstruction remains a core challenge in computer vision, particularly in applications requiring accurate and scalable representations across diverse perspectives. Current leading methods such as DUSt3R employ a fundamentally pairwise approach, processing images in pairs and necessitating costly global alignment procedures to reconstruct from multiple views. We propose Fast3R (Fast 3D Reconstruction), a novel multi-view generalization to DUSt3R that achieves efficient and scalable 3D reconstruction by processing many views in parallel. Fast3R's Transformer-based architecture forwards N images in a single forward pass, bypassing the need for iterative alignment. Through extensive experiments on camera pose estimation and 3D reconstruction, Fast3R demonstrates competitive to superior performance compared to DUSt3R and MASt3R, while significantly reducing inference time for multi-view inputs.
</details>

[📃 Paper](https://arxiv.org/abs/2501.13928) | [🌐 Project Page](https://fast3r-3d.github.io/) | [⌨️ Code](https://github.com/facebookresearch/fast3r)

---

#### MV-DUSt3R+ ![](https://img.shields.io/badge/2024-arXiv-red)
**Authors**: Shuzhe Wang, Vincent Leroy, Yohann Cabon, Boris Chidlovskii, Jerome Revaud

<details span>
<summary><b>Abstract</b></summary>
Recent sparse multi-view scene reconstruction advances like DUSt3R and MASt3R no longer require camera calibration and camera pose estimation. However, they only process a pair of views at a time to infer pixel-aligned pointmaps. When dealing with more than two views, a combinatorial number of error-prone pairwise reconstructions are usually followed by an expensive global optimization, which often fails to rectify the pairwise reconstruction errors. To handle more views, reduce errors, and improve inference time, we propose the fast single-stage feed-forward network MV-DUSt3R. At its core are multi-view decoder blocks which exchange information across any number of views while considering one reference view. To make the method robust to reference view selection, we further propose MV-DUSt3R+, which employs cross-reference-view blocks to fuse information across different reference view choices. Extensive experiments on pose estimation and scene reconstruction demonstrate that MV-DUSt3R+ outperforms existing methods and can reconstruct scenes from sparse views in 2 seconds.
</details>

[📃 Paper](https://arxiv.org/abs/2412.06974) | [🌐 Project Page](https://mv-dust3r.github.io/) | [⌨️ Code](https://github.com/facebookresearch/mvdust3r)

---

#### SLAM3R ![](https://img.shields.io/badge/2025-arXiv-red)
**Authors**: Xu Yan, Zhiheng Li, Binbin Xu, Xin Chen, Haomin Liu, Guofeng Zhang, Ronghui Zhan, Hujun Bao

<details span>
<summary><b>Abstract</b></summary>
In this paper, we introduce SLAM3R, a novel and effective system for real-time, high-quality, dense 3D reconstruction using RGB videos. SLAM3R provides an end-to-end solution by seamlessly integrating local 3D reconstruction and global coordinate registration through feed-forward neural networks. Given an input video, the system first converts it into overlapping clips using a sliding window mechanism. Unlike traditional pose optimization-based methods, SLAM3R directly regresses 3D pointmaps from RGB images in each window and progressively aligns and deforms these local pointmaps to create a globally consistent scene reconstruction - all without explicitly solving any camera parameters. Experiments across datasets consistently show that SLAM3R achieves state-of-the-art reconstruction accuracy and completeness while maintaining real-time performance at 20+ FPS.
</details>

[📃 Paper](https://arxiv.org/abs/2412.09401) | [⌨️ Code](https://github.com/PKU-VCL-3DV/SLAM3R)

---

#### Spann3R ![](https://img.shields.io/badge/2024-NeurIPS-blue)
**Authors**: Hengyi Wang, Lourdes Agapito

<details span>
<summary><b>Abstract</b></summary>
We present Spann3R, a novel approach for dense 3D reconstruction from ordered or unordered image collections. Built on the DUSt3R paradigm, Spann3R uses a transformer-based architecture to directly regress pointmaps from images without any prior knowledge of the scene or camera parameters. Unlike DUSt3R, which predicts per image-pair pointmaps each expressed in its local coordinate frame, Spann3R can predict per-image pointmaps expressed in a global coordinate system, thus eliminating the need for optimization-based global alignment. The key idea of Spann3R is to manage an external spatial memory that learns to keep track of all previous relevant 3D information. Spann3R then queries this spatial memory to predict the 3D structure of the next frame in a global coordinate system. Taking advantage of DUSt3R's pre-trained weights and further fine-tuning on a subset of datasets, Spann3R shows competitive performance and generalization ability on various unseen datasets and can reconstruct 3D scenes in real-time.
</details>

[📃 Paper](https://arxiv.org/abs/2408.16061) | [🌐 Project Page](https://hengyiwang.github.io/projects/spanner) | [⌨️ Code](https://github.com/HengyiWang/spann3r)

---

#### MUSt3R ![](https://img.shields.io/badge/2025-arXiv-red)
**Authors**: Yohann Cabon, Lucas Stoffl, Leonid Antsfeld, Gabriela Csurka, Boris Chidlovskii, Jerome Revaud, Philippe Weinzaepfel

<details span>
<summary><b>Abstract</b></summary>
DUSt3R introduced a novel paradigm in geometric computer vision by proposing a model that can provide dense and unconstrained Stereo 3D Reconstruction of arbitrary image collections with no prior information about camera calibration nor viewpoint poses. However, DUSt3R processes image pairs, regressing local 3D reconstructions that need to be aligned in a global coordinate system. The number of pairs, growing quadratically, is an inherent limitation that becomes especially concerning for robust and fast optimization in the case of large image collections. In this paper, we propose an extension of DUSt3R from pairs to multiple views. We propose a Multi-view Network for Stereo 3D Reconstruction (MUSt3R), which modifies the DUSt3R architecture by making it symmetric and extending it to directly predict 3D structure for all views in a common coordinate frame. MUSt3R can process hundreds of views in a single forward pass and, unlike DUSt3R, does not require a global alignment step. Extensive experiments demonstrate that MUSt3R achieves state-of-the-art performance on various benchmarks.
</details>

[📃 Paper](https://arxiv.org/abs/2503.01661) | [⌨️ Code](https://github.com/naver/must3r)

---

#### CUT3R ![](https://img.shields.io/badge/2025-CVPR-brightgreen)
**Authors**: Bingkun Luo, Zhengdi Liu, Hengyi Wang, Lourdes Agapito, Toby Breckon

<details span>
<summary><b>Abstract</b></summary>
We present a unified framework capable of solving a broad range of 3D tasks. Our approach features a stateful recurrent model that continuously updates its state representation with each new observation. Given a stream of images, this evolving state can be used to generate metric-scale pointmaps (per-pixel 3D points) for each new input in an online fashion. These pointmaps reside within a common coordinate system, and can be accumulated into a coherent, dense scene reconstruction that updates as new images arrive. Our model, called CUT3R (Continuous Updating Transformer for 3D Reconstruction), captures rich priors of real-world scenes: not only can it predict accurate pointmaps from image observations, but it can also infer unseen regions of the scene by probing at virtual, unobserved views. Our method is simple yet highly flexible, naturally accepting varying lengths of images that may be either video streams or unordered photo collections, containing both static and dynamic content. We evaluate our method on various 3D/4D tasks and demonstrate competitive or state-of-the-art performance in each.
</details>

[📃 Paper](https://arxiv.org/abs/2501.12387) | [🌐 Project Page](https://cut3r.github.io/) | [⌨️ Code](https://github.com/CUT3R/CUT3R)

---

#### MonST3R ![](https://img.shields.io/badge/2025-ICLR-blue)
**Authors**: Junyi Zhang, Charles Herrmann, Junhwa Hur, Varun Jampani, Trevor Darrell, Forrester Cole, Deqing Sun, Ming-Hsuan Yang

<details span>
<summary><b>Abstract</b></summary>
We present MonST3R (Motion DUSt3R), a geometry-first approach for estimating geometry in the presence of motion in dynamic scenes. MonST3R directly estimates per-timestep pointmaps from dynamic video, adapting DUSt3R's pointmap representation to handle motion without requiring explicit motion modeling. Given a temporal sliding window, it computes pairwise pointmaps for each frame pair alongside optical flow from an off-the-shelf method. These intermediates then serve as inputs to optimize a global point cloud and per-frame camera poses and intrinsics, from which video depth is directly derived. By fine-tuning DUSt3R on limited dynamic scene data, MonST3R achieves robust video depth estimation, camera pose estimation, and dense 4D reconstruction even in complex dynamic environments.
</details>

[📃 Paper](https://arxiv.org/abs/2410.03825) | [🌐 Project Page](https://monst3r-project.github.io/) | [⌨️ Code](https://github.com/Junyi42/monst3r)

---

#### MegaSaM ![](https://img.shields.io/badge/2025-CVPR-brightgreen)
**Authors**: Zhengqi Li, Richard Tucker, Forrester Cole, Qianqian Wang, Linyi Jin, Vickie Ye, Angjoo Kanazawa, Aleksander Holynski, Noah Snavely

<details span>
<summary><b>Abstract</b></summary>
We present MegaSaM, a full pipeline for accurate, fast, and robust camera tracking and depth estimation from in-the-wild monocular videos of dynamic scenes. MegaSaM combines the strengths of several prior approaches: it leverages a deep visual SLAM framework for camera pose estimation with careful modifications to handle real-world dynamic scenes, integrates optical flow for cross-frame consistency, and uses a monocular depth estimation model for initialization. The pipeline first estimates camera poses and low-resolution depth via differentiable bundle adjustment, then refines video depth with flow and depth losses. Extensive experiments demonstrate significantly improved accuracy and robustness over prior work on both synthetic and real dynamic videos.
</details>

[📃 Paper](https://arxiv.org/abs/2412.04463) | [⌨️ Code](https://github.com/mega-sam/mega-sam)

---

#### Easi3R ![](https://img.shields.io/badge/2025-ICCV-yellow)
**Authors**: Xingyu Chen, Yue Chen, Yuliang Xiu, Andreas Geiger, Anpei Chen

<details span>
<summary><b>Abstract</b></summary>
We present Easi3R, a simple training-free approach that adapts DUSt3R for dynamic scene reconstruction. Rather than fine-tuning on dynamic data, Easi3R discovers that the cross-attention maps in DUSt3R's decoder inherently encode rich information about camera and object motion. By aggregating these attention maps and applying attention adaptation during inference, Easi3R achieves accurate dynamic region segmentation, camera pose estimation, and 4D dense point map reconstruction at almost no additional cost on top of DUSt3R. Despite requiring no additional training, Easi3R significantly outperforms prior methods that rely on expensive fine-tuning on dynamic datasets, demonstrating the strong latent 4D understanding embedded in pretrained pointmap models.
</details>

[📃 Paper](https://arxiv.org/abs/2503.24391) | [🌐 Project Page](https://easi3r.github.io/) | [⌨️ Code](https://github.com/Inception3D/Easi3R)

---

#### Driv3R ![](https://img.shields.io/badge/2025-arXiv-red)
**Authors**: Yufei Wei, Yifan Lu, Muyu Xu, Jiahui Zhang, Wenzhao Zheng, Shijian Lu

<details span>
<summary><b>Abstract</b></summary>
Realtime 4D reconstruction for dynamic scenes remains a crucial challenge for autonomous driving perception. Most existing methods rely on depth estimation through self-supervision or multi-modality sensor fusion. In this paper, we propose Driv3R, a DUSt3R-based framework that directly regresses per-frame point maps from multi-view image sequences. To achieve streaming dense reconstruction, we maintain a memory pool to reason both spatial relationships across sensors and dynamic temporal contexts to enhance multi-view 3D consistency and temporal integration. Furthermore, we employ a 4D flow predictor to identify moving objects within the scene to direct our network focus more on reconstructing these dynamic regions. Finally, we align all per-frame pointmaps consistently to the world coordinate system in an optimization-free manner. We conduct extensive experiments on the large-scale nuScenes dataset to evaluate the effectiveness of our method. Driv3R outperforms previous frameworks in 4D dynamic scene reconstruction, achieving 15x faster inference speed compared to methods requiring global alignment.
</details>

[📃 Paper](https://arxiv.org/abs/2412.06777) | [⌨️ Code](https://github.com/Driv3R/Driv3R)

---

#### Light3R-SfM ![](https://img.shields.io/badge/2025-CVPR-brightgreen)
**Authors**: Sven Elflein, Qunjie Zhou, Danda Pani Paudel, Laura Leal-Taixé

<details span>
<summary><b>Abstract</b></summary>
We present Light3R-SfM, a feed-forward, end-to-end learnable framework for efficient large-scale Structure-from-Motion (SfM) from unconstrained image collections. Unlike existing SfM solutions that rely on costly matching and global optimization to achieve accurate 3D reconstructions, Light3R-SfM addresses this limitation through a novel latent global alignment module. This module replaces traditional global optimization with a learnable attention mechanism, effectively capturing multi-view constraints across images for robust and precise camera pose estimation. Light3R-SfM constructs a sparse scene graph via retrieval-score-guided shortest path tree to dramatically reduce memory usage and computational overhead compared to the naive approach. Extensive experiments demonstrate that Light3R-SfM achieves competitive accuracy while significantly reducing runtime, making it ideal for 3D reconstruction tasks in real-world applications with a runtime constraint. This work pioneers a data-driven, feed-forward SfM approach, paving the way toward scalable, accurate, and efficient 3D reconstruction in the wild.
</details>

[📃 Paper](https://arxiv.org/abs/2501.14914) | [🌐 Project Page](https://light3r.github.io/)

---

#### MASt3R-SfM ![](https://img.shields.io/badge/2025-CVPR-brightgreen)
**Authors**: Bardienus Pieter Duisterhof, Lojze Zust, Philippe Weinzaepfel, Vincent Leroy, Yohann Cabon, Jerome Revaud

<details span>
<summary><b>Abstract</b></summary>
Structure-from-Motion (SfM), a task aiming at jointly recovering camera poses and 3D geometry of a scene given a set of images, remains a hard problem with still many open challenges despite decades of significant progress. The traditional solution for SfM consists of a complex pipeline of minimal solvers which tends to propagate errors and fails when images do not sufficiently overlap, have too little motion, etc. Recent methods have attempted to revisit this paradigm, but we empirically show that they fall short of fixing these core issues. In this paper, we propose instead to build upon a recently released foundation model for 3D vision that can robustly produce local 3D reconstructions and accurate matches. We introduce a low-memory approach to accurately align these local reconstructions in a global coordinate system. We further show that such foundation models can serve as efficient image retrievers without any overhead, reducing the overall complexity from quadratic to linear. Overall, our novel SfM pipeline is simple, scalable, fast and truly unconstrained, i.e. it can handle any collection of images, ordered or not. Extensive experiments on multiple benchmarks show that our method provides steady performance across diverse settings, especially outperforming existing methods in small- and medium-scale settings.
</details>

[📃 Paper](https://arxiv.org/abs/2409.19152) | [⌨️ Code](https://github.com/naver/mast3r)

---

#### MoGe ![](https://img.shields.io/badge/2025-CVPR-brightgreen)
**Authors**: Ruicheng Wang, Sicheng Xu, Cassie Dai, Jianfeng Xiang, Yu Deng, Xin Tong, Jiaolong Yang

<details span>
<summary><b>Abstract</b></summary>
We present MoGe, a powerful model for recovering 3D geometry from monocular open-domain images. Given a single image, our model directly predicts a 3D point map of the captured scene with an affine-invariant representation, which is agnostic to true global scale and shift. This new representation precludes ambiguous supervision in training and facilitates effective geometry learning. Furthermore, we propose a set of novel global and local geometry supervisions that empower the model to learn high-quality geometry. These include a robust, optimal, and efficient point cloud alignment solver for accurate global shape learning, and a multi-scale local geometry loss promoting precise local geometry supervision. We train our model on a large, mixed dataset and demonstrate strong generalizability and high accuracy, significantly outperforming state-of-the-art methods across all tasks in comprehensive evaluations on diverse unseen datasets.
</details>

[📃 Paper](https://arxiv.org/abs/2410.19115) | [🌐 Project Page](https://wangrc.site/MoGePage/) | [⌨️ Code](https://github.com/microsoft/MoGe)

---

#### Test3R ![](https://img.shields.io/badge/2025-arXiv-red)
**Authors**: Ziwen Yuan, Sicheng Xu, Ruicheng Wang, Jiaolong Yang, Xin Tong, Baining Guo

<details span>
<summary><b>Abstract</b></summary>
Dense matching methods like DUSt3R regress pairwise pointmaps for 3D reconstruction. However, the reliance on pairwise prediction and the limited generalization capability inherently restrict the global geometric consistency. In this work, we introduce Test3R, a surprisingly simple test-time learning technique that significantly boosts geometric accuracy. Using image triplets (I1, I2, I3), Test3R generates reconstructions from pairs (I1, I2) and (I1, I3). The core idea is to optimize the network at test time via a self-supervised objective: maximizing the geometric consistency between these two reconstructions relative to the common image I1. This ensures the model produces cross-pair consistent outputs, regardless of the inputs. Extensive experiments demonstrate that our technique significantly outperforms previous state-of-the-art methods on the 3D reconstruction and multi-view depth estimation tasks. Moreover, it is universally applicable and nearly cost-free, making it easily applied to other models and implemented with minimal test-time training overhead and parameter footprint.
</details>

[📃 Paper](https://arxiv.org/abs/2506.13750)

---

#### AerialMegaDepth ![](https://img.shields.io/badge/2025-CVPR-brightgreen)
**Authors**: Khiem Vuong, Anurag Ghosh, Deva Ramanan, Srinivasa Narasimhan, Shubham Tulsiani

<details span>
<summary><b>Abstract</b></summary>
We explore the task of geometric reconstruction of images captured from a mixture of ground and aerial views. Current state-of-the-art learning-based approaches fail to handle the extreme viewpoint variation between aerial-ground image pairs. Our hypothesis is that the lack of high-quality, co-registered aerial-ground datasets for training is a key reason for this failure. Such data is difficult to assemble precisely because it is difficult to reconstruct in a scalable way. To overcome this challenge, we propose a scalable framework combining pseudo-synthetic renderings from 3D city-wide meshes (e.g., Google Earth) with real, ground-level crowd-sourced images (e.g., MegaDepth). Using this hybrid dataset, we fine-tune several state-of-the-art algorithms and achieve significant improvements on real-world, zero-shot aerial-ground tasks. For example, we observe that baseline DUSt3R localizes fewer than 5% of aerial-ground pairs within 5 degrees of camera rotation error, while fine-tuning with our data raises accuracy to nearly 56%.
</details>

[📃 Paper](https://arxiv.org/abs/2504.13157) | [🌐 Project Page](https://aerial-megadepth.github.io/)

---

#### VGGT ![](https://img.shields.io/badge/2025-CVPR-brightgreen)
**Authors**: Jianyuan Wang, Minghao Chen, Nikita Karaev, Andrea Vedaldi, Christian Rupprecht, David Novotny

<details span>
<summary><b>Abstract</b></summary>
We present VGGT, a feed-forward neural network that directly infers all key 3D attributes of a scene, including camera parameters, point maps, depth maps, and 3D point tracks, from one, a few, or hundreds of its views. This approach is a step forward in 3D computer vision, where models have typically been constrained to and specialized for single tasks. It is also simple and efficient, reconstructing images in under one second, and still outperforming alternatives that require post-processing with visual geometry optimization techniques. The network achieves state-of-the-art results in multiple 3D tasks, including camera parameter estimation, multi-view depth estimation, dense point cloud reconstruction, and 3D point tracking. We also show that using pretrained VGGT as a feature backbone significantly enhances downstream tasks, such as non-rigid point tracking and feed-forward novel view synthesis.
</details>

[📃 Paper](https://arxiv.org/abs/2503.11651) | [🌐 Project Page](https://vggt.github.io/) | [⌨️ Code](https://github.com/facebookresearch/vggt)

---

#### VGGT-Long (Tesseract) ![](https://img.shields.io/badge/2025-arXiv-red)
**Authors**: Peize Deng, Jianyuan Wang, Bokui Shen, Nikita Karaev, Tsun-Yi Yang, David Novotny, Christian Rupprecht, Andrea Vedaldi

<details span>
<summary><b>Abstract</b></summary>
Foundation models for 3D vision have recently demonstrated remarkable capabilities in 3D perception. However, extending these models to large-scale RGB stream 3D reconstruction remains challenging due to memory limitations. In this work, we propose VGGT-Long, a simple yet effective system that pushes the limits of monocular 3D reconstruction to kilometer-scale, unbounded outdoor environments. Our approach addresses the scalability bottlenecks of existing models through a chunk-based processing strategy combined with overlapping alignment and lightweight loop closure optimization. Without requiring camera calibration, depth supervision or model retraining, VGGT-Long achieves trajectory and reconstruction performance comparable to traditional methods. We evaluate our method on KITTI, Waymo, and Virtual KITTI datasets. VGGT-Long not only runs successfully on long RGB sequences where foundation models typically fail, but also produces accurate and consistent geometry across various conditions.
</details>

[📃 Paper](https://arxiv.org/abs/2507.16443) | [🌐 Project Page](https://tesseract-4d.github.io/)

---

## 3D Gaussian Splatting Methods

### Gaussian Map: General

#### Splatter Image ![](https://img.shields.io/badge/2024-CVPR-green)
**Authors**: Stanislaw Szymanowicz, Christian Rupprecht, Andrea Vedaldi

<details span>
<summary><b>Abstract</b></summary>
We introduce Splatter Image, an ultra-efficient approach for monocular 3D object reconstruction. Splatter Image is based on Gaussian Splatting, which allows fast and high-quality reconstruction of 3D scenes from multiple images. We apply Gaussian Splatting to monocular reconstruction by learning a neural network that, at test time, performs reconstruction in a feed-forward manner, at 38 FPS. Our main contribution is the surprisingly simple design of this network, which, using 2D operators, maps the input image to one 3D Gaussian per pixel. The resulting Gaussians thus have the form of an image — the "Splatter Image". We further extend Splatter Image to take several images as input via cross-view attention layers. Compared to prior work, we achieve competitive or better results while being significantly faster and more memory efficient.
</details>

[📃 Paper](https://arxiv.org/abs/2312.13150) | [🌐 Project Page](https://szymanowiczs.github.io/splatter-image) | [⌨️ Code](https://github.com/szymanowiczs/splatter-image)

---

#### GRM ![](https://img.shields.io/badge/2024-ECCV-yellow)
**Authors**: Yinghao Xu, Zifan Shi, Wang Yifan, Hansheng Chen, Ceyuan Yang, Sida Peng, Yujun Shen, Gordon Wetzstein

<details span>
<summary><b>Abstract</b></summary>
We introduce GRM, a large-scale reconstructor capable of recovering a 3D asset from sparse-view images in around 0.1 seconds. GRM is a feed-forward transformer-based model that efficiently incorporates multi-view information to translate the input pixels into pixel-aligned Gaussians, which are unprojected to create a set of densely distributed 3D Gaussians representing a scene. Together, the transformer architecture and the use of 3D Gaussians unlock a scalable and efficient reconstruction framework. Extensive experimental results demonstrate the superiority of the method over alternatives regarding both reconstruction quality and efficiency. We also showcase the potential of GRM in generative tasks — text-to-3D and image-to-3D — by integrating it with existing multi-view diffusion models.
</details>

[📃 Paper](https://arxiv.org/abs/2403.14621) | [🌐 Project Page](https://justimyhxu.github.io/projects/grm/)

---

#### Flash3D ![](https://img.shields.io/badge/2025-3DV-brightgreen)
**Authors**: Stanislaw Szymanowicz, Eldar Insafutdinov, Chuanxia Zheng, Dylan Campbell, João F. Henriques, Christian Rupprecht, Andrea Vedaldi

<details span>
<summary><b>Abstract</b></summary>
We introduce Flash3D, a method for scene reconstruction and novel view synthesis from a single image which is both very generalisable and efficient. For generalisability, we start from a "foundation" model for monocular depth estimation and extend it to a full 3D shape and appearance reconstructor. For efficiency, this extension is based on feed-forward Gaussian Splatting. Specifically, we predict a first layer of 3D Gaussians at the predicted depth, and then add additional layers of Gaussians that are offset in space, allowing the model to complete the reconstruction behind occlusions and truncations. Flash3D is very efficient, trainable on a single GPU in a day. When transferred to unseen datasets like NYU and KITTI, it outperforms competitors by a large margin, even surpassing methods trained specifically on those datasets in some cases.
</details>

[📃 Paper](https://arxiv.org/abs/2406.04343) | [⌨️ Code](https://github.com/eldar/flash3d)

---

#### GS-LRM ![](https://img.shields.io/badge/2024-ECCV-yellow)
**Authors**: Kai Zhang, Sai Bi, Hao Tan, Yuanbo Xiangli, Nanxuan Zhao, Kalyan Sunkavalli, Zexiang Xu

<details span>
<summary><b>Abstract</b></summary>
We present GS-LRM, a scalable large reconstruction model that can predict high-quality 3D Gaussian primitives from 2–4 posed sparse images in 0.23 seconds on a single A100 GPU. Our model features a very simple transformer-based architecture: we patchify input posed images, concatenate multi-view image tokens, and pass them through a sequence of transformer blocks to directly decode per-pixel Gaussian parameters. By operating on posed images, GS-LRM naturally handles scenes with large variations in scale and complexity, reconstructing both unbounded outdoor scenes and bounded indoor environments. We train separate models for objects and scenes, demonstrating state-of-the-art performance in both settings and generalizing well across diverse scene types.
</details>

[📃 Paper](https://arxiv.org/abs/2404.19702) | [🌐 Project Page](https://sai-bi.github.io/project/gs-lrm/)

---

#### eFreeSplat ![](https://img.shields.io/badge/2024-arXiv-red)
**Authors**: Zhiyuan Min, Yawei Luo, Jianwen Sun, Yi Yang

<details span>
<summary><b>Abstract</b></summary>
We develop an Epipolar-Free 3D Gaussian Splatting (eFreeSplat) method for generalizable novel view synthesis across both objects and scenes. Existing pixelSplat and MVSplat methods depend on epipolar priors and cost volumes for cross-view feature matching during encoding, resulting in a speed bottleneck. In contrast, we utilize an Iterative Cross-View Gaussians (ICVG) method that focuses on the target view in an epipolar-free manner to enhance multi-view feature matching. Additionally, we apply a large vision foundation model pretrained ViT as a backbone for Gaussian prediction, leveraging its rich prior knowledge. eFreeSplat achieves superior performance in novel view synthesis from sparse views while maintaining higher efficiency compared to epipolar-based methods.
</details>

[📃 Paper](https://arxiv.org/abs/2410.22817)

---

#### Long-LRM ![](https://img.shields.io/badge/2024-arXiv-red)
**Authors**: Chen Ziwen, Hao Tan, Kai Zhang, Sai Bi, Fujun Luan, Yicong Hong, Li Fuxin, Zexiang Xu

<details span>
<summary><b>Abstract</b></summary>
We present Long-LRM, a generalizable 3D Gaussian splatting model capable of reconstructing a large scene from a long sequence of input images. Long-LRM processes 32 input frames all at once using a scalable architecture that combines Mamba2 blocks with transformer layers. By using efficient Mamba2 blocks for sequence tokens and cross-attention for anchor tokens, our architecture processes long image sequences with relatively small computational resources. Our model achieves high-quality wide-coverage 3D reconstruction from significantly longer image sequences than standard transformer-based methods.
</details>

[📃 Paper](https://arxiv.org/abs/2410.12781)

---

#### FreeSplatter ![](https://img.shields.io/badge/2024-arXiv-red)
**Authors**: Jiale Xu, Shenghua Gao, Ying Shan

<details span>
<summary><b>Abstract</b></summary>
We present FreeSplatter, a feed-forward framework capable of generating pixel-aligned Gaussian primitives from uncalibrated sparse-view images and estimating their camera parameters in a matter of seconds. FreeSplatter is built upon a scalable transformer architecture and trained on extensive collections of high-quality 3D assets. Given sparse-view images without any camera information, FreeSplatter simultaneously reconstructs 3D Gaussian representations and recovers camera poses in a single forward pass, enabling high-quality novel view synthesis for both object-centric and scene-level cases with strong open-world generalization.
</details>

[📃 Paper](https://arxiv.org/abs/2412.09573)

---

#### LGM ![](https://img.shields.io/badge/2024-ECCV-yellow)
**Authors**: Jiaxiang Tang, Zhaoxi Chen, Xiaokang Chen, Tengfei Wang, Gang Zeng, Ziwei Liu

<details span>
<summary><b>Abstract</b></summary>
3D content creation has achieved significant progress in terms of both quality and speed. Although current feed-forward models can produce 3D objects in seconds, their resolution is constrained by the intensive computation required during training. In this paper, we introduce the Large Multi-View Gaussian Model (LGM), a novel framework designed to generate high-resolution 3D models from text prompts or single-view images. Our key insights are two-fold: 1) 3D Representation: We propose multi-view Gaussian features as an efficient yet powerful representation, which can be fused together for differentiable rendering. 2) 3D Backbone: We present an asymmetric U-Net as a high-throughput backbone operating on multi-view images, which can be produced from text or single-view image input by leveraging multi-view diffusion models. Extensive experiments demonstrate the high fidelity and efficiency of our approach, generating 3D objects within 5 seconds at high resolution.
</details>

[📃 Paper](https://arxiv.org/abs/2402.05054) | [🌐 Project Page](https://me.kiui.moe/lgm/) | [⌨️ Code](https://github.com/3DTopia/LGM)

---

#### Wonderland ![](https://img.shields.io/badge/2025-CVPR-brightgreen)
**Authors**: Hanwen Liang, Junli Cao, Vidit Goel, Guocheng Qian, Sergei Korolev, Demetri Terzopoulos, Konstantinos N. Plataniotis, Sergey Tulyakov, Jian Ren

<details span>
<summary><b>Abstract</b></summary>
We present Wonderland, a novel framework for generating large-scale, wide-scope 3D scenes from a single image. Existing methods face constraints such as limited generalization, time-consuming per-scene optimization, and low visual quality in unseen regions. To address these, we propose a pipeline where a camera-guided video diffusion model generates 3D-aware video latents following a specified camera trajectory, which a latent-based large reconstruction model then converts into a 3D Gaussian scene in a feed-forward manner. By operating in latent space, our reconstruction model dramatically reduces memory requirements while capturing rich scene priors from video diffusion, enabling efficient high-quality wide-scope 3D Gaussian scene generation from a single input image.
</details>

[📃 Paper](https://arxiv.org/abs/2412.12091) | [🌐 Project Page](https://snap-research.github.io/wonderland/)

---

### Gaussian Map: Epipolar-Guided

#### PixelSplat ![](https://img.shields.io/badge/2024-CVPR-green)
**Authors**: David Charatan, Sizhe Lester Li, Andrea Tagliasacchi, Vincent Sitzmann

<details span>
<summary><b>Abstract</b></summary>
We introduce pixelSplat, a feed-forward model that learns to reconstruct 3D radiance fields parameterized by 3D Gaussian primitives from pairs of images. Our model features real-time and memory-efficient rendering for scalable training as well as fast 3D reconstruction at inference time. To overcome local minima inherent to sparse and locally supported representations, we predict a dense probability distribution over 3D and sample Gaussian means from that distribution. Sampling is made differentiable via a reparameterization trick, allowing gradients to flow through the Gaussian splatting representation. We also predict a per-scene scale using the epipolar geometry between the two input views, resolving the scale ambiguity in the underlying geometry. We evaluate on RealEstate10k and ACID, achieving state-of-the-art novel view synthesis while being 2.5 orders of magnitude faster at render time than competing approaches.
</details>

[📃 Paper](https://arxiv.org/abs/2312.12337) | [🌐 Project Page](https://davidcharatan.com/pixelsplat/) | [⌨️ Code](https://github.com/dcharatan/pixelsplat)

---

#### LatentSplat ![](https://img.shields.io/badge/2024-ECCV-yellow)
**Authors**: Christopher Wewer, Kevin Raj, Eddy Ilg, Bernt Schiele, Jan Eric Lenssen

<details span>
<summary><b>Abstract</b></summary>
We propose latentSplat, a method to predict semantic Gaussians in a 3D latent space that can be splatted and decoded by a light-weight generative 2D architecture. latentSplat is designed for scalable generalizable 3D reconstruction from two input views, autoencoding the views into variational feature Gaussians from which fast novel view synthesis can be performed, generalizing to both interpolated and extrapolated views. The core of our method are variational 3D Gaussians, which efficiently encode varying uncertainty in a 3D latent space: in observed regions they provide a regressed solution with low variance, while in unobserved areas they acknowledge uncertainty and enable generative completion. Our approach outperforms prior work in quality and generalization while being fast and scalable to high-resolution data.
</details>

[📃 Paper](https://arxiv.org/abs/2403.16292) | [🌐 Project Page](https://geometric-rl.mpi-inf.mpg.de/latentsplat/) | [⌨️ Code](https://github.com/Chrixtar/latentsplat)

---

#### GGRt ![](https://img.shields.io/badge/2024-ECCV-yellow)
**Authors**: Hao Li, Yuanyuan Gao, Dingwen Zhang, Chenming Wu, Yalun Dai, Chen Zhao, Haocheng Feng, Errui Ding, Jingdong Wang, Junwei Han

<details span>
<summary><b>Abstract</b></summary>
We present GGRt, a novel approach to generalizable novel view synthesis that alleviates the need for real camera poses, complexity in processing high-resolution images, and lengthy optimization processes. We design a joint learning framework consisting of an Iterative Pose Optimization Network (IPO-Net) and a Generalizable 3D-Gaussians (G-3DG) model. With this joint learning mechanism, GGRt can inherently estimate robust relative pose information from image observations, eliminating the requirement for camera poses. We further introduce a deferred back-propagation mechanism for high-resolution training and a progressive Gaussian cache module for enhanced efficiency. As the first pose-free generalizable 3D-GS framework, GGRt achieves inference at ≥ 5 FPS and real-time rendering at ≥ 100 FPS, outperforming existing pose-free techniques on the LLFF, KITTI, and Waymo Open datasets.
</details>

[📃 Paper](https://arxiv.org/abs/2403.10147) | [🌐 Project Page](https://3d-aigc.github.io/GGRt/) | [⌨️ Code](https://github.com/lifuguan/GGRt_official)

---

### Gaussian Map: Cost-Volume-Based

#### MVSplat ![](https://img.shields.io/badge/2024-ECCV-yellow)
**Authors**: Yuedong Chen, Haofei Xu, Chuanxia Zheng, Bohan Zhuang, Marc Pollefeys, Andreas Geiger, Tat-Jen Cham, Jianfei Cai

<details span>
<summary><b>Abstract</b></summary>
We introduce MVSplat, an efficient model that, given sparse multi-view images as input, predicts clean feed-forward 3D Gaussians. To accurately localize the Gaussian centers, we build a cost volume representation via plane sweeping, where the cross-view feature similarities stored in the cost volume provide valuable geometry cues for depth estimation. Other Gaussian primitives' parameters are learned jointly with the Gaussian centers while only relying on photometric supervision. We demonstrate the importance of the cost volume representation in learning feed-forward Gaussians via extensive evaluations on large-scale real-world datasets. Compared to the latest state-of-the-art method pixelSplat, MVSplat uses 10× fewer parameters and is more than 2× faster while achieving higher quality.
</details>

[📃 Paper](https://arxiv.org/abs/2403.14627) | [🌐 Project Page](https://donydchen.github.io/mvsplat/) | [⌨️ Code](https://github.com/donydchen/mvsplat)

---

#### MVSGaussian ![](https://img.shields.io/badge/2024-ECCV-yellow)
**Authors**: Tianqi Liu, Guangcong Wang, Shoukang Hu, Liao Shen, Xinyi Ye, Yuhang Zang, Zhiguo Cao, Wei Li, Ziwei Liu

<details span>
<summary><b>Abstract</b></summary>
We present MVSGaussian, a new generalizable 3D Gaussian representation approach derived from Multi-View Stereo (MVS) that can efficiently reconstruct unseen scenes. Specifically, we leverage MVS to encode geometry-aware Gaussian representations and decode them into Gaussian parameters, propose a hybrid Gaussian rendering that integrates efficient volume rendering for novel view synthesis, and introduce a multi-view geometric consistent aggregation strategy for fast per-scene fine-tuning initialization. Compared with previous generalizable NeRF-based methods, MVSGaussian achieves real-time rendering (300+ FPS) with better synthesis quality for each scene, with 13.3× less training computational cost.
</details>

[📃 Paper](https://arxiv.org/abs/2405.12218) | [🌐 Project Page](https://mvsgaussian.github.io/) | [⌨️ Code](https://github.com/TQTQliu/MVSGaussian)

---

#### TranSplat ![](https://img.shields.io/badge/2025-AAAI-blue)
**Authors**: Chuanrui Zhang, Yingshuang Zou, Zhuoling Li, Minmin Yi, Haoqian Wang

<details span>
<summary><b>Abstract</b></summary>
Generalizable 3D Gaussian Splatting methods achieve impressive efficiency in the sparse-view setting but rely heavily on accurate multi-view feature matching, which is particularly challenging in scenes with non-overlapping regions or repetitive patterns. We present TranSplat, which addresses these challenges through a Depth-Aware Deformable Matching Transformer (DDMT) that generates a depth confidence map to guide accurate local feature matching, while leveraging a pretrained monocular depth estimation model as a prior for non-overlapping regions. A Depth Refine U-Net further refines the depth prediction, and pixel-wise 3D Gaussian parameters are decoded for novel view rendering. TranSplat outperforms prior state-of-the-art methods on the RealEstate10K and ACID benchmarks across all metrics with competitive inference speed.
</details>

[📃 Paper](https://arxiv.org/abs/2408.13770) | [🌐 Project Page](https://xingyoujun.github.io/transplat/) | [⌨️ Code](https://github.com/xingyoujun/transplat)

---

#### DepthSplat ![](https://img.shields.io/badge/2024-arXiv-red)
**Authors**: Haofei Xu, Songyou Peng, Fangjinhua Wang, Hermann Blum, Daniel Barath, Andreas Geiger, Marc Pollefeys

<details span>
<summary><b>Abstract</b></summary>
We present DepthSplat, which connects Gaussian splatting and depth estimation to improve the quality of feed-forward 3D Gaussian splatting reconstruction. Our key insight is that pretrained monocular depth features provide strong geometry cues that enhance multi-view stereo cost volume matching. DepthSplat leverages a multi-view depth model integrating these monocular depth features, leading to improved depth estimation and consequently higher-quality Gaussian reconstruction. We conduct extensive experiments on multiple datasets, demonstrating that DepthSplat outperforms previous methods in novel view synthesis quality and cross-dataset generalization.
</details>

[📃 Paper](https://arxiv.org/abs/2410.13862)

---

#### HiSplat ![](https://img.shields.io/badge/2024-arXiv-red)
**Authors**: Shengji Tang, Weicai Ye, Peng Ye, Weihao Lin, Yang Zhou, Tao Chen, Wanli Ouyang

<details span>
<summary><b>Abstract</b></summary>
We introduce HiSplat, a framework for generalizable 3D Gaussian splatting that adopts hierarchical representations to capture both large-scale structures and fine texture details from sparse multi-view images. HiSplat generates hierarchical 3D Gaussians through a coarse-to-fine pipeline: it first establishes an overall scene structure via coarse Gaussian estimation, then refines this with fine-grained Gaussians capturing local texture details, and applies an error compensation mechanism to correct inaccuracies from preceding stages. By decoupling reconstruction into structural and textural components, HiSplat achieves higher quality, particularly in capturing both large-scale geometry and high-frequency details.
</details>

[📃 Paper](https://arxiv.org/abs/2410.06245)

---

#### PanSplat ![](https://img.shields.io/badge/2024-arXiv-red)
**Authors**: Cheng Zhang, Haofei Xu, Qianyi Wu, Camilo Cruz Gambardella, Dinh Phung, Jianfei Cai

<details span>
<summary><b>Abstract</b></summary>
We present PanSplat, a generalizable approach for feed-forward panoramic novel view synthesis using 3D Gaussian Splatting. Inspired by advances in feed-forward perspective reconstruction, PanSplat builds a hierarchical spherical cost volume to efficiently capture geometry from panoramic image pairs. A lightweight Gaussian head then decodes this cost volume into panoramic 3D Gaussians for real-time novel view synthesis at 4K resolution. PanSplat demonstrates significantly better performance compared to perspective-based methods applied to panoramic inputs, achieving high-quality wide-angle scene rendering suitable for real-world applications.
</details>

[📃 Paper](https://arxiv.org/abs/2412.12096)

---

#### MVSplat360 ![](https://img.shields.io/badge/2024-arXiv-red)
**Authors**: Yuedong Chen, Chuanxia Zheng, Haofei Xu, Bohan Zhuang, Andrea Vedaldi, Tat-Jen Cham, Jianfei Cai

<details span>
<summary><b>Abstract</b></summary>
We introduce MVSplat360, a feed-forward approach for 360° novel view synthesis (NVS) from sparse input views. Existing feed-forward 3D Gaussian splatting models are limited to forward-facing or bounded-viewpoint scenes. MVSplat360 addresses this by adapting the MVSplat framework with a video diffusion prior for completing unobserved regions, enabling 360° scene reconstruction and high-quality NVS from just 5 input views. Our model achieves superior performance on 360° scene benchmarks compared to prior generalizable methods.
</details>

[📃 Paper](https://arxiv.org/abs/2411.04924)

---

#### LongSplat ![](https://img.shields.io/badge/2025-arXiv-red)
**Authors**: Guichen Huang, Ruoyu Wang, Xiangjun Gao, Che Sun, Yuwei Wu, Shenghua Gao, Yunde Jia

<details span>
<summary><b>Abstract</b></summary>
We present LongSplat, a framework for online generalizable 3D Gaussian splatting from long-sequence image streams. Existing generalizable 3D Gaussian splatting models typically process a small fixed number of images, making it challenging to scale to long sequences. LongSplat introduces an online updating mechanism that incrementally integrates new observations into a consistent 3D Gaussian representation without storing the full frame history. The approach is evaluated on indoor and outdoor scene benchmarks, demonstrating effective scalability to long-sequence inputs while maintaining high rendering quality.
</details>

[📃 Paper](https://arxiv.org/abs/2507.16144)

---

### Gaussian Map: Pretrained-Model-Based

#### Splatt3R ![](https://img.shields.io/badge/2024-arXiv-red)
**Authors**: Brandon Smart, Chuanxia Zheng, Iro Laina, Victor Adrian Prisacariu

<details span>
<summary><b>Abstract</b></summary>
We introduce Splatt3R, a pose-free, feed-forward method for in-the-wild 3D reconstruction and novel view synthesis from stereo pairs. Splatt3R builds on the large-scale pretrained foundation 3D vision model MASt3R and integrates a Gaussian Splatting decoder head, enabling zero-shot 3D Gaussian splatting from uncalibrated image pairs. Unlike prior methods that rely on known camera parameters or epipolar geometry, Splatt3R directly predicts 3D Gaussians from image pairs in a single forward pass, demonstrating strong zero-shot generalization to diverse real-world scenes without any camera pose information at test time.
</details>

[📃 Paper](https://arxiv.org/abs/2408.13912) | [🌐 Project Page](https://splatt3r.active.vision/) | [⌨️ Code](https://github.com/btsmart/splatt3r)

---

#### NoPoSplat ![](https://img.shields.io/badge/2024-arXiv-red)
**Authors**: Botao Ye, Sifei Liu, Haofei Xu, Xueting Li, Marc Pollefeys, Ming-Hsuan Yang, Songyou Peng

<details span>
<summary><b>Abstract</b></summary>
We introduce NoPoSplat, a feed-forward model capable of reconstructing 3D scenes parameterized by 3D Gaussians from unposed sparse multi-view images. Our model, trained exclusively with photometric loss, achieves competitive or superior performance compared to pose-conditioned methods on cross-dataset generalization. NoPoSplat uses a MASt3R backbone and predicts 3D Gaussians in a canonical coordinate space without requiring ground-truth camera poses or depth as input. We demonstrate that 3D Gaussian reconstruction can be learned from photometric supervision alone, removing the dependency on known camera geometry and making the approach practical for real-world unposed image collections.
</details>

[📃 Paper](https://arxiv.org/abs/2410.24207) | [🌐 Project Page](https://noposplat.github.io/) | [⌨️ Code](https://github.com/cvg/NoPoSplat)

---

#### SmileSplat ![](https://img.shields.io/badge/2024-arXiv-red)
**Authors**: Yanyan Li, Yixin Fang, Federico Tombari, Gim Hee Lee

<details span>
<summary><b>Abstract</b></summary>
We introduce SmileSplat, a generalizable Gaussian splatting framework for unconstrained sparse images. SmileSplat adopts DUSt3R as a backbone to predict dense pointmaps from sparse unconstrained input views, and applies a multi-head Gaussian regression decoder to predict Gaussian surfel attributes. Gaussian surfels offer more stable surface representation than volume Gaussians for unconstrained inputs. Our method achieves high-quality 3D reconstruction and novel view synthesis from sparse unposed images, demonstrating the effectiveness of combining feed-forward pointmap prediction with Gaussian splatting for general-purpose unposed reconstruction.
</details>

[📃 Paper](https://arxiv.org/abs/2411.18072)

---

#### SelfSplat ![](https://img.shields.io/badge/2024-arXiv-red)
**Authors**: Gyeongjin Kang, Jisang Yoo, Jihyeon Park, Seungtae Nam, Hyeonsoo Im, Sangheon Shin, Sangpil Kim, Eunbyung Park

<details span>
<summary><b>Abstract</b></summary>
We propose SelfSplat, a self-supervised generalizable 3D Gaussian splatting model that jointly estimates depth, camera pose, and 3D Gaussian attributes from unconstrained videos without any ground-truth 3D supervision or known camera parameters. SelfSplat unifies Gaussian prediction with self-supervised geometric learning, using photometric consistency across frames as the sole training signal. By jointly learning pose estimation and Gaussian reconstruction, the model achieves better geometric alignment than methods treating these tasks separately, while remaining applicable to uncalibrated in-the-wild video collections.
</details>

[📃 Paper](https://arxiv.org/abs/2411.17190)

---

#### PREF3R ![](https://img.shields.io/badge/2024-arXiv-red)
**Authors**: Zequn Chen, Jiezhi Yang, Heng Yang

<details span>
<summary><b>Abstract</b></summary>
We present PREF3R, a novel pose-free feed-forward 3D Gaussian splatting framework for variable-length image sequences. PREF3R adopts Spann3R as a backbone to leverage its spatial memory network for handling multiview inputs of arbitrary length. This enables scalable pose-free 3D Gaussian reconstruction beyond the pairwise constraints of DUSt3R- and MASt3R-based approaches. We demonstrate that PREF3R achieves high-quality novel view synthesis from unposed image sequences of varying length, without requiring camera calibration or sequential alignment post-processing.
</details>

[📃 Paper](https://arxiv.org/abs/2411.16877)

---

#### Lyra ![](https://img.shields.io/badge/2025-arXiv-red)
**Authors**: Sherwin Bahmani, Tianchang Shen, Jiawei Ren, Jiahui Huang, Yifeng Jiang, Haithem Turki, Andrea Tagliasacchi, David B. Lindell, Zan Gojcic, Sanja Fidler, et al.

<details span>
<summary><b>Abstract</b></summary>
We present Lyra, a generative 3D scene reconstruction framework that transfers the implicit 3D knowledge encoded in video diffusion models into explicit 3D Gaussian Splatting representations via a self-distillation strategy. Lyra trains a 3DGS student decoder using a pretrained camera-controlled video diffusion model as the teacher, eliminating the need for captured multiview real-world data. The self-distillation framework enables the model to leverage rich 3D priors learned by video diffusion models while producing explicit, renderable 3D Gaussian scenes in a feed-forward manner, without per-scene optimization.
</details>

[📃 Paper](https://arxiv.org/abs/2509.19296)

---

### Gaussian Volume

#### LaRa ![](https://img.shields.io/badge/2024-ECCV-yellow)
**Authors**: Anpei Chen, Haofei Xu, Stefano Esposito, Siyu Tang, Andreas Geiger

<details span>
<summary><b>Abstract</b></summary>
Radiance field methods have achieved photorealistic novel view synthesis and geometry reconstruction, but are mostly applied to per-scene optimization or small-baseline settings. While several recent works investigate feed-forward reconstruction with large baselines using transformers, they ignore the local nature of 3D reconstruction. We propose LaRa, which unifies local and global reasoning in transformer layers via Group Attention Layers that divide the volumetric feature space into local groups and apply attention within each group, followed by cross-attention for global information sharing. Our model represents scenes as Gaussian Volumes and, trained for two days on four GPUs, demonstrates high fidelity in reconstructing 360° radiance fields with strong zero-shot and out-of-domain generalization.
</details>

[📃 Paper](https://arxiv.org/abs/2407.04699) | [🌐 Project Page](https://apchenstu.github.io/LaRa/) | [⌨️ Code](https://github.com/autonomousvision/LaRa)

---

#### GaussianCube ![](https://img.shields.io/badge/2024-arXiv-red)
**Authors**: Bowen Zhang, Yiji Cheng, Jiaolong Yang, Chunyu Wang, Feng Zhao, Yansong Tang, Dong Chen, Baining Guo

<details span>
<summary><b>Abstract</b></summary>
We propose GaussianCube, a structured and explicit 3D Gaussian representation designed for generative 3D modeling. Unlike unordered Gaussian point clouds, GaussianCube fits Gaussians into a predefined voxel grid using a differentiable optimal transport algorithm, producing a structured representation amenable to standard 3D generative models such as diffusion models. This structuring enables effective 3D diffusion model training for single-image 3D generation, while maintaining the rendering efficiency of Gaussian Splatting. Experiments demonstrate that GaussianCube enables higher-quality 3D generation with better geometric consistency compared to unstructured Gaussian representations.
</details>

[📃 Paper](https://arxiv.org/abs/2403.19655)

---

#### Triplane-Gaussian (TGS) ![](https://img.shields.io/badge/2024-CVPR-green)
**Authors**: Zi-Xin Zou, Zhipeng Yu, Yuan-Chen Guo, Yangguang Li, Ding Liang, Yan-Pei Cao, Song-Hai Zhang

<details span>
<summary><b>Abstract</b></summary>
Recent advancements in 3D reconstruction from single images have been driven by generative models, but these methods often face limitations due to slow optimization or rendering processes. We introduce TGS (Triplane Gaussian Splatting), a novel 3D reconstruction method from single-view images that employs a hybrid explicit-and-implicit 3D representation by combining triplane features with 3D Gaussian Splatting. TGS uses two transformer-based networks — a point cloud decoder and a triplane decoder — to reconstruct the explicit point cloud and implicit triplane features respectively. Gaussian attributes are decoded from triplane features queried at each point location, enabling fast and high-quality reconstruction in a single forward pass. Both decoders are trained on large-scale 3D datasets, achieving higher quality with faster runtimes compared to prior single-view methods.
</details>

[📃 Paper](https://arxiv.org/abs/2312.09147) | [🌐 Project Page](https://zouzx.github.io/TriplaneGaussian/)

---

#### AGG ![](https://img.shields.io/badge/2024-arXiv-red)
**Authors**: Dejia Xu, Ye Yuan, Morteza Mardani, Sifei Liu, Jiaming Song, Zhangyang Wang, Arash Vahdat

<details span>
<summary><b>Abstract</b></summary>
We introduce Amortized Generative 3D Gaussians (AGG), an amortized single-image-to-3D generation framework using feed-forward 3D Gaussian Splatting. AGG first represents scene textures as a triplane and then decodes 3D Gaussians from triplane-based texture features queried at 3D point locations, enabling efficient amortized inference. Unlike optimization-based approaches that require per-instance optimization, AGG generates 3D Gaussians for unseen images in a single forward pass, enabling rapid 3D object creation from a single image while producing high-quality 3D assets.
</details>

[📃 Paper](https://arxiv.org/abs/2401.04099)

---

#### SCube ![](https://img.shields.io/badge/2024-NeurIPS-blue)
**Authors**: Xuanchi Ren, Yifan Lu, Hanxue Liang, Jay Zhangjie Wu, Huan Ling, Mike Chen, Sanja Fidler, Francis Williams, Jiahui Huang

<details span>
<summary><b>Abstract</b></summary>
We introduce SCube, a novel method for reconstructing large-scale 3D scenes (geometry, appearance, and semantics) from a sparse set of posed images. Our method employs a novel representation called VoxSplat — a set of 3D Gaussians supported on a high-resolution sparse-voxel scaffold — and predicts VoxSplats via a two-stage feed-forward process: a hierarchical voxel latent diffusion model conditioned on input images generates the scene geometry, followed by a feed-forward appearance network that predicts Gaussian attributes within each voxel. From as few as 3 non-overlapping images, SCube generates millions of Gaussians spanning hundreds of meters in 20 seconds, demonstrating state-of-the-art large-scale reconstruction quality on the Waymo driving dataset.
</details>

[📃 Paper](https://arxiv.org/abs/2410.20030) | [🌐 Project Page](https://research.nvidia.com/labs/toronto-ai/scube/) | [⌨️ Code](https://github.com/nv-tlabs/SCube)

---

#### Generative Densification ![](https://img.shields.io/badge/2025-CVPR-brightgreen)
**Authors**: Seungtae Nam, Xiangyu Sun, Gyeongjin Kang, Younggeun Lee, Seungjun Oh, Eunbyung Park

<details span>
<summary><b>Abstract</b></summary>
Generalized feed-forward Gaussian models have achieved significant progress in sparse-view 3D reconstruction but often struggle to represent high-frequency details due to a limited number of Gaussians. We propose Generative Densification, an efficient and generalizable method to densify Gaussians generated by feed-forward models. Unlike the per-scene 3D-GS densification strategy that iteratively splits and clones Gaussian parameters, our method up-samples feature representations from the feed-forward model and generates fine Gaussians in a single forward pass, leveraging embedded prior knowledge for enhanced generalization. Experimental results on object-level and scene-level reconstruction tasks demonstrate that Generative Densification outperforms state-of-the-art approaches with comparable or smaller model sizes, achieving notable improvements in representing fine details.
</details>

[📃 Paper](https://arxiv.org/abs/2412.06234) | [⌨️ Code](https://github.com/stnamjef/GenerativeDensification)

---

#### QuickSplat ![](https://img.shields.io/badge/2025-arXiv-red)
**Authors**: Yueh-Cheng Liu, Lukas Höllein, Matthias Nießner, Angela Dai

<details span>
<summary><b>Abstract</b></summary>
We present QuickSplat, a fast method for feed-forward 3D surface reconstruction using learned Gaussian initialization. QuickSplat learns to predict voxel-level features using neural networks, which are subsequently decoded by MLPs into Gaussian primitives for efficient surface reconstruction. Based on G3R, QuickSplat enables rapid surface reconstruction without slow per-scene optimization by providing well-structured Gaussian initialization, demonstrating competitive reconstruction quality with significantly faster inference than optimization-based methods.
</details>

[📃 Paper](https://arxiv.org/abs/2505.05591)

---

#### AnySplat ![](https://img.shields.io/badge/2025-arXiv-red)
**Authors**: Lihan Jiang, Yucheng Mao, Linning Xu, Tao Lu, Kerui Ren, Yichen Jin, Xudong Xu, Mulin Yu, Jiangmiao Pang, Feng Zhao, et al.

<details span>
<summary><b>Abstract</b></summary>
We present AnySplat, a feed-forward 3D Gaussian splatting method from unconstrained views. AnySplat constructs volumetric Gaussians by voxelizing Gaussian maps predicted from variable numbers of input views into a shared 3D volume, yielding a unified model capable of handling both sparse and dense input configurations without requiring separate models for different view counts. By aggregating per-view Gaussian predictions into a volumetric representation, AnySplat naturally handles the fusion of information from varying numbers of views, achieving state-of-the-art novel view synthesis quality across a range of input configurations.
</details>

[📃 Paper](https://arxiv.org/abs/2505.23716)

---

## Other 3D Representations

### Mesh-Based Methods

#### Pixel2Mesh ![](https://img.shields.io/badge/2018-ECCV-yellow)
**Authors**: Nanyang Wang, Yinda Zhang, Zhuwen Li, Yanwei Fu, Wei Liu, Yu-Gang Jiang

<details span>
<summary><b>Abstract</b></summary>
We propose an end-to-end deep learning architecture that produces a 3D shape in triangular mesh from a single color image. We adopt a graph-based convolutional neural network that deforms an ellipsoid mesh to the target shape in a coarse-to-fine manner. The network extracts image features with a pretrained VGG network and updates the mesh using graph convolutions that incorporate both local and global shape context. The proposed method achieves state-of-the-art performance on the ShapeNet benchmark, producing smooth and accurate meshes in a single feed-forward pass.
</details>

[📃 Paper](https://arxiv.org/abs/1804.01654) | [⌨️ Code](https://github.com/nywang16/Pixel2Mesh)

---

#### Mesh R-CNN ![](https://img.shields.io/badge/2019-ICCV-yellow)
**Authors**: Georgia Gkioxari, Jitendra Malik, Justin Johnson

<details span>
<summary><b>Abstract</b></summary>
Real-world objects have 3D shape, but existing methods for 3D shape prediction are restricted to artificial settings with no background or to specific object categories. We propose Mesh R-CNN, an architecture that can detect objects in real-world images and predict a triangle mesh giving the 3D shape of each detected object. Mesh R-CNN augments Mask R-CNN with a mesh prediction branch that first generates a coarse voxel representation then refines it into a mesh through a series of graph convolution operations, enabling 3D shape prediction directly from in-the-wild images.
</details>

[📃 Paper](https://arxiv.org/abs/1906.02739)

---

#### One-2-3-45 ![](https://img.shields.io/badge/2023-NeurIPS-blue)
**Authors**: Minghua Liu, Chao Xu, Haian Jin, Linghao Chen, Mukund Varma T, Zexiang Xu, Hao Su

<details span>
<summary><b>Abstract</b></summary>
Single image 3D reconstruction is an important but challenging task that requires extensive knowledge of our natural world. Many existing methods solve this problem by optimizing a neural radiance field under the guidance of 2D diffusion models but suffer from lengthy optimization time, 3D inconsistency results, and poor geometry. In this work, we propose a novel single-image-to-3D pipeline by leveraging the output of the multi-view diffusion model Zero123. Our method eliminates the need for per-shape optimization and reconstructs a 3D mesh in 45 seconds given only a single image, by using multi-view images generated by Zero123 as input to a multi-view reconstruction model.
</details>

[📃 Paper](https://arxiv.org/abs/2306.16928) | [⌨️ Code](https://github.com/One-2-3-45/One-2-3-45)

---

#### One-2-3-45++ ![](https://img.shields.io/badge/2024-CVPR-green)
**Authors**: Minghua Liu, Ruoxi Shi, Linghao Chen, Zhuoyang Zhang, Chao Xu, Xinyue Wei, Hansheng Chen, Chong Zeng, Jiayuan Gu, Hao Su

<details span>
<summary><b>Abstract</b></summary>
Single image 3D reconstruction aims to efficiently generate high-quality 3D content from a single image. While recent methods based on Score Distillation Sampling (SDS) or 2D diffusion models have shown promising results, they are limited by long optimization times or view inconsistencies. This paper presents One-2-3-45++, which significantly improves the quality and consistency of 3D reconstruction by introducing a novel multi-view generation approach that directly generates multi-view consistent images from a single image and uses a 3D diffusion model to reconstruct a textured mesh in less than one minute, outperforming prior methods in both speed and quality.
</details>

[📃 Paper](https://arxiv.org/abs/2311.07885) | [🌐 Project Page](https://sudo-ai-3d.github.io/One2345plus_page/)

---

#### Wonder3D ![](https://img.shields.io/badge/2024-CVPR-green)
**Authors**: Xiaoxiao Long, Yuan-Chen Guo, Cheng Lin, Yuan Liu, Zhiyang Dou, Lingjie Liu, Yuexin Ma, Song-Hai Zhang, Marc Habermann, Christian Theobalt, et al.

<details span>
<summary><b>Abstract</b></summary>
We introduce Wonder3D, a novel method for efficiently generating high-fidelity textured 3D meshes from single-view images. To holistically improve the quality, consistency, and efficiency of image-to-3D tasks, Wonder3D employs a cross-domain diffusion model to generate multi-view normal maps and corresponding color images simultaneously. These cross-domain outputs ensure coherent 3D shapes and appearances across different views, which are then fused into textured 3D meshes using a geometry-aware normal fusion method. Wonder3D achieves high-quality 3D reconstruction in about 2–3 minutes.
</details>

[📃 Paper](https://arxiv.org/abs/2310.15008) | [🌐 Project Page](https://xxlong.site/Wonder3D/) | [⌨️ Code](https://github.com/xxlong0/Wonder3D)

---

#### Unique3D ![](https://img.shields.io/badge/2024-NeurIPS-blue)
**Authors**: Kailu Wu, Fangfu Liu, Zhihan Cai, Runjie Yan, Hanyang Wang, Yating Hu, Yueqi Duan, Kaisheng Ma

<details span>
<summary><b>Abstract</b></summary>
In this work, we introduce Unique3D, a novel image-to-3D framework for efficiently generating high-quality 3D meshes from single-view images, featuring state-of-the-art generation quality and strong generalizability. Previous methods suffer from multi-view inconsistency and low-quality meshes. Unique3D addresses these problems by introducing a multi-level upscale-then-reconstruct strategy: a multi-view diffusion model first generates multi-view images and normal maps with high consistency, which are then used by a coarse-to-fine reconstruction pipeline to produce high-fidelity textured meshes.
</details>

[📃 Paper](https://arxiv.org/abs/2405.20343) | [🌐 Project Page](https://wukailu.github.io/Unique3D/) | [⌨️ Code](https://github.com/AiuniAI/Unique3D)

---

#### MeshLRM ![](https://img.shields.io/badge/2024-arXiv-red)
**Authors**: Xinyue Wei, Kai Zhang, Sai Bi, Hao Tan, Fujun Luan, Valentin Deschaintre, Kalyan Sunkavalli, Hao Su, Zexiang Xu

<details span>
<summary><b>Abstract</b></summary>
We propose MeshLRM, a novel LRM-based approach that can reconstruct a high-quality mesh from merely four input images in less than one second. Different from previous large reconstruction models that focus on NeRF-based representation, MeshLRM incorporates differentiable mesh extraction and rendering into the LRM framework, enabling end-to-end mesh optimization with both reconstruction and perceptual losses. The resulting mesh is of high quality with detailed textures, and can be directly used in 3D graphics applications without further post-processing.
</details>

[📃 Paper](https://arxiv.org/abs/2404.12385)

---

#### InstantMesh ![](https://img.shields.io/badge/2024-arXiv-red)
**Authors**: Jiale Xu, Weihao Cheng, Yiming Gao, Xintao Wang, Shenghua Gao, Ying Shan

<details span>
<summary><b>Abstract</b></summary>
We present InstantMesh, a practical framework for generating sparse-view, high-quality 3D meshes from a single image within 10 seconds. By synergizing the multi-view image generation capabilities of a state-of-the-art multi-view diffusion model and the powerful reconstruction capabilities of a large reconstruction model (LRM) based on a multiplane representation, InstantMesh is able to create diverse 3D assets with high quality, both in terms of geometry and texture. Experiments on publicly available datasets demonstrate that InstantMesh outperforms existing baseline methods in terms of both reconstruction quality and generation diversity.
</details>

[📃 Paper](https://arxiv.org/abs/2404.07191)

---

#### MeshFormer ![](https://img.shields.io/badge/2024-NeurIPS-blue)
**Authors**: Minghua Liu, Chong Zeng, Xinyue Wei, Ruoxi Shi, Linghao Chen, Chao Xu, Mengqi Zhang, Zhaoning Wang, Xiaoshuai Zhang, Isabella Liu, et al.

<details span>
<summary><b>Abstract</b></summary>
Open-world 3D reconstruction models have recently garnered significant attention. However, without sufficient 3D inductive bias, existing methods typically entail expensive training costs and struggle to extract high-quality 3D meshes. In this work, we introduce MeshFormer, a sparse-view reconstruction model that explicitly leverages 3D native structure, input guidance, and training supervision. By incorporating sparse 3D convolutions and integrating 3D attention with 2D attention, MeshFormer can efficiently process high-resolution sparse voxel representations with 3D structural priors. Combined with surface-rendering-based supervision, MeshFormer can generate detailed and high-quality meshes directly without the need for complex post-processing.
</details>

[📃 Paper](https://arxiv.org/abs/2408.10198)

---

#### MeshGPT ![](https://img.shields.io/badge/2024-CVPR-green)
**Authors**: Yawar Siddiqui, Antonio Alliegro, Alexey Artemov, Tatiana Tommasi, Daniele Sirigatti, Vladislav Rosov, Angela Dai, Matthias Nießner

<details span>
<summary><b>Abstract</b></summary>
We introduce MeshGPT, a new approach for generating triangle meshes that reflects the language of 3D shapes as sequences of triangles. Inspired by recent successful applications of large language models, we adopt a two-stage approach: first learning a vocabulary of triangle sequences using graph neural networks and a VQ-VAE, then training an autoregressive transformer to generate new meshes based on this vocabulary. MeshGPT can generate compact, coherent 3D shapes as triangle meshes that are directly usable in standard 3D applications without post-processing.
</details>

[📃 Paper](https://arxiv.org/abs/2311.15475) | [🌐 Project Page](https://nihalsid.github.io/mesh-gpt/) | [⌨️ Code](https://github.com/audi/MeshGPT)

---

#### MeshXL ![](https://img.shields.io/badge/2024-NeurIPS-blue)
**Authors**: Sijin Chen, Xin Chen, Anqi Pang, Xianfang Zeng, Wei Cheng, Yijun Fu, Fukun Yin, Billzb Wang, Jingyi Yu, Gang Yu, et al.

<details span>
<summary><b>Abstract</b></summary>
The polygon mesh representation of 3D data is both efficient and powerful, yet challenging for deep learning due to its irregular structure. In this work, we introduce MeshXL, a family of generative pre-trained autoregressive models for 3D mesh generation, built upon a novel neural coordinate field representation that encodes each triangle as a compact sequence of neural coordinates. This approach enables standard sequence modeling techniques to generate 3D polygon meshes of arbitrary shapes, scaling to large model sizes and diverse datasets as a scalable 3D generative foundation model.
</details>

[📃 Paper](https://arxiv.org/abs/2405.20853) | [🌐 Project Page](https://meshxl.github.io/) | [⌨️ Code](https://github.com/OpenMeshLab/MeshXL)

---

#### MeshAnything ![](https://img.shields.io/badge/2025-ICLR-blue)
**Authors**: Yiwen Chen, Tong He, Di Huang, Weicai Ye, Sijin Chen, Jiaxiang Tang, Xin Chen, Zhongang Cai, Lei Yang, Gang Yu, et al.

<details span>
<summary><b>Abstract</b></summary>
We introduce MeshAnything, a model that treats mesh generation as a language modeling problem, producing artist-created meshes conditioned on given shapes. Previous methods for 3D generation often produce meshes with excessive faces and irregular topology, limiting their usability. MeshAnything uses an autoregressive transformer to generate efficient, structured meshes aligned with an input point cloud representation, enabling the generation of meshes that can be directly used in professional 3D applications. Extensive experiments demonstrate that MeshAnything produces high-quality meshes competitive with manual artist creation across diverse shape categories.
</details>

[📃 Paper](https://arxiv.org/abs/2406.10163) | [🌐 Project Page](https://buaacyw.github.io/mesh-anything/) | [⌨️ Code](https://github.com/buaacyw/MeshAnything)

---

### Occupancy-Based Methods

#### Any-Shot GIN ![](https://img.shields.io/badge/2022-3DV-brightgreen)
**Authors**: Yongqin Xian, Julian Chibane, Bharat Lal Bhatnagar, Bernt Schiele, Zeynep Akata, Gerard Pons-Moll

<details span>
<summary><b>Abstract</b></summary>
We tackle the problem of generalizing implicit shape reconstruction networks to novel, unseen object categories given only a small number of examples at test time. Our method, Any-Shot GIN, introduces a meta-learning strategy that trains an implicit network to rapidly adapt its learned prior to new shape classes with as few as one example. By conditioning the shape network on class-level feature prototypes, our approach can reconstruct 3D occupancy of novel categories without retraining, enabling genuine any-shot 3D shape reconstruction across diverse object classes.
</details>

[📃 Paper](https://arxiv.org/abs/2204.02684)

---

#### MCC ![](https://img.shields.io/badge/2023-CVPR-green)
**Authors**: Chao-Yuan Wu, Justin Johnson, Jitendra Malik, Christoph Feichtenhofer, Georgia Gkioxari

<details span>
<summary><b>Abstract</b></summary>
We propose Multiview Compressive Coding (MCC), a self-supervised approach for 3D object reconstruction from a single RGB-D image. MCC trains a model to predict the 3D occupancy and color of a scene from one input view using a large set of unlabeled RGB-D video data. The model processes the observed point cloud with a transformer encoder and uses cross-attention to decode the 3D properties of queried 3D locations. MCC achieves strong performance on diverse in-the-wild images and demonstrates that self-supervised learning from RGB-D video is a promising path for scalable 3D reconstruction.
</details>

[📃 Paper](https://arxiv.org/abs/2301.09107)

---

#### ZeroShape ![](https://img.shields.io/badge/2024-CVPR-green)
**Authors**: Zixuan Huang, Stefan Stojanov, Anh Thai, Varun Jampani, James M Rehg

<details span>
<summary><b>Abstract</b></summary>
We tackle zero-shot 3D shape reconstruction from single RGB images. ZeroShape is a simple, efficient, and general regression-based method trained purely on synthetic data that directly regresses the implicit occupancy field of the 3D shape from a single image. Our model leverages pretrained vision foundation models for feature extraction and achieves strong zero-shot generalization to real-world images without any domain-specific fine-tuning, outperforming existing methods on standard benchmarks while being significantly faster and simpler.
</details>

[📃 Paper](https://arxiv.org/abs/2312.14198) | [🌐 Project Page](https://zixuanh.com/projects/zeroshape.html) | [⌨️ Code](https://github.com/zxhuang1698/ZeroShape)

---

### SDF-Based Methods

#### SparseNeuS ![](https://img.shields.io/badge/2022-ECCV-yellow)
**Authors**: Xiaoxiao Long, Cheng Lin, Peng Wang, Taku Komura, Wenping Wang

<details span>
<summary><b>Abstract</b></summary>
We present SparseNeuS, a novel generalizable neural surface reconstruction method that can reconstruct high-quality surfaces from only 2–3 sparse input views, without per-scene optimization. SparseNeuS leverages a geometry encoding volume constructed from multi-scale image features and a novel rendering strategy incorporating both color and geometry information to train a generalizable implicit surface network. The method achieves fast inference and high reconstruction quality, significantly outperforming previous methods on sparse-view benchmarks.
</details>

[📃 Paper](https://arxiv.org/abs/2206.05737) | [🌐 Project Page](https://xxlong.site/SparseNeuS/) | [⌨️ Code](https://github.com/xxlong0/SparseNeuS)

---

#### Shap-E ![](https://img.shields.io/badge/2023-arXiv-red)
**Authors**: Heewoo Jun, Alex Nichol

<details span>
<summary><b>Abstract</b></summary>
We present Shap-E, a conditional generative model for 3D assets. Unlike prior work that directly generates explicit representations such as point clouds or meshes, Shap-E generates the parameters of implicit functions that can be rendered as both textured meshes and neural radiance fields. We train Shap-E in two stages: first training an encoder to deterministically map 3D assets into the parameters of an implicit function, then training a conditional diffusion model on the resulting latent space. Shap-E can generate diverse and high-quality 3D assets conditioned on text or images in seconds.
</details>

[📃 Paper](https://arxiv.org/abs/2305.02463)

---

#### C2F2NeUS ![](https://img.shields.io/badge/2023-ICCV-yellow)
**Authors**: Luoyuan Xu, Tao Guan, Yuesong Wang, Wenkai Liu, Zhaojie Zeng, Junle Wang, Wei Yang

<details span>
<summary><b>Abstract</b></summary>
We propose C2F2NeUS, a cascade cost frustum fusion approach for high-fidelity and generalizable neural surface reconstruction. Existing generalizable methods suffer from limited reconstruction quality due to insufficient use of local geometric details. C2F2NeUS addresses this by constructing cascade cost frustums at multiple scales, progressively fusing coarse-to-fine geometric features from multi-view images into a signed distance field. The coarse-to-fine design effectively captures both global structure and local fine-grained details, achieving state-of-the-art reconstruction quality on standard benchmarks.
</details>

[📃 Paper](https://arxiv.org/abs/2310.07987)

---

#### UFORecon ![](https://img.shields.io/badge/2024-CVPR-green)
**Authors**: Youngju Na, Woo Jae Kim, Kyu Beom Han, Suhyeon Ha, Sung-Eui Yoon

<details span>
<summary><b>Abstract</b></summary>
We present UFORecon, a framework for generalizable sparse-view surface reconstruction from arbitrary and unfavorable image sets. Prior methods assume ideal camera configurations (e.g., overlapping fields of view), failing when given arbitrary or adverse camera arrangements. UFORecon addresses this by introducing a view-graph-based feature aggregation scheme that robustly handles diverse camera topologies, combined with an SDF-based neural surface representation trained for generalizable reconstruction. UFORecon achieves state-of-the-art performance on standard benchmarks under both favorable and challenging camera configurations.
</details>

[📃 Paper](https://arxiv.org/abs/2403.05086) | [🌐 Project Page](https://youngju-na.github.io/uforecon.github.io/) | [⌨️ Code](https://github.com/youngju-na/UFORecon)

---

#### CRM ![](https://img.shields.io/badge/2024-ECCV-yellow)
**Authors**: Zhengyi Wang, Yikai Wang, Yifei Chen, Chendong Xiang, Shuo Chen, Dajiang Yu, Chongxuan Li, Hang Su, Jun Zhu

<details span>
<summary><b>Abstract</b></summary>
We present CRM, a high-fidelity feed-forward single-image-to-3D generation model. CRM takes a single image as input and outputs a textured 3D mesh in about 10 seconds. The key insight is to use a convolutional U-Net to predict a Flexicubes grid from six multi-view images and normals, which are first generated by a multi-view diffusion model. This enables end-to-end trainable 3D reconstruction with high geometric fidelity and texture quality, significantly advancing the state of the art for single-image 3D generation in terms of both speed and quality.
</details>

[📃 Paper](https://arxiv.org/abs/2403.05034) | [🌐 Project Page](https://ml.cs.tsinghua.edu.cn/~zhengyi/CRM/) | [⌨️ Code](https://github.com/thu-ml/CRM)

---

#### VolRecon ![](https://img.shields.io/badge/2023-CVPR-green)
**Authors**: Yufan Ren, Fangjinhua Wang, Tong Zhang, Marc Pollefeys, Sabine Süsstrunk

<details span>
<summary><b>Abstract</b></summary>
We introduce VolRecon, a novel generalizable reconstruction method using Signed Ray Distance Function (SRDF) with volume rendering. VolRecon reconstructs the 3D geometry of a scene from sparse multi-view images without per-scene optimization. The method employs a ray transformer to aggregate patch-level features from multi-view images and predict the SRDF along sampled rays, enabling volume rendering for geometry extraction. VolRecon achieves state-of-the-art performance on multi-view reconstruction benchmarks and generalizes well to novel scenes.
</details>

[📃 Paper](https://arxiv.org/abs/2212.08067) | [🌐 Project Page](https://fangjinhuawang.github.io/VolRecon/) | [⌨️ Code](https://github.com/IVRL/VolRecon)

---

#### ReTR ![](https://img.shields.io/badge/2023-NeurIPS-blue)
**Authors**: Yixun Liang, Hao He, Yingcong Chen

<details span>
<summary><b>Abstract</b></summary>
We present ReTR, a novel framework that models the rendering process via transformers for generalizable neural surface reconstruction. ReTR introduces a rendering transformer that directly maps multi-view image features to surface properties at queried 3D points through cross-attention, enabling the network to learn how to aggregate multi-view information in a data-driven manner. The rendering transformer is jointly trained with an SDF-based implicit surface representation, achieving state-of-the-art surface reconstruction quality on standard benchmarks while enabling fast feed-forward inference on novel scenes.
</details>

[📃 Paper](https://arxiv.org/abs/2305.18832) | [🌐 Project Page](https://yixunliang.github.io/ReTR/) | [⌨️ Code](https://github.com/YixunLiang/ReTR)

---

## 3D-Free Models

### Regression-Based

#### SRT ![](https://img.shields.io/badge/2022-CVPR-green)
**Authors**: Mehdi SM Sajjadi, Henning Meyer, Etienne Pot, Urs Bergmann, Klaus Greff, Noha Radwan, Suhani Vora, Mario Lučić, Daniel Duckworth, Alexey Dosovitskiy, et al.

<details span>
<summary><b>Abstract</b></summary>
We present the Scene Representation Transformer (SRT), a method for novel view synthesis from unposed images that bypasses explicit 3D representations. SRT uses a transformer-based encoder to map a set of input images to a latent scene representation, and a transformer-based decoder with light field ray queries to render novel views from that representation. Trained on diverse multi-scene datasets, SRT learns to generalize across different scenes without per-scene optimization, enabling feed-forward novel view synthesis in a single forward pass.
</details>

[📃 Paper](https://arxiv.org/abs/2111.13152) | [🌐 Project Page](https://srt-paper.github.io/) | [⌨️ Code](https://github.com/stelzner/srt)

---

#### RUST ![](https://img.shields.io/badge/2023-CVPR-green)
**Authors**: Mehdi SM Sajjadi, Aravindh Mahendran, Thomas Kipf, Etienne Pot, Daniel Duckworth, Mario Lučić, Klaus Greff

<details span>
<summary><b>Abstract</b></summary>
We present RUST (Latent Neural Scene Representations from Unposed Imagery), a method for novel view synthesis purely from unposed RGB images, without any camera pose information. RUST inherits the encoder-decoder architecture of SRT, but replaces explicit camera pose conditioning with implicit latent poses predicted by a learned pose estimation module. This allows the model to discover pose representations in a self-supervised manner and render novel views based on these implicit poses, enabling scene understanding from uncurated image collections.
</details>

[📃 Paper](https://arxiv.org/abs/2211.14306)

---

#### OSRT ![](https://img.shields.io/badge/2022-NeurIPS-blue)
**Authors**: Mehdi SM Sajjadi, Daniel Duckworth, Aravindh Mahendran, Sjoerd Van Steenkiste, Filip Pavetic, Mario Lucic, Leonidas J Guibas, Klaus Greff, Thomas Kipf

<details span>
<summary><b>Abstract</b></summary>
We present the Object Scene Representation Transformer (OSRT), which extends SRT with an object-centric inductive bias for novel view synthesis of multi-object 3D scenes. OSRT incorporates a slot attention module to decompose the encoded scene representation into object-centric slot representations, where each slot captures an individual object or background region. A slot mixer decoder then renders novel views in a single forward pass using these object slots, enabling structured scene understanding and novel view synthesis without per-scene optimization.
</details>

[📃 Paper](https://arxiv.org/abs/2207.01819)

---

#### RePAST ![](https://img.shields.io/badge/2023-arXiv-red)
**Authors**: Aleksandr Safin, Daniel Duckworth, Mehdi SM Sajjadi

<details span>
<summary><b>Abstract</b></summary>
We present RePAST (Relative Pose Attention Scene Representation Transformer), which extends SRT to large-scale unbounded scenes by integrating relative camera pose information into the attention layers. Instead of relying on absolute pose conditioning, RePAST encodes relative transformations between input and query cameras directly into the attention mechanism, enabling the model to generalize to scene-level novel view synthesis without per-scene optimization.
</details>

[📃 Paper](https://arxiv.org/abs/2304.00947)

---

#### GPNR ![](https://img.shields.io/badge/2022-ECCV-yellow)
**Authors**: Mohammed Suhail, Carlos Esteves, Leonid Sigal, Ameesh Makadia

<details span>
<summary><b>Abstract</b></summary>
We present Generalizable Patch-based Neural Rendering (GPNR), a method for novel view synthesis that generalizes across scenes without per-scene optimization. GPNR leverages an encoder-decoder architecture where epipolar geometry is integrated into the encoder to aggregate multi-view patch features along epipolar lines, enabling geometrically consistent feature matching. The decoder then renders novel views from these aggregated features, achieving strong generalization to unseen scenes.
</details>

[📃 Paper](https://arxiv.org/abs/2207.10662)

---

#### Wide-Baseline Stereo NVS ![](https://img.shields.io/badge/2023-CVPR-green)
**Authors**: Yilun Du, Cameron Smith, Ayush Tewari, Vincent Sitzmann

<details span>
<summary><b>Abstract</b></summary>
We present a method for learning to render novel views from wide-baseline stereo image pairs. Our approach introduces a multiview vision transformer that processes stereo pairs with epipolar line sampling to capture geometric correspondences across large baselines. Combined with a neural renderer, our model learns to synthesize photorealistic novel views from challenging wide-baseline inputs, without per-scene optimization, outperforming prior methods on both interpolation and extrapolation benchmarks.
</details>

[📃 Paper](https://arxiv.org/abs/2304.10463)

---

#### GBT ![](https://img.shields.io/badge/2023-ICCV-yellow)
**Authors**: Naveen Venkat, Mayank Agarwal, Maneesh Singh, Shubham Tulsiani

<details span>
<summary><b>Abstract</b></summary>
We present Geometry-Biased Transformers (GBT), a method for novel view synthesis that incorporates geometric reasoning into transformer-based architectures. GBT introduces ray distance-based geometry reasoning into the multi-head attention layers of both the encoder and decoder transformers, enabling the network to leverage geometric structure for improved rendering quality. The geometry-biased attention encourages the model to attend to geometrically relevant features, leading to better generalization on novel scenes.
</details>

[📃 Paper](https://arxiv.org/abs/2301.04650) | [🌐 Project Page](https://mayankgrwl97.github.io/gbt/) | [⌨️ Code](https://github.com/mayankgrwl97/gbt)

---

#### GTA ![](https://img.shields.io/badge/2024-ICLR-blue)
**Authors**: Takeru Miyato, Bernhard Jaeger, Max Welling, Andreas Geiger

<details span>
<summary><b>Abstract</b></summary>
We present GTA (Geometric Transform Attention), a geometry-aware attention mechanism that embeds the geometrical structure of 3D tokens into transformer computations. GTA encodes relative 3D transformations between token pairs as biases in the attention weights, enabling the transformer to naturally reason about spatial relationships. When integrated into SRT, GTA improves novel view synthesis quality by giving the model an explicit understanding of the geometry underlying the scene representation.
</details>

[📃 Paper](https://arxiv.org/abs/2310.10375) | [🌐 Project Page](https://takerum.github.io/gta/) | [⌨️ Code](https://github.com/autonomousvision/gta)

---

#### LVSM ![](https://img.shields.io/badge/2025-ICLR-blue)
**Authors**: Haian Jin, Hanwen Jiang, Hao Tan, Kai Zhang, Sai Bi, Tianyuan Zhang, Fujun Luan, Noah Snavely, Zexiang Xu

<details span>
<summary><b>Abstract</b></summary>
We present LVSM (Large View Synthesis Model), a transformer-based approach for novel view synthesis with minimal 3D inductive bias. LVSM treats posed multi-view images and Plücker ray embeddings as tokens and uses a large-scale self-attention architecture to directly regress target view pixels, without any explicit 3D geometric priors or epipolar constraints in the architecture. Trained at scale, LVSM demonstrates that a pure attention-based architecture can achieve state-of-the-art novel view synthesis quality across diverse indoor and outdoor scenes.
</details>

[📃 Paper](https://arxiv.org/abs/2410.17242) | [🌐 Project Page](https://haian-jin.github.io/projects/LVSM/) | [⌨️ Code](https://github.com/Haian-Jin/LVSM)

---

#### RayZer ![](https://img.shields.io/badge/2025-arXiv-red)
**Authors**: Hanwen Jiang, Hao Tan, Peng Wang, Haian Jin, Yue Zhao, Sai Bi, Kai Zhang, Fujun Luan, Kalyan Sunkavalli, Qixing Huang, et al.

<details span>
<summary><b>Abstract</b></summary>
We present RayZer, a self-supervised large view synthesis model that enables novel view synthesis without camera pose annotations. RayZer jointly learns camera parameters and latent scene representations from unposed multi-view images, then renders novel views using the learned representations and ray embeddings. Through a self-supervised training objective that exploits multi-view consistency, RayZer learns to discover pose representations and generalize to novel scenes, bridging the gap between posed and unposed novel view synthesis.
</details>

[📃 Paper](https://arxiv.org/abs/2505.00702)

---

### Image Diffusion-Based

#### GFVS ![](https://img.shields.io/badge/2021-ICCV-yellow)
**Authors**: Robin Rombach, Patrick Esser, Björn Ommer

<details span>
<summary><b>Abstract</b></summary>
We present Geometry-Free View Synthesis (GFVS), a transformer-based approach for novel view synthesis that requires no 3D priors. Rather than learning a deterministic mapping from input to target views, GFVS models the distribution of plausible target views conditioned on a source image and camera transformation, sampling outputs autoregressively using a transformer. This generative formulation allows the model to handle large viewpoint changes and ambiguous regions without explicit geometric reasoning.
</details>

[📃 Paper](https://arxiv.org/abs/2104.07652)

---

#### ViewFormer ![](https://img.shields.io/badge/2022-ECCV-yellow)
**Authors**: Jonáš Kulhánek, Erik Derner, Torsten Sattler, Robert Babůška

<details span>
<summary><b>Abstract</b></summary>
We present ViewFormer, a NeRF-free method for few-shot novel view synthesis using transformers. ViewFormer encodes a set of context images and camera poses with a ViT-based image encoder, then autoregressively generates target view images with a discrete token-based image decoder conditioned on the target camera pose. A key contribution is a branching attention mechanism that extends single-view to multiview novel view synthesis, enabling the model to synthesize diverse novel views from a handful of reference images without any 3D representation.
</details>

[📃 Paper](https://arxiv.org/abs/2112.05218)

---

#### RenderDiffusion ![](https://img.shields.io/badge/2023-CVPR-green)
**Authors**: Titas Anciukevičius, Zexiang Xu, Matthew Fisher, Paul Henderson, Hakan Bilen, Niloy J Mitra, Paul Guerrero

<details span>
<summary><b>Abstract</b></summary>
We present RenderDiffusion, the first diffusion model for 3D generation and inference trained using only monocular 2D supervision. Central to our method is a novel image denoising architecture that generates and renders an intermediate three-dimensional representation of a scene in each denoising step. This enforces a strong inductive structure within the diffusion process, providing a 3D-consistent representation while only requiring 2D supervision. The resulting 3D representation can be rendered from any view. Our method supports 3D object generation, single-image 3D reconstruction, and 3D-consistent inpainting, all within a single unified framework trained from 2D images alone.
</details>

[📃 Paper](https://arxiv.org/abs/2211.09869) | [⌨️ Code](https://github.com/Anciukevicius/RenderDiffusion)

---

#### Zero-1-to-3 ![](https://img.shields.io/badge/2023-ICCV-yellow)
**Authors**: Ruoshi Liu, Rundi Wu, Basile Van Hoorick, Pavel Tokmakov, Sergey Zakharov, Carl Vondrick

<details span>
<summary><b>Abstract</b></summary>
We present Zero-1-to-3, a framework for changing the camera viewpoint of an object given a single RGB image. To perform novel view synthesis in this zero-shot setting, we leverage geometric priors that large-scale diffusion models learn from internet data. Our conditional diffusion model uses the relative camera viewpoint as an explicit conditioning factor, replacing the text prompt of a pretrained latent diffusion model. Zero-1-to-3 demonstrates that the knowledge acquired by large generative models can be leveraged for 3D-aware downstream tasks such as novel view synthesis and 3D reconstruction.
</details>

[📃 Paper](https://arxiv.org/abs/2303.11328) | [🌐 Project Page](https://zero123.cs.columbia.edu/) | [⌨️ Code](https://github.com/cvlab-columbia/zero123)

---

#### ZeroNVS ![](https://img.shields.io/badge/2024-CVPR-green)
**Authors**: Kyle Sargent, Zizhang Li, Tanmay Shah, Charles Herrmann, Hong-Xing Yu, Yunzhi Zhang, Eric Ryan Chan, Dmitry Lagun, Li Fei-Fei, Deqing Sun, et al.

<details span>
<summary><b>Abstract</b></summary>
We present ZeroNVS, a method for zero-shot 360-degree view synthesis from a single in-the-wild image. Extending Zero-1-to-3 to scene-level novel view synthesis, ZeroNVS introduces field-of-view conditioning to resolve the scale ambiguity inherent in single-image 3D inference. The model is trained on a curated mixture of 3D data sources covering diverse indoor and outdoor scenes, enabling robust generalization to real-world single images and enabling 360-degree scene extrapolation without per-scene optimization.
</details>

[📃 Paper](https://arxiv.org/abs/2310.17994) | [🌐 Project Page](https://kylesargent.github.io/zeronvs/) | [⌨️ Code](https://github.com/kylesargent/ZeroNVS)

---

#### SyncDreamer ![](https://img.shields.io/badge/2023-arXiv-red)
**Authors**: Yuan Liu, Cheng Lin, Zijiao Zeng, Xiaoxiao Long, Lingjie Liu, Taku Komura, Wenping Wang

<details span>
<summary><b>Abstract</b></summary>
We present SyncDreamer, a diffusion model that generates multiview-consistent images from a single-view image. Initialized from Zero-1-to-3 weights, SyncDreamer models the joint distribution of 16 target views simultaneously using a 3D-aware feature attention mechanism that synchronizes information across all generated views. This joint generation ensures geometric and appearance consistency across different viewpoints, enabling the use of multi-view reconstruction pipelines to recover high-quality 3D shapes from the generated views.
</details>

[📃 Paper](https://arxiv.org/abs/2309.03453) | [🌐 Project Page](https://liuyuan-pal.github.io/SyncDreamer/) | [⌨️ Code](https://github.com/liuyuan-pal/SyncDreamer)

---

#### Zero123++ ![](https://img.shields.io/badge/2023-arXiv-red)
**Authors**: Ruoxi Shi, Hansheng Chen, Zhuoyang Zhang, Minghua Liu, Chao Xu, Xinyue Wei, Linghao Chen, Chong Zeng, Hao Su

<details span>
<summary><b>Abstract</b></summary>
We present Zero123++, a single-image-to-3D generation baseline that generates six consistent views of a 3D object from a single reference image. Unlike prior methods that generate views independently, Zero123++ arranges six target views in a single output image grid, enabling the diffusion model to enforce global consistency via self-attention across all views simultaneously. We further introduce training improvements including consistent noise schedules and reference conditioning, resulting in a strong and efficient multi-view diffusion base model.
</details>

[📃 Paper](https://arxiv.org/abs/2310.15110) | [⌨️ Code](https://github.com/SUDO-AI-3D/zero123plus)

---

#### ViewDiff ![](https://img.shields.io/badge/2024-CVPR-green)
**Authors**: Lukas Höllein, Aljaž Božič, Norman Müller, David Novotny, Hung-Yu Tseng, Christian Richardt, Michael Zollhöfer, Matthias Nießner

<details span>
<summary><b>Abstract</b></summary>
We present ViewDiff, a method for 3D-consistent image generation using pretrained text-to-image diffusion models. ViewDiff integrates cross-frame attention layers and 3D volume rendering into the U-Net blocks of a text-to-image model, enabling the generation of multi-view consistent images in a single denoising pass. An autoregressive generation scheme further improves 3D consistency across arbitrary viewpoints. Trained on real-world object datasets, ViewDiff generates diverse, high-quality instances with authentic textures and backgrounds that are consistent across multiple viewpoints.
</details>

[📃 Paper](https://arxiv.org/abs/2403.01807) | [🌐 Project Page](https://lukashoel.github.io/ViewDiff/) | [⌨️ Code](https://github.com/facebookresearch/ViewDiff)

---

#### Consistent123 ![](https://img.shields.io/badge/2023-arXiv-red)
**Authors**: Haohan Weng, Tianyu Yang, Jianan Wang, Yu Li, Tong Zhang, C.L. Chen, Lei Zhang

<details span>
<summary><b>Abstract</b></summary>
We present Consistent123, a method that combines Zero-1-to-3 and stable diffusion to provide case-aware diffusion priors for single-image-to-3D synthesis. Consistent123 introduces a consistency module that aligns multi-view generated images to enforce geometric consistency, using cross-view attention to propagate information from reference views to target views during the diffusion process. This enables the generation of multi-view consistent images from a single input image, significantly improving the quality of downstream 3D reconstruction.
</details>

[📃 Paper](https://arxiv.org/abs/2310.08092)

---

#### ConsistNet ![](https://img.shields.io/badge/2024-CVPR-green)
**Authors**: Jiayu Yang, Ziang Cheng, Yunfei Duan, Pan Ji, Hongdong Li

<details span>
<summary><b>Abstract</b></summary>
We present ConsistNet, a method for enforcing 3D consistency in multi-view image diffusion. ConsistNet performs parallel viewpoint-specific diffusion and aligns the generated images using a consistency module that shares information across views via epipolar attention. By explicitly enforcing geometric constraints during the diffusion process, ConsistNet generates multi-view images that are both photorealistic and geometrically consistent, enabling high-quality downstream 3D reconstruction without per-scene optimization.
</details>

[📃 Paper](https://arxiv.org/abs/2310.08527)

---

#### MVDream ![](https://img.shields.io/badge/2023-arXiv-red)
**Authors**: Yichun Shi, Peng Wang, Jianglong Ye, Mai Long, Kejie Li, Xiao Yang

<details span>
<summary><b>Abstract</b></summary>
We present MVDream, a multi-view diffusion model that generates geometrically consistent multi-view images from text prompts. MVDream adapts a 2D text-to-image diffusion model by introducing 3D self-attention layers that attend across views, leveraging both 2D internet image data and 3D rendered data for training. This combination inherits the generalizability of 2D diffusion models while achieving the multi-view consistency of 3D renderings, providing powerful 3D priors applicable to text-to-3D generation and novel view synthesis tasks.
</details>

[📃 Paper](https://arxiv.org/abs/2308.16512) | [🌐 Project Page](https://mv-dream.github.io/) | [⌨️ Code](https://github.com/bytedance/MVDream)

---

#### CAT3D ![](https://img.shields.io/badge/2024-arXiv-red)
**Authors**: Ruiqi Gao, Aleksander Holynski, Philipp Henzler, Arthur Brussee, Ricardo Martin-Brualla, Pratul Srinivasan, Jonathan T Barron, Ben Poole

<details span>
<summary><b>Abstract</b></summary>
We present CAT3D (Create Anything in 3D), a method for creating high-quality 3D scenes from any number of input images using a multi-view diffusion model. CAT3D first generates large numbers of consistent novel views using a multi-view diffusion model conditioned on the input images, then uses these views for robust 3D reconstruction. This two-stage approach disentangles generation and reconstruction, enabling the creation of compelling 3D scenes from as few as one input image, with state-of-the-art quality across a diverse range of objects and scenes.
</details>

[📃 Paper](https://arxiv.org/abs/2405.10314) | [🌐 Project Page](https://cat3d.github.io/)

---

#### SEVA ![](https://img.shields.io/badge/2025-arXiv-red)
**Authors**: Jensen Jinghao Zhou, Hang Gao, Vikram Voleti, Aaryaman Vasishta, Chun-Han Yao, Mark Boss, Philip Torr, Christian Rupprecht, Varun Jampani

<details span>
<summary><b>Abstract</b></summary>
We present SEVA (Stable Virtual Camera), a generative model for novel view synthesis based on diffusion models. SEVA generates high-quality novel views of real-world scenes conditioned on one or more input images and target camera parameters, trained on a large-scale dataset of multi-view scenes. Our model demonstrates strong generalization to in-the-wild images and can synthesize consistent novel views across large camera motions, enabling compelling applications in visual media production and 3D content creation.
</details>

[📃 Paper](https://arxiv.org/abs/2503.14489) | [🌐 Project Page](https://stabilityai.github.io/stable-virtual-camera/) | [⌨️ Code](https://github.com/Stability-AI/stable-virtual-camera)

---

#### CAT4D ![](https://img.shields.io/badge/2025-CVPR-brightgreen)
**Authors**: Rundi Wu, Ruiqi Gao, Ben Poole, Alex Trevithick, Changxi Zheng, Jonathan T Barron, Aleksander Holynski

<details span>
<summary><b>Abstract</b></summary>
We present CAT4D (Create Anything in 4D), which extends CAT3D to dynamic 4D reconstruction from monocular video. CAT4D uses multi-view video diffusion models to generate consistent multi-view observations across both space and time from a single input video, then applies a robust 4D reconstruction method to produce dynamic radiance fields. This approach enables high-quality reconstruction of complex dynamic scenes, including non-rigid motions, from casually captured monocular video.
</details>

[📃 Paper](https://arxiv.org/abs/2411.18613) | [🌐 Project Page](https://cat-4d.github.io/)

---

### Video Diffusion-Based

#### ReconX ![](https://img.shields.io/badge/2024-arXiv-red)
**Authors**: Fangfu Liu, Wenqiang Sun, Hanyang Wang, Yikai Wang, Haowen Sun, Junliang Ye, Jun Zhang, Yueqi Duan

<details span>
<summary><b>Abstract</b></summary>
We present ReconX, a novel 3D scene reconstruction paradigm that reframes the challenge as a temporal generation task using video diffusion models. ReconX uses the generative prior of large pretrained video diffusion models to synthesize novel views from any sparse set of input views. Point clouds extracted from the sparse inputs are encoded as 3D structural conditions that guide the video diffusion model, ensuring multi-view consistency and geometric faithfulness in the generated views. The resulting multi-view video is then used for high-quality 3D reconstruction.
</details>

[📃 Paper](https://arxiv.org/abs/2408.16767) | [🌐 Project Page](https://liuff19.github.io/ReconX/) | [⌨️ Code](https://github.com/liuff19/ReconX)

---

#### ViewCrafter ![](https://img.shields.io/badge/2024-arXiv-red)
**Authors**: Wangbo Yu, Jinbo Xing, Li Yuan, Wenbo Hu, Xiaoyu Li, Zhipeng Huang, Xiangjun Gao, Tien-Tsin Wong, Ying Shan, Yonghong Tian

<details span>
<summary><b>Abstract</b></summary>
We present ViewCrafter, a method for taming video diffusion models to enable high-fidelity novel view synthesis from single or sparse images. Rather than directly using point clouds as conditions, ViewCrafter renders the reconstructed point cloud into images at target viewpoints and uses these rendered images as visual conditions for a video diffusion model. This approach provides strong structural guidance while leveraging the generative capacity of video diffusion models to hallucinate unseen regions, enabling consistent and accurate novel view synthesis with large viewpoint changes.
</details>

[📃 Paper](https://arxiv.org/abs/2409.02048) | [🌐 Project Page](https://drexubery.github.io/ViewCrafter/) | [⌨️ Code](https://github.com/Drexubery/ViewCrafter)

---

#### MultiDiff ![](https://img.shields.io/badge/2024-CVPR-green)
**Authors**: Norman Müller, Katja Schwarz, Barbara Rössle, Lorenzo Porzi, Samuel Rota Buló, Matthias Nießner, Peter Kontschieder

<details span>
<summary><b>Abstract</b></summary>
We present MultiDiff, a method for consistent novel view synthesis from a single image using diffusion models. MultiDiff generates multiple geometrically consistent novel views simultaneously by conditioning on a single reference image and a predefined target camera trajectory, using depth cues extracted from the input image to guide the generation. A shared noise strategy encourages global scene consistency across all generated views, enabling the creation of diverse yet coherent scene visualizations without per-scene optimization.
</details>

[📃 Paper](https://arxiv.org/abs/2306.05003) | [🌐 Project Page](https://sirwyver.github.io/MultiDiff/)

---

#### Difix3D+ ![](https://img.shields.io/badge/2025-CVPR-brightgreen)
**Authors**: Jay Zhangjie Wu, Yuxuan Zhang, Haithem Turki, Xuanchi Ren, Jun Gao, Mike Zheng Shou, Sanja Fidler, Zan Gojcic, Huan Ling

<details span>
<summary><b>Abstract</b></summary>
We present Difix3D+, a pipeline for improving 3D reconstructions using single-step diffusion models. Difix is a single-step image diffusion model trained to enhance rendered novel views by removing artifacts caused by underconstrained regions of NeRF or 3DGS representations. Difix3D+ uses this model in two roles: during reconstruction to clean up pseudo-training views that are distilled back into 3D, and at inference as a neural enhancer to remove residual rendering artifacts. The result is a general, reconstruction-agnostic pipeline compatible with both NeRF and 3DGS that achieves significant quality improvements on novel view synthesis benchmarks.
</details>

[📃 Paper](https://arxiv.org/abs/2503.01774) | [🌐 Project Page](https://research.nvidia.com/labs/toronto-ai/difix3d/) | [⌨️ Code](https://github.com/nv-tlabs/Difix3D)

---

#### SpatialCrafter ![](https://img.shields.io/badge/2025-ICCV-yellow)
**Authors**: Songchun Zhang, Huiyao Xu, Sitong Guo, Zhongwei Xie, Pengwei Liu, Hujun Bao, Weiwei Xu, Changqing Zou

<details span>
<summary><b>Abstract</b></summary>
We present SpatialCrafter, a framework that leverages video diffusion models to generate plausible novel views for scene reconstruction from sparse or single-view inputs. SpatialCrafter achieves precise camera control via ray embeddings and a trainable camera encoder with epipolar attention, ensuring 3D-consistent view generation. A unified scale estimator resolves scale ambiguity across multi-dataset training, and a hybrid Mamba-Transformer architecture integrates monocular depth priors with semantic video latent features to directly regress 3D Gaussian primitives from the generated views, enabling robust scene reconstruction under minimal observation.
</details>

[📃 Paper](https://arxiv.org/abs/2505.11992) | [🌐 Project Page](https://franklinz233.github.io/projects/spatialcrafter/)

---

#### GenFusion ![](https://img.shields.io/badge/2025-CVPR-brightgreen)
**Authors**: Sibo Wu, Congrong Xu, Binbin Huang, Andreas Geiger, Anpei Chen

<details span>
<summary><b>Abstract</b></summary>
We present GenFusion, a method that closes the loop between 3D reconstruction and video generation for artifact-free novel view synthesis. GenFusion introduces a reconstruction-driven video diffusion model that conditions on artifact-prone RGB-D renderings from a 3D reconstruction, learning to restore missing or corrupted regions. A cyclical fusion pipeline iteratively incorporates restored frames back into the training set for the 3D reconstruction, progressively improving reconstruction quality and enabling scene content expansion along novel trajectories. This coupling of generation and reconstruction resolves the coverage limitations of sparse-view inputs.
</details>

[📃 Paper](https://arxiv.org/abs/2503.21219) | [🌐 Project Page](https://genfusion.sibowu.com/) | [⌨️ Code](https://github.com/Inception3D/GenFusion)

---

