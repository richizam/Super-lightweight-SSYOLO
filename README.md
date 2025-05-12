SS-YOLO 🔎🦾

```bash
# 1. Clone
git clone https://github.com/richizam/Super-lightweight-SSYOLO.git
cd Super-lightweight-SSYOLO

# 2. Install
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt        # Python ≥3.9, CUDA 11.x

# 3. Prepare NEU-DET
bash scripts/download_neudet.sh        # or place dataset in ./NEUDET
python scripts/split_dataset.py        # creates ./NEUDET_split (80/10/10)

# 4. Train
python yolov7/train.py \
  --data configs/neudet.yaml \
  --cfg  configs/ssyolo-tiny.yaml \
  --weights '' --device 0 --batch-size 32 --epochs 300

# 5. Inference
python yolov7/detect.py --weights runs/train/exp/weights/best.pt \
  --source sample_images/ --img 640 --conf-thres 0.25

SS-YOLO (ours)	9.7 M	parameters with 82.7 %
