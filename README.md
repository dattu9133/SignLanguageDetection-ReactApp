## Sign Language Detection Model README

This repository contains code and resources to build a sign language detection model using TensorFlow Object Detection API, OpenCV, LabelImg, and Protocol Buffers.

### Features
- Converts TensorFlow models to TensorFlow.js for real-time detection with improved processing speed.
- Deploys the model on IBM Cloud as an API, supporting over 10,000 requests per day.
- Includes a React frontend for real-time detection achieving approximately 90% accuracy.

### Getting Started

#### Clone the Repository
```bash
git clone https://github.com/dattu9133/SignLanguageDetection-ReactApp
cd sign_language_detection
```

#### Setting Up the Environment

1. **Install Dependencies:**
   ```bash
   pip install -r requirements.txt
   npm install
   ```

2. **Download TensorFlow Object Detection API:**
   Follow the [installation instructions](https://github.com/tensorflow/models/blob/master/research/object_detection/g3doc/tf2.md) to set up the TensorFlow Object Detection API.

3. **Labeling Images:**
   Use LabelImg to annotate images and generate XML files compatible with TensorFlow Object Detection API.

#### Training the Model

1. **Prepare Data:**
   Organize annotated images and XML files in the required format.

2. **Configuration:**
   Modify the configuration files in the `models/research/object_detection/configs` directory to suit your dataset and requirements.

3. **Training:**
   Run the training script:
   ```bash
   python Tensorflow/models/research/object_detection/model_main_tf2.py
      --model_dir=Tensorflow/workspace/models/my_ssd_mobnet
      --pipeline_config_path=Tensorflow/workspace/models/my_ssd_mobnet/pipeline.config
      --num_train_steps=20000
   ```

#### Converting to TensorFlow.js

1. **Convert Model:**
   Convert the TensorFlow model to TensorFlow.js for deployment:
   ```bash
    tensorflowjs_converter
   --input_format=tf_saved_model
   --output_node_names=
   'detection_boxes,detection_classes,detection_features,detection_multiclass_scores,detection_scores,num_detections,raw_detection_boxes,raw_detection_scores'
    --output_format=tfjs_graph_model
   --signature_name=serving_default
   Tensorflow/workspace/models/my_ssd_mobnet/export/saved_model
   Tensorflow/workspace/models/my_ssd_mobnet/converted
   ```

#### Deploying on IBM Cloud

1. **Create API:**
   Deploy the TensorFlow.js model as an API on IBM Cloud using Cloud Functions or Cloud Foundry.

2. **Scaling:**
   Configure IBM Cloud to handle over 10,000 requests per day based on your model's requirements.

#### React Frontend

1. **Install Dependencies:**
   ```bash
   npm install
   ```

2. **Run Development Server:**
   ```bash
   npm start
   ```

3. **Access the Application:**
   Open your browser and navigate to `http://localhost:3000` to use the real-time sign language detection frontend.

### Contributing

1. Fork the repository and create a new branch.
2. Make your changes and test them thoroughly.
3. Create a pull request with a detailed description of your contributions.

### License

This project is licensed under the MIT License - see the LICENSE file for details.

### Acknowledgments

- TensorFlow Object Detection API contributors
- OpenCV community
- LabelImg developers

For detailed instructions on cloning and updating this repository, please refer to the sections above.
