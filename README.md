# VisDrone three-class split and reported results

This repository contains the data used for the reported experiments. Training and model code are not included.

## Dataset

`data/visdrone_3class` is a three-class subset of VisDrone detection images: pedestrian, car, and bicycle. Official training and validation images were pooled, boxes with a non-positive score or with width, height, or area below 4, 4, and 16 pixels were removed, and the remaining images were divided 80/20 with seed 42.

- Training images: 5,610
- Validation images: 1,403
- `labels/train` and `labels/val`: YOLO labels used for the reported numbers
- `splits/train.txt` and `splits/val.txt`: the exact image file names in each partition
- `conversion_stats.json`: counts recorded when the split was built
- `data.yaml`: class names and the `images/train`, `images/val` layout

The original VisDrone photographs are not redistributed here. Download them from the VisDrone authors and place each file listed in the split lists under `data/visdrone_3class/images/train` or `images/val`. The three training seeds used this same image list; they did not redraw the split.

## Results

`results` stores one folder per model. Each seed directory contains `results.csv` and `args.yaml`. Metrics below are the epoch with the highest AP50–95. Seeds are listed as seed 42, seed 1, seed 2.

| Model | AP50 | AP50–95 |
| --- | --- | --- |
| Complete GRSF | 0.5605, 0.5598, 0.5609 | 0.3199, 0.3193, 0.3192 |
| GRSF without auxiliary loss | 0.5585, 0.5586, 0.5594 | 0.3185, 0.3184, 0.3190 |
| CBAM | 0.5579, 0.5560, 0.5585 | 0.3190, 0.3177, 0.3182 |
| Linear bottleneck | 0.5561, 0.5543, 0.5589 | 0.3180, 0.3173, 0.3187 |
| SCConv | 0.5555, 0.5576, 0.5592 | 0.3172, 0.3179, 0.3196 |
| YOLOv10m | 0.5040, one run | 0.2966, one run |

Precision, recall, and the selected epoch are in `results/README.md`.
