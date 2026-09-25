⌚ ESP32-C3 Single-Button Smartwatch OS

A feature-rich, ultra-low-power smartwatch firmware built for the ESP32-C3. This project transforms a standard ESP32-C3 and an SSD1306 OLED into a fully functional smartwatch operated entirely by a single tactile button.

It features an Always-On Display (AOD) mode, deep sleep power management, built-in applications, and a standalone Wi-Fi Web Portal for wireless configuration and time synchronization.

✨ Features

Single-Button OS: A custom input engine distinguishing between instant single clicks, double clicks, and long holds without lag.

Deep Sleep & AOD: Maximizes battery life using ESP32 deep sleep, with an optional customizable Always-On Display.

Built-in Applications: Includes a Stopwatch, 3D animated Coin Flipper, side-scrolling Dino Jump game, and a Secure Text Vault.

Wi-Fi Web Dashboard: Hold the button to broadcast an Access Point. Access the sleek dark-mode portal at 192.168.4.1 to change settings, upload text notes, and view live telemetry.

Auto Time-Sync: Opening the web dashboard on your phone automatically syncs the watch to your phone's exact local time in the background.

🔌 Hardware Connections

Tactile Button: GPIO 4 (Connect one side to GPIO 4, other to GND. The code uses the internal pull-up resistor).

Battery ADC: GPIO 1 (Used for battery voltage monitoring via voltage divider).

OLED SDA: GPIO 8 (I2C Data Line for the SSD1306 display).

OLED SCL: GPIO 9 (I2C Clock Line for the SSD1306 display).

OLED VCC/GND: 3.3V / GND (Power for the display).

📚 Libraries Required

Make sure to install the following libraries via the Arduino Library Manager before compiling:

U8g2 by oliver (For OLED display rendering)

Preferences (Included in ESP32 Core - for saving AOD/Brightness settings)

LittleFS (Included in ESP32 Core - for saving uploaded text files)

WiFi & WebServer (Included in ESP32 Core)

⚙️ Software Setup & Flashing

Open the sketch in the Arduino IDE.

Under Tools > Board, select ESP32C3 Dev Module.

Under Tools > Partition Scheme, select a scheme that includes data storage (e.g., "Default 4MB with spiffs"). This is strictly required for the Text Vault to save files.

Edit the Personal Information section at the top of the code to add your Name, Phone Number, and Instagram ID.

Compile and upload!

🎮 Navigation & Button Controls

The OS relies on a smart timing engine to handle inputs effortlessly.

Main System Navigation

Single Click: Cycle to the next screen. (Instantly wakes the watch if the screen is dimmed).

Hold (2 Seconds):

On the System Status page: Enters AOD configuration mode.

On any other page: Turns on the Wi-Fi Access Point (C3_Mini_Watch).

App Controls (Game, Coin Toss, Stopwatch, Text Vault)

When viewing an app's splash screen:

Double Click: Opens/Starts the application.

Single Click: Skips to the next screen.

When inside an active app:

Single Click: Action button (Jump, Toss Coin, Start/Stop time, scroll text).

Double Click (Stopwatch only): Resets the timer.

Hold (2 Seconds): Safely exits the application and returns to the Home Clock.

📱 The Web Dashboard

To access the settings:

Hold the watch button for 2 seconds until the Wi-Fi screen appears.

On your phone or PC, connect to the Wi-Fi network C3_Mini_Watch (Password: 12345678).

Open a browser and navigate to 192.168.4.1.

The dashboard allows you to:

View live battery and core temperature telemetry.

Adjust Active and AOD brightness sliders.

Set screen timeout durations.

Upload .txt files directly into the watch's Secure Text Vault.

Note: The Wi-Fi portal has an automatic 60-second timeout. If no device connects, or if a connected device disconnects, the watch will automatically shut down the Wi-Fi radio to save battery.
