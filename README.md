# CBAM-YOLO: Enhancing Wildlife Detection in Drone Imagery

## Overview
This repository contains the implementation of **CBAM-YOLO**, a novel architecture designed to improve wildlife detection in drone imagery. The model integrates the **Convolutional Block Attention Module (CBAM)** into **YOLOv7**, aiming to enhance feature extraction and detection accuracy.

## Features
- **YOLOv7-based Architecture**: Built on the state-of-the-art YOLOv7 object detection framework.
- **CBAM Attention Mechanism**: Incorporates both **Channel and Spatial Attention Modules** to improve feature prioritization and suppress background noise.
- **WAID Dataset Utilization**: Trained and evaluated using the **WAID dataset**, a high-quality dataset for wildlife detection in UAV images.
- **Comparison with SE-YOLO**: Evaluates CBAM-YOLO against SE-YOLO, analyzing the effectiveness of different attention mechanisms.

## Research Questions
This study aims to answer the following questions:
1. Can **CBAM-YOLO** achieve comparable or superior results to the **state-of-the-art SE-YOLO** in wildlife detection?
2. Can **CBAM** serve as a viable alternative to SE attention mechanisms in YOLO architectures?
3. How do attention mechanisms impact **detection accuracy for small wildlife targets** in UAV imagery?

## Dataset
The **WAID Dataset** is used for training and evaluation. It consists of **14,375 UAV images** of various wildlife species.

### Class Distribution:
| Class   | Training | Validation | Testing | Total |
|---------|----------|-----------|---------|--------|
| Sheep   | 3602     | 349       | 173     | 4124   |
| Cattle  | 3301     | 943       | 471     | 4715   |
| Seal    | 2709     | 330       | 329     | 3368   |
| Camelus | 512      | 149       | 82      | 743    |
| Zebra   | 443      | 126       | 65      | 643    |
| Kiang   | 551      | 157       | 74      | 782    |

## Model Architecture
### 1. YOLOv7 Baseline
- Standard YOLOv7 architecture with no modifications.

### 2. CBAM-YOLO
- YOLOv7 with **CBAM blocks** integrated into the **neck layer**.
- **Channel Attention Module (CAM)**: Focuses on inter-channel dependencies.
- **Spatial Attention Module (SAM)**: Enhances spatial relationships.

## Results
### YOLOv7 Baseline Performance:
| Architecture | Precision | Recall | mAP@0.5 |
|-------------|-----------|--------|---------|
| YOLOv7 (paper) | 0.964 | 0.953  | 0.972   |
| YOLOv7 (mine)  | 0.963 | 0.953  | 0.976   |

### SE-YOLO vs CBAM-YOLO:
| Architecture | Precision | Recall | mAP@0.5 |
|-------------|-----------|--------|---------|
| SE-YOLO (paper) | 0.978 | 0.969  | 0.983   |
| SE-YOLO (mine)  | 0.940 | 0.930  | 0.956   |
| CBAM-YOLO (mine)| 0.948 | 0.920  | 0.954   |

## Key Findings
- **SE-YOLO outperformed CBAM-YOLO** for the WAID dataset, suggesting that **channel-wise attention (SE) may be more effective** than spatial attention for small wildlife targets.
- CBAM-YOLO still showed **promising results**, but the added spatial attention may introduce noise in specific cases.
- The study highlights the **importance of dataset characteristics** in determining the best attention mechanism.

## Conclusion
While **CBAM-YOLO** demonstrated competitive performance, **SE-YOLO remains the superior approach** for wildlife detection in drone imagery. Future research should explore **hybrid attention mechanisms** combining **SE and CBAM** to leverage their strengths.

## References
- Jie Hu, Li Shen, and Gang Sun. "Squeeze-and-Excitation Networks." CVPR, 2018.
- Sanghyun Woo et al. "CBAM: Convolutional Block Attention Module." ECCV, 2018.
- Kailin Jiang et al. "An Attention Mechanism-Improved YOLOv7 for Object Detection." Agriculture, 2022.

## Installation & Usage
1. Clone the repository:
   ```bash
   git clone https://github.com/your-repo/CBAM-YOLO.git
   cd CBAM-YOLO
   ```
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Train the model:
   ```bash
   python train.py --data waid.yaml --cfg yolov7-cbam.yaml --weights yolov7.pt
   ```
4. Evaluate:
   ```bash
   python test.py --weights best.pt --data waid.yaml
   ```
   
