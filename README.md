
# TensorFlow Object Detection Project

signs to words: sign language gesture détection demonstrates the use of TensorFlow Object Detection API to detect objects in images. The model is trained on custom image datasets with annotations for five categories: `bonjour`, `cava`, `merci`, `non`, and `oui`.

## Project Structure

```
TFOD/
│
├── Tensorflow/
│   ├── models/                     # TensorFlow models and configurations
│   ├── protoc/                     # Protocol Buffers
│   ├── scripts/                    # Scripts for data processing
│   ├── workspace/
│       ├── annotations/            # Label annotations for images (.xml format)
│       ├── images/                 # Dataset images organized by folders:
│       │   ├── collectedimages/    # Raw collected images
│       │   ├── train/              # Training images and annotations
│       │   └── test/               # Testing images and annotations
│       ├── models/                 # Trained models and checkpoints
│       └── pre-trained-models/     # Pre-trained models used for transfer learning
├── tfod.ipynb                      # Main Jupyter notebook file for training and evaluation
└── archive.tar.gz                  # Archived project files
```

## Dataset

The dataset consists of images collected for five different classes:

- **bonjour**
- **cava**
- **merci**
- **non**
- **oui**

Each image is associated with an XML annotation file (created using [LabelImg](https://github.com/tzutalin/labelImg)) that specifies the bounding boxes around the objects of interest.

### Example Image/Annotation Files:

```
images/
└── test/
    ├── bonjour.4b2268a6-a2b5-11eb-a0a2-005056c00008.jpg
    ├── bonjour.4b2268a6-a2b5-11eb-a0a2-005056c00008.xml
    ├── cava.6aa38e9c-a2b5-11eb-8ebc-005056c00008.jpg
    ├── cava.6aa38e9c-a2b5-11eb-8ebc-005056c00008.xml
    └── ...
```

## Model

The model used is `ssd_mobilenet_v2_fpnlite_320x320`, which is pre-trained on the COCO dataset and fine-tuned on the custom dataset. The model files are downloaded from the TensorFlow Model Zoo.

### Model Files:

```
workspace/
└── models/
    └── my_ssd_mobnet/
        ├── checkpoint/
        ├── saved_model/
        └── pipeline.config
```

## Installation

1. Clone the TensorFlow models repository:

   ```bash
   git clone https://github.com/tensorflow/models
   ```

2. Install TensorFlow Object Detection API and other dependencies as described in the `tfod.ipynb` notebook.

3. Prepare the environment:

   ```bash
   pip install -r requirements.txt
   ```

4. Compile protocol buffers:

   ```bash
   protoc object_detection/protos/*.proto --python_out=.
   ```

5. Run the training and evaluation in the Jupyter notebook `tfod.ipynb`.

## Usage

1. **Training the Model**: Follow the steps in `tfod.ipynb` to train the model on your custom dataset.
2. **Testing**: After training, use the test images in the `test/` folder to evaluate the model.

## Labels

The label map file `label_map.pbtxt` includes the five object classes:

```text
item {
    id: 1
    name: 'bonjour'
}
item {
    id: 2
    name: 'cava'
}
item {
    id: 3
    name: 'merci'
}
item {
    id: 4
    name: 'non'
}
item {
    id: 5
    name: 'oui'
}
```

## Contributions

Feel free to open issues or pull requests if you have any improvements or suggestions.

---

Happy detecting!
