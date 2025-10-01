# Egyptian Currency Detection App

A Flutter-based mobile application for real-time detection and recognition of Egyptian currency using YOLOv8 deep learning model. This app provides accurate currency identification through both live camera feed and static images.

## 🎯 Features

- **Real-time Currency Detection**: Live camera stream detection with YOLOv8
- **Image-based Detection**: Upload images from gallery for currency recognition
- **OCR Capabilities**: Text extraction using Tesseract OCR
- **High Accuracy**: Custom-trained YOLOv8 model specifically for Egyptian currency
- **User-friendly Interface**: Intuitive floating action button menu for easy navigation

## 💰 Supported Currency Denominations

The app can detect the following Egyptian Pound denominations:

- 0.25 Pound (Quarter Pound)
- 0.50 Pound (Half Pound)
- 1 Pound
- 5 Pounds
- 10 Pounds
- 20 Pounds
- 50 Pounds
- 100 Pounds
- 200 Pounds

Both new and old versions of coins and banknotes are supported.

## 🛠️ Technologies Used

- **Flutter**: Cross-platform mobile development framework
- **YOLOv8**: State-of-the-art object detection model
- **Flutter Vision**: Flutter plugin for AI vision tasks
- **Camera Plugin**: Real-time camera access and image streaming
- **Tesseract OCR**: Optical character recognition for text extraction
- **Image Picker**: Gallery and camera image selection

## 📋 Prerequisites

Before running this application, ensure you have the following installed:

- Flutter SDK (latest stable version)
- Dart SDK
- Android Studio / Xcode (for mobile development)
- Android SDK (API level 21 or higher) or iOS 11.0+

## 🚀 Installation

1. **Clone the repository**
```bash
git clone <repository-url>
cd fluttrt_project_stream
```

2. **Install dependencies**
```bash
flutter pub get
```

3. **Add the YOLOv8 model**
   - Place your trained `yolov8n.tflite` model in the `assets/` directory
   - Ensure `labels.txt` is present with all currency labels

4. **Update pubspec.yaml**
   - Verify all assets are declared in `pubspec.yaml`:
```yaml
flutter:
  assets:
    - assets/yolov8n.tflite
    - assets/labels.txt
```

5. **Run the app**
```bash
flutter run
```

## 📱 Usage

### Live Detection Mode
1. Launch the app
2. Tap the floating menu button
3. Select "Yolo on Frame" (red camera icon)
4. Point your camera at Egyptian currency
5. Press the play button to start detection
6. Detection boxes will appear around recognized currency with confidence scores
7. Press the stop button to pause detection

### Image Detection Mode
1. Launch the app
2. Tap the floating menu button
3. Select "Yolo on Image" (blue camera icon)
4. Tap "Pick image" to select an image from gallery
5. Tap "Detect" to run currency detection
6. View results with bounding boxes and labels

### Text Recognition Mode
1. Launch the app
2. Tap the floating menu button
3. Select "Tesseract" (green text icon)
4. Pick an image containing text
5. Tap "Get Text" to extract text from the image

## 🏗️ Project Structure

```
fluttrt_project_stream/
├── android/                 # Android native code
├── ios/                    # iOS native code
├── assets/                 # Model and label files
│   ├── yolov8n.tflite     # YOLOv8 model
│   └── labels.txt         # Currency labels
├── lib/
│   └── main.dart          # Main application code
└── pubspec.yaml           # Dependencies
```

## ⚙️ Configuration

### Model Parameters
You can adjust detection parameters in the code:

```dart
await vision.yoloOnFrame(
  iouThreshold: 0.4,      // Intersection over Union threshold
  confThreshold: 0.4,     // Confidence threshold
  classThreshold: 0.5     // Class probability threshold
);
```

### Camera Settings
Modify camera resolution in `_YoloVideoState.init()`:
```dart
controller = CameraController(cameras[0], ResolutionPreset.low);
```

Available presets: `low`, `medium`, `high`, `veryHigh`, `ultraHigh`, `max`

## 📊 Model Training

The YOLOv8 model was custom-trained on a dataset of Egyptian currency. The training process included:

1. Data collection of various Egyptian currency denominations
2. Image annotation with bounding boxes
3. Model training using YOLOv8 architecture
4. Conversion to TensorFlow Lite format for mobile deployment
5. Optimization for real-time inference

## 🔧 Troubleshooting

### Model Not Loading
- Verify `yolov8n.tflite` and `labels.txt` are in the `assets/` folder
- Check that assets are declared in `pubspec.yaml`
- Run `flutter clean` and `flutter pub get`

### Camera Permission Issues
- Ensure camera permissions are granted in device settings
- Check AndroidManifest.xml includes camera permissions

### Low Detection Accuracy
- Ensure good lighting conditions
- Keep camera steady and at appropriate distance
- Adjust threshold values for better sensitivity
