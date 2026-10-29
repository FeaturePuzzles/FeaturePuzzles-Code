<div align="center">

# Feature Puzzles

### Single-Image Supervision for Multi-View 3D-Aware Segmentation

[Jiahao Ma](https://jiahao-ma.github.io/)<sup>1</sup> &nbsp;
[Qiang Zhang](https://jonyzhang2023.github.io/)<sup>2</sup> &nbsp;
[Miaomiao Liu](http://users.cecs.anu.edu.au/~mliu/)<sup>1</sup> &nbsp;
[David Ahmedt-Aristizabal](https://people.csiro.au/a/d/david-ahmedtaristizabal)<sup>3</sup> &nbsp;
[Chuong Nguyen](https://people.csiro.au/N/C/Chuong-Nguyen)<sup>3</sup>

<sup>1</sup>Australian National University &nbsp;
<sup>2</sup>University of Science and Technology of China &nbsp;
<sup>3</sup>CSIRO, Australia

[**Project page**](https://featurepuzzles.github.io/) ·
[**Paper**](https://openreview.net/forum?id=C9iJlwJc0W) ·
[**Video (1:30)**](https://featurepuzzles.github.io/media/promo/teaser_90s.mp4)

</div>

> [!NOTE]
> **Code is coming soon.** We plan to release the code around the **end of November 2026**. Watch or star this repository to be notified.

## Video

<a href="https://featurepuzzles.github.io/media/promo/teaser_90s.mp4">
  <img src="https://featurepuzzles.github.io/media/promo/poster.jpg" alt="Feature Puzzles, 1:30 video" width="100%">
</a>

<p align="center"><a href="https://featurepuzzles.github.io/media/promo/teaser_90s.mp4">▶ Watch the 1:30 video</a> &nbsp;·&nbsp; <a href="https://featurepuzzles.github.io/#video">full 5:56 version on the project page</a></p>

## What is Feature Puzzles?

People recognize the same object from any viewpoint of a 3D scene. Teaching a model to do the same usually takes videos, calibrated multi-view captures or reconstructed 3D scenes, which are far more expensive and less diverse than ordinary single images.

**Feature Puzzles** learns multi-view-consistent segmentation from **single-image supervision only**:

- **Multi-view supervision from one image.** Overlapping crops of a single image become synthetic views. Every crop is tied to the parent image by a known transform, so labels (SAM instance masks) and dense teacher features (DINO) computed once on the parent agree on every overlap by construction. No video, no camera poses, no multi-view annotation.
- **Plug-and-play on a 3D foundation model.** Lightweight decoders sit on a pretrained VGGT-Omega backbone, adapted only in its last blocks with LoRA. The adapters switch off at inference, so the backbone's original depth and camera outputs are kept.
- **One model, many prompts.** Mask, point or box prompts given on one or more views return masks on every view in a single feed-forward pass, with no per-scene optimization.
- **Open-vocabulary 3D segmentation.** A feature decoder distills single-image DINOv3 features into multi-view-consistent dense features; matching them to text queries gives open-vocabulary instances fused in 3D, from rooms to building scale, zero-shot.

Under this single-image supervision, the feed-forward model achieves the best mIoU on NVOS, stays competitive on SPIn-NeRF and ScanNet++ against baselines that use per-scene optimization or in-domain multi-view training, and transfers zero-shot to open-vocabulary 3D segmentation.

## Release plan

- [x] Project page and video
- [ ] Code release (expected around the end of November 2026)

## Citation

```bibtex
@misc{ma2026featurepuzzles,
  title  = {Feature Puzzles: Single-Image Supervision for Multi-View 3D-Aware Segmentation},
  author = {Ma, Jiahao and Zhang, Qiang and Liu, Miaomiao and Ahmedt-Aristizabal, David and Nguyen, Chuong},
  year   = {2026},
  url    = {https://featurepuzzles.github.io/}
}
```
