Meshwave - Decentralized Emergency Mesh Network
Meshwave is a privacy-focused, off-grid communication tool designed for emergency situations where internet and cellular networks are unavailable. It uses Bluetooth Low Energy (BLE) and Tor (Arti) to create a resilient peer-to-peer mesh network.

Key Emergency Features:

1. "Ok Mesh" Hands-Free Voice Messaging

Designed for "unavoidable circumstances" where a user cannot manually operate their phone (e.g., trapped, injured, or busy hands).
• Wake Word Detection: Simply saying "Ok Mesh" activates the feature automatically.
• 10-Second Window: The app listens for 10 seconds of speech immediately after the wake word.
• Offline AI Transcription: Uses an embedded OpenAI Whisper Tiny engine to convert voice to text locally.
• Instant Broadcast: The resulting text is automatically broadcasted to the entire mesh network.
• Zero-Touch: No buttons need to be pressed to alert nearby responders.

2. Shake2Rescue (Handshake Emergency)

A physical-gesture-based SOS system for rapid distress signaling.
• High-G Detection: By shaking the device vigorously, the Shake2Rescue module is triggered.
• Emergency Handshake: The app instantly broadcasts a high-priority "Emergency Handshake" packet to all nodes within Bluetooth range.
• Responder Priority: These messages are flagged in the mesh to ensure they bypass standard congestion and reach every available peer.

Features

• Decentralized Messaging: No servers, no central authority.
• Offline Voice-to-Text: Hands-free emergency communication via "Ok Mesh".
• Emergency Shake: Shake the device to send an SOS broadcast with location.
• End-to-End Encryption: Powered by the Noise Protocol Framework.
• Anonymity: Optional routing through the Tor (Arti) network.
• Adaptive Power Management: Optimizes BLE scanning to preserve battery during disasters.

Requirements & Installation

PermissionsTo function correctly, especially for the Voice-to-Text feature, the following permissions are required:
• Microphone: For wake-word detection and voice recording.
• Nearby Devices (Bluetooth): For mesh networking.
• Post Notifications: To keep the Mesh Service alive in the background.

Local AI Models

Because this app is 100% offline, you must manually add the AI model files to the project before building:
1. Download the whisper-tiny.tflite model.
2. Place the file in: app/src/main/assets/models/whisper-tiny.tflite.
3. (Optional) For wake-word detection, ensure the .pv or .bin model for "Ok Mesh" is in the assets folder.

Architecture

The app follows Clean Architecture with a focus on background stability:
• MeshForegroundService: The heart of the app. It manages BLE, the Shake Detector, and the new WakeWord/STT Managers.
• SpeechToTextManager: Handles the 10-second recording buffer and interfaces with the Whisper Tiny TFLite interpreter.
• BluetoothMeshService: Handles the logic for broadcasting the transcribed strings to the network.

Development & Setup

1. Clone the repo: Shell Script
	git clone https://github.com/your-repo/meshwave-android.git
2. Build the project: Use Android Studio (Ladybug or newer) with Kotlin 1.9+.
3. Run: Install on a physical device (BLE features and Microphone detection do not work accurately on emulators).

Security & Privacy

• Local Processing: Voice data never leaves the device. The conversion from voice to text happens entirely in the        app's memory.
• Zero Metadata: We do not track who sends voice messages; only the encrypted text is shared across the mesh.

License

This project is licensed under the MIT License. See LICENSE for details.

Note: This project is intended for emergency and educational use. Always ensure you have a backup communication method in life-threatening situations.
