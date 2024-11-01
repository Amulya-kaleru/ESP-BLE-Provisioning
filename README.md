# ESP-BLE-Provisioning

Overview
This project demonstrates how to implement Wi-Fi provisioning on the ESP32 using Bluetooth Low Energy (BLE). It allows users to easily connect their ESP32 devices to Wi-Fi networks through the Espressif Wi-Fi Provisioning App.

 Key Features
- BLE-based provisioning for easy Wi-Fi configuration
- QR code generation for quick device identification
- Real-time feedback in the Serial Monitor during the provisioning process
- Automatic deletion of previous provisioning data for a clean setup

 Requirements
- ESP32 Development Board
- Espressif Wi-Fi Provisioning App (available on [Google Play Store](https://play.google.com/store/apps/details?id=com.espressif.provble))

 Code Explanation
 Key Parts of the Code
- **Provisioning Parameters**:
  - `pop`: Proof of Possession (PoP) required for authentication during provisioning.
  - `service_name`: Sets the Bluetooth device name visible to the app.
  - `service_key`: Password for SoftAP method (not required for BLE provisioning).
  - `reset_provisioned`: Erases previous provisioning data to ensure new credentials are used.

- **Event Handler (SysProvEvent)**:
  - Handles various events during the provisioning process, such as Wi-Fi connection, credential receipt, provisioning failure, and successful connection.
  - Outputs relevant logs to the Serial Monitor for debugging.

- **BLE Provisioning Setup**:
  - Initializes provisioning with BLE, using security mode 1 and a predefined PoP.
  - Generates a QR code for quick device connection via the provisioning app.

 Instructions for Uploading the Code
1. Open the Arduino IDE and copy the provided code.
2. Select the appropriate ESP32 board in the Tools menu.
3. If you encounter a "Sketch too big" error, go to **Tools > Partition Scheme** and select a partition scheme that has more than 1.4MB APP (e.g., “Huge APP (3MB No OTA/1MB SPIFFS”).
4. Upload the code to the ESP32.

 Testing the Code
1. After successfully uploading the code, open the **Serial Monitor** with a baud rate of **115200**.
2. Press the **RST button** on the ESP32 to start the program.
   > **Note**: If you see a PSRAM error, it’s safe to ignore it.
3. You should see logs in the Serial Monitor similar to:
   ```
   Begin Provisioning using BLE
   Provisioning started
   Provide Wi-Fi credentials using the smartphone app
   ```
4. Open the **Espressif Wi-Fi Provisioning App** on your smartphone.
5. Select **Provision Device**. If scanning the QR code does not work, select **I don’t have a QR code**.
6. Choose the device named **PROV_123** from the list of nearby Bluetooth devices.
7. Enter the **Proof of Possession (PoP)**. Use the default value `abcd1234`.
8. Select your Wi-Fi network from the list or choose **Join Other Network** to manually enter the SSID.
9. Enter the Wi-Fi password and press **Connect**.
10. Check the Serial Monitor for confirmation that the ESP32 has received the Wi-Fi credentials and successfully connected to the network.

Conclusion
Wi-Fi provisioning has been successfully implemented on the ESP32, allowing seamless connection to a Wi-Fi network using the Espressif provisioning app. This project can serve as a foundational example for integrating Wi-Fi capabilities into your ESP32 applications.
