# CLEAR: Conflict-Aware Modality-Reliability Fusion With Language Priors for Multimodal Remote-Sensing Semantic Segmentation

**Conflict-aware Language-prior Evidential Reliability (CLEAR)** is a plug-in fusion neck for dual-encoder multimodal remote-sensing semantic segmentation. It learns a normalized per-pixel modality-reliability distribution at a standard feature-pyramid interface, so it can be attached to existing encoder--decoder architectures without redesigning their internal interaction rules.

## Authors

Yongqi Sun, Anzhu Yu\*, Chenguang Dai, Qi Dong, Yinhe Liu, Danyang Hong, Yanfei Zhong

\*Corresponding author: Anzhu Yu (`anzhu_yu@126.com`).

## Abstract  

Multimodal remote-sensing semantic segmentation combines optical imagery with complementary measurements. Its performance depends on how reliability is allocated between modalities at each pixel, particularly when the inputs disagree. Existing fusion weights describe feature interaction rather than explicit relative reliability, and therefore need not provide a well-founded allocation under disagreement. Architecture-specific interaction rules can also require redesign. We present Conflict-aware Language-prior Evidential Reliability (CLEAR), a plug-in fusion neck that learns a normalized per-pixel modality-reliability distribution at a standard feature-pyramid interface. Per-modality Dirichlet distributions model the class evidence committed by each visual branch and yield evidential confidence. Frozen Contrastive Language--Image Pretraining (CLIP) text prototypes parameterize a trainable prior over class-conditioned modality preferences, using language to guide fusion rather than to predict segmentation classes directly. CLEAR combines this prior with the evidential confidence and decomposes Dempster--Shafer conflict into two continuous components according to prior concentration. The directed component sharpens semantically supported allocation, while the unresolved component reduces unsupported asymmetry. Across five benchmarks spanning digital surface models, synthetic aperture radar, near-infrared imagery, and relative depth, CLEAR outperforms the strongest evaluated multimodal state-of-the-art (SOTA) method on each dataset. In architecture-matched comparisons, it improves mean intersection over union (mIoU) by an average of 1.27 percentage points with DINOv2-Base and 1.10 percentage points with DINOv2-Large. CLEAR is validated with seven encoder backbones and three decoder heads and yields positive matched gains on two RGB--thermal datasets without architectural modification. These results support explicit modality-reliability modeling as a complement to pixel-level feature interaction.

## Matched Results at Two Backbone Capacities

The non-ablation comparisons use same-capacity concatenation baselines. Values are mIoU (%), and gains are CLEAR minus the corresponding model without CLEAR.

| Backbone | Configuration | Potsdam | Vaihingen | WHU-NIR | WHU-SAR | SUSAN | Average |
|---|---|---:|---:|---:|---:|---:|---:|
| DINOv2-Base | w/o CLEAR | 78.91 | 74.50 | 57.45 | 57.24 | 48.88 | 63.40 |
| DINOv2-Base | + CLEAR | 79.94 | 75.71 | 57.95 | 57.93 | 51.82 | 64.67 |
| DINOv2-Base | Gain | +1.03 | +1.21 | +0.50 | +0.69 | +2.94 | +1.27 |
| DINOv2-Large | w/o CLEAR | 79.53 | 74.95 | 57.89 | 57.50 | 51.40 | 64.25 |
| DINOv2-Large | + CLEAR | 80.78 | 76.48 | 58.33 | 58.71 | 52.49 | 65.36 |
| DINOv2-Large | Gain | +1.25 | +1.53 | +0.44 | +1.21 | +1.09 | +1.10 |

The Base gain is larger on WHU-NIR and SUSAN, whereas the Large gain is larger on Potsdam, Vaihingen, and WHU-SAR. CLEAR is therefore more effective on average with the smaller backbone in these experiments, but the result does not imply a universal inverse relationship between backbone size and fusion benefit.

## Results on ISPRS Potsdam

Per-class IoU and mIoU (%) on the ISPRS Potsdam benchmark (RGB + DSM, 5 cm GSD, six classes). `Opt.` denotes optical imagery and `Aux.` the co-registered DSM. The best value in each column is in bold. `Δ` is CLEAR-Large minus the architecture-matched DINOv2-Large model without CLEAR, which replaces the CLEAR neck with feature concatenation while keeping the same encoders, decoder, optimizer, schedule, crop size, and evaluation protocol.

| Method | Modality | Imperv. surf. | Building | Low veg. | Tree | Car | Clutter | mIoU |
|---|---|---:|---:|---:|---:|---:|---:|---:|
| UrbanSSF-L | Opt. | 86.98 | 93.58 | 77.66 | 80.06 | 92.90 | 44.98 | 79.36 |
| MSEONet | Opt. | 86.95 | 93.16 | 76.30 | 79.79 | 90.54 | 42.80 | 78.26 |
| CFFormer-B4 | Opt.+Aux. | 87.98 | 94.08 | 78.68 | 80.65 | 92.27 | 43.25 | 79.48 |
| DFormer-L | Opt.+Aux. | 87.95 | 95.25 | 78.18 | 80.47 | 92.70 | 43.23 | 79.63 |
| DFormerv2-L | Opt.+Aux. | 87.81 | 94.71 | 78.61 | 80.66 | 93.07 | 43.40 | 79.71 |
| DINOv2-Large w/o CLEAR | Opt.+Aux. | 87.61 | 94.58 | 77.55 | 80.18 | 92.83 | 44.43 | 79.53 |
| **CLEAR-Large (ours)** | Opt.+Aux. | **88.24** | **95.38** | **79.20** | **81.04** | **93.64** | **47.15** | **80.78** |
| Δ | -- | +0.63 | +0.80 | +1.65 | +0.86 | +0.81 | +2.72 | +1.25 |

CLEAR-Large leads every category among the evaluated configurations. The largest matched gain is on clutter (+2.72), followed by low vegetation (+1.65). All results use single-scale inference without test-time augmentation.

## Code Availability

The code is available at [https://github.com/Ameeliaaa/CLEAR](https://github.com/Ameeliaaa/CLEAR).

## Citation

If you find this work useful, please cite:

```bibtex
@article{sun2026clear,
  title   = {Conflict-Aware Modality-Reliability Fusion With Language Priors
             for Multimodal Remote-Sensing Semantic Segmentation},
  author  = {Sun, Yongqi and Yu, Anzhu and Dai, Chenguang and Dong, Qi and
             Liu, Yinhe and Hong, Danyang and Zhong, Yanfei},
  journal = {ISPRS Journal of Photogrammetry and Remote Sensing},
  year    = {2026}
}
```

The volume, number, page range, and DOI will be added once the paper is published.
