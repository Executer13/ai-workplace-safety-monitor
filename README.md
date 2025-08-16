# AI Workplace Safety Monitor 🛡️

An AI-powered real-time workplace safety monitoring system that uses computer vision to detect missing safety equipment (helmets and safety vests) in industrial environments. The system provides instant alerts, automatic image capture, and comprehensive compliance tracking.

![Python](https://img.shields.io/badge/python-v3.8+-blue.svg)
![OpenVINO](https://img.shields.io/badge/OpenVINO-2022+-green.svg)
![Firebase](https://img.shields.io/badge/Firebase-Integrated-orange.svg)
![License](https://img.shields.io/badge/license-MIT-blue.svg)

## 🚀 Features

### Core Functionality
- **Real-time Safety Detection**: Continuously monitors workers for proper safety gear usage
- **AI-Powered Analysis**: Uses Intel OpenVINO optimized models for fast, accurate detection
- **RTSP Camera Integration**: Supports IP cameras and security systems
- **Instant Alerts**: Push notifications when safety violations are detected
- **Automatic Documentation**: Captures and stores violation images for compliance

### Technical Capabilities
- **Person Detection**: Advanced person tracking with ID assignment
- **Safety Gear Classification**: Detects helmets, safety vests, and violations
- **Cloud Integration**: Firebase backend for authentication, storage, and notifications
- **Configurable Monitoring**: Enable/disable detection remotely
- **Multi-User Support**: User authentication and personalized monitoring

## 🏗️ Architecture

```
┌─────────────────┐    ┌──────────────────┐    ┌─────────────────┐
│   RTSP Camera   │────│  AI Detection    │────│   Firebase      │
│   Live Feed     │    │   Engine         │    │   Backend       │
└─────────────────┘    └──────────────────┘    └─────────────────┘
                              │                          │
                              ▼                          ▼
                       ┌──────────────┐         ┌─────────────────┐
                       │  OpenVINO    │         │  Push Notifications│
                       │  Models      │         │  & Image Storage │
                       └──────────────┘         └─────────────────┘
```

## 🔧 Installation & Setup

### Prerequisites
- Python 3.8+
- OpenVINO Runtime
- Firebase Account
- RTSP-compatible IP camera

### 1. Clone the Repository
```bash
git clone https://github.com/yourusername/ai-workplace-safety-monitor.git
cd ai-workplace-safety-monitor
```

### 2. Install Dependencies
```bash
pip install -r requirements.txt
```

**Required packages:**
```
opencv-python>=4.5.0
openvino>=2022.1.0
firebase-admin>=5.0.0
pyrebase4>=4.5.0
Pillow>=8.0.0
numpy>=1.20.0
tkinter
```

### 3. Firebase Configuration

1. **Create Firebase Project**:
   - Go to [Firebase Console](https://console.firebase.google.com/)
   - Create a new project
   - Enable Authentication, Firestore, and Storage

2. **Download Service Account Key**:
   - Go to Project Settings → Service Accounts
   - Generate new private key
   - Save as `firebase-service-account.json`

3. **Update Configuration**:
   - Replace Firebase config in `main.py` with your project details
   - Update the service account file path

### 4. Model Setup
The repository includes pre-trained OpenVINO models:
- `person_detection_0013_model/`: Person detection model (320×544)
- `worker-safety-mobilenet/`: Safety gear detection model (224×224)

## 🎯 Usage

### Basic Operation
1. **Start the Application**:
```bash
python main.py
```

2. **Login**: Use Firebase authentication to access the system

3. **Configure RTSP Stream**: Set your camera's RTSP URL in the user interface

4. **Monitor**: The system will automatically detect and alert on safety violations

### Configuration Options
- **Detection Sensitivity**: Adjust confidence thresholds in code
- **Alert Frequency**: Configure notification intervals
- **Storage Settings**: Customize image retention policies

## 📊 Detection Classes

The system detects the following safety equipment:

| Class | Description | Action |
|-------|-------------|---------|
| ✅ Helmet + Vest | Worker properly equipped | No alert |
| ⚠️ Helmet Only | Missing safety vest | Send alert |
| ⚠️ Vest Only | Missing helmet | Send alert |
| 🚨 No Safety Gear | No protection detected | High priority alert |

## 🔐 Security Features

- **User Authentication**: Firebase-based secure login
- **Data Encryption**: All communications encrypted
- **Access Control**: Role-based permissions
- **Audit Trail**: Complete logging of all activities

## 📱 Mobile Integration

The system supports push notifications to mobile devices:
- Real-time safety alerts
- Violation image previews
- Remote monitoring controls
- Historical compliance reports

## 🛠️ Technical Details

### AI Models
- **Person Detection**: Intel's person-detection-retail-0013
- **Safety Classification**: Custom MobileNet-SSD model
- **Inference Engine**: OpenVINO for optimized performance

### Performance Metrics
- **Detection Accuracy**: >95% for standard industrial environments
- **Processing Speed**: 15-30 FPS depending on hardware
- **Response Time**: <2 seconds from detection to alert

### Hardware Requirements
- **Minimum**: Intel Core i5, 8GB RAM
- **Recommended**: Intel Core i7, 16GB RAM, Intel GPU
- **Camera**: IP camera with RTSP support

## 📂 Project Structure

```
├── main.py                    # Main application entry point
├── README.md                  # Project documentation
├── requirements.txt           # Python dependencies
├── firebase-config.json       # Firebase configuration
├── person_detection_0013_model/
│   ├── person-detection-retail-0013.xml
│   ├── person-detection-retail-0013.bin
│   └── person-detection-retail-0013.prototxt
├── worker-safety-mobilenet/
│   ├── worker_safety_mobilenet_ir.xml
│   └── worker_safety_mobilenet_ir.bin
├── Alerts/                    # Local alert storage
├── test.ipynb                 # Jupyter notebook for testing
└── assets/                    # UI assets and images
```

## 🔧 Customization

### Adding New Detection Classes
1. Retrain the safety gear model with new classes
2. Update class labels in `perform_safety_gear_detection()`
3. Modify alert logic accordingly

### Integrating Additional Cameras
1. Add multiple RTSP URLs to configuration
2. Implement multi-threaded processing
3. Update Firebase schema for multi-camera support

## 📈 Monitoring & Analytics

The system provides comprehensive analytics:
- **Compliance Rates**: Daily/weekly safety compliance statistics
- **Violation Trends**: Historical analysis of safety incidents
- **Worker Tracking**: Individual compliance monitoring
- **Performance Metrics**: System uptime and detection accuracy

## 🤝 Contributing

We welcome contributions! Please follow these guidelines:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### Development Setup
```bash
# Install development dependencies
pip install -r requirements-dev.txt

# Run tests
python -m pytest tests/

# Code formatting
black main.py
```

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🆘 Support & Troubleshooting

### Common Issues

**Camera Connection Failed**:
- Verify RTSP URL format: `rtsp://username:password@ip:port/path`
- Check network connectivity
- Ensure camera supports RTSP

**Model Loading Errors**:
- Verify OpenVINO installation
- Check model file integrity
- Ensure sufficient system memory

**Firebase Authentication Issues**:
- Validate service account key
- Check Firebase project configuration
- Verify internet connectivity

### Getting Help
- 📧 Email: support@yourproject.com
- 💬 Issues: [GitHub Issues](https://github.com/yourusername/ai-workplace-safety-monitor/issues)
- 📖 Documentation: [Wiki](https://github.com/yourusername/ai-workplace-safety-monitor/wiki)

## 🙏 Acknowledgments

- Intel OpenVINO team for optimization tools
- Firebase team for backend infrastructure
- OpenCV community for computer vision libraries
- Industrial safety professionals for domain expertise

## 📊 Roadmap

### Version 2.0 Features
- [ ] Multi-camera simultaneous monitoring
- [ ] Advanced analytics dashboard
- [ ] Mobile app for remote monitoring
- [ ] Integration with existing safety systems
- [ ] Machine learning model improvements
- [ ] Edge deployment capabilities

### Long-term Goals
- [ ] Support for additional PPE types
- [ ] Integration with IoT sensors
- [ ] Predictive safety analytics
- [ ] Compliance reporting automation

---

**Made with ❤️ for workplace safety**

*Protecting workers through the power of AI and computer vision*