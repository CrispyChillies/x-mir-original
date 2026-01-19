# Evaluate Saliency Usage Examples

This document shows how to use the updated `evaluate_saliency.py` script with different model architectures and devices.

## Command-Line Arguments

- `--dataset_type`: Dataset type (covid or isic). Default: `covid`
- `--model_type`: Model architecture (densenet121 or resnet50). Default: `densenet121`
- `--model_weights`: Path to model weights file. Default: `/data/brian.hu/covid_saliency/covid_densenet121_embed_256_seed_1_epoch_20_ckpt.pth`
- `--main_path`: Path to saliency maps directory. Default: `/data/brian.hu/covid_saliency/simatt/`
- `--query_img_path`: Path to query images directory. Default: `/data/brian.hu/COVID/data/test/`
- `--csv_path`: Path to ISIC CSV file (only for isic dataset). Default: `./ISIC-2017_Test_v2_Part3_GroundTruth_balanced.csv`
- `--device`: Device to use (cuda or cpu). Default: `cuda`

## Usage Examples

### 1. Run with DenseNet121 on GPU (CUDA)
```bash
python evaluate_saliency.py \
    --model_type densenet121 \
    --model_weights /path/to/densenet121_weights.pth \
    --device cuda
```

### 2. Run with ResNet50 on GPU (CUDA)
```bash
python evaluate_saliency.py \
    --model_type resnet50 \
    --model_weights /path/to/resnet50_weights.pth \
    --device cuda
```

### 3. Run with DenseNet121 on CPU
```bash
python evaluate_saliency.py \
    --model_type densenet121 \
    --model_weights /path/to/densenet121_weights.pth \
    --device cpu
```

### 4. Run with ResNet50 on CPU
```bash
python evaluate_saliency.py \
    --model_type resnet50 \
    --model_weights /path/to/resnet50_weights.pth \
    --device cpu
```

### 5. Full example with custom paths (ISIC dataset)
```bash
python evaluate_saliency.py \
    --dataset_type isic \
    --model_type resnet50 \
    --model_weights /path/to/resnet50_weights.pth \
    --main_path /path/to/saliency_maps/ \
    --query_img_path /path/to/query_images/ \
    --csv_path ./ISIC-2017_Test_v2_Part3_GroundTruth_balanced.csv \
    --device cuda
```

## Notes

- If CUDA is not available and you specify `--device cuda`, the script will automatically fall back to CPU.
- Make sure your model weights file matches the model architecture you specify with `--model_type`.
- The script will print which device is being used at the start of execution.
