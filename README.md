# CLEAR: Conflict-Aware Modality-Reliability Fusion With Language Priors for Multimodal Remote-Sensing Semantic Segmentation

**Conflict-aware Language-prior Evidential Reliability (CLEAR)** is a plug-in fusion neck for dual-encoder multimodal remote-sensing semantic segmentation. It learns a normalized per-pixel modality-reliability distribution at a standard feature-pyramid interface, so it can be attached to existing encoder--decoder architectures without redesigning their internal interaction rules.

## Authors

Yongqi Sun, Anzhu Yu\*, Chenguang Dai, Qi Dong, Yinhe Liu (Member, IEEE), Danyang Hong, Yanfei Zhong (Senior Member, IEEE)

\*Corresponding author: Anzhu Yu (`anzhu_yu@126.com`).

Yongqi Sun, Anzhu Yu, Chenguang Dai, Qi Dong, and Danyang Hong are with the School of Surveying and Mapping, Information Engineering University, Zhengzhou 450001, China. Yinhe Liu and Yanfei Zhong are with the State Key Laboratory of Information Engineering in Surveying, Mapping and Remote Sensing, Wuhan University, Wuhan 430079, China.

## Abstract

Multimodal remote-sensing semantic segmentation combines optical imagery with complementary measurements. Its performance depends on how reliability is allocated between modalities at each pixel, particularly when the inputs disagree. Existing fusion weights describe feature interaction rather than explicit relative reliability, and therefore need not provide a well-founded allocation under disagreement. Architecture-specific interaction rules can also require redesign. We present Conflict-aware Language-prior Evidential Reliability (CLEAR), a plug-in fusion neck that learns a normalized per-pixel modality-reliability distribution at a standard feature-pyramid interface. Per-modality Dirichlet distributions model the class evidence committed by each visual branch and yield evidential confidence. Frozen Contrastive Language--Image Pretraining (CLIP) text prototypes parameterize a trainable prior over class-conditioned modality preferences, using language to guide fusion rather than to predict segmentation classes directly. CLEAR combines this prior with the evidential confidence and decomposes Dempster--Shafer conflict into two continuous components according to prior concentration. The directed component sharpens semantically supported allocation, while the unresolved component reduces unsupported asymmetry. Across five benchmarks spanning digital surface models, synthetic aperture radar, near-infrared imagery, and relative depth, CLEAR outperforms the strongest evaluated multimodal state-of-the-art (SOTA) method on each dataset. In architecture-matched comparisons, it improves mean intersection over union (mIoU) by an average of 1.96 percentage points over configurations without CLEAR. CLEAR is validated with seven encoder backbones and three decoder heads and yields positive matched gains on two RGB--thermal datasets without architectural modification. These results support explicit modality-reliability modeling as a complement to pixel-level feature interaction.


## Code Availability

The code is available at [https://github.com/Ameeliaaa/CLEAR](https://github.com/Ameeliaaa/CLEAR).

## Citation

If you find this work useful, please cite:

```bibtex
@article{sun2026clear,
  title   = {Conflict-Aware Modality-Reliability Fusion With Language Priors
             for Multimodal Remote-Sensing Semantic Segmentation},
  author  = {Sun, Yongqi and Yu, Anzhu and Dai, Chenguang and Dong, Qi
             and Liu, Yinhe and Hong, Danyang and Zhong, Yanfei},
  journal = {IEEE Transactions on Geoscience and Remote Sensing},
  year    = {2026}
}
```

The volume, number, page range, and DOI will be added once the paper is published.
