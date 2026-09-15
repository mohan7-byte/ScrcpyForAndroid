# Scrcpy for Android (Screen Off Feature)

- This application is android port to desktop application [**Scrcpy**](https://github.com/Genymobile/scrcpy).

- This application mirrors display and touch controls from a remote android device to android device.

- Scrcpy for Android uses the ADB interface to connect to the android device to be mirrored, either over the network (WiFi) or over a USB cable.

## New Feature: Screen Off Button ⭐

**Perfect for devices with broken/damaged screens!**

- **Screen Off Button**: Turn off the physical screen of the remote device while continuing to control it
- Your local screen remains ON for viewing and control
- Remote device's physical screen goes OFF completely
- **Solves Ghost Touch Problem**: If your remote device has screen damage causing ghost touches, turning off the physical screen eliminates all touch interference
- The device stays responsive to ADB commands even when screen is off

### How to Use Screen Off Feature:

1. Connect to your remote device via WiFi or USB (as usual)
2. Look for the new "Screen Off" button in the control panel
3. Tap "Screen Off" to turn off the remote device's physical display
4. Your local screen will still show the remote device's last display state
5. You can still control the device completely via touch/keyboard
6. Tap "Screen Off" again or any wake-up button to turn the screen back on

### Real-World Usage Example:

```
Your Phone (Control Panel + Scrcpy)  ← WiFi/USB ← Redmi (Broken Screen, Ghost Touches)

You can:
✅ See Redmi's screen on your phone
✅ Control Redmi's apps by touching
✅ Turn OFF Redmi's physical screen (eliminates ghost touches)
✅ Still control Redmi via ADB commands
```

## Download

[scrcpy-release.apk](https://github.com/mohan7-byte/ScrcpyForAndroid/releases)

## Instructions to use (WiFi)

- Make sure both devices are on same local network.
- Enable **ADB-connect/ADB-wireless/ADB over network** on the device to be mirrored. 
- Open scrcpy-android app and enter ip address of device to be mirrored.
- Select display parameters and bitrate from drop-down menu(1280x720 and 2Mbps works best).
- Set **Navbar** switch if the device to be mirrored has only hardware navigation buttons.
- Hit **start** button.
- Accept and trust(check always allow from this computer) the ADB connection prompt on target device(Some custom roms don't have this prompt).
- Thats all! You should be seeing the screen of remote android device.
- To wake up the remote device, **double tap anywhere on screen**.
- **To turn OFF the remote device's screen, use the new "Screen Off" button** (prevents ghost touches).
- To bring back the local android system navbar while mirroring the remote device, **swipe up from the bottom edge of screen**.

## Instructions to use (USB)

- Connect the target device to this phone with a USB cable (USB-C to USB-C, or an OTG adapter).
- Enable **USB debugging** in Developer options on the target device.
- Open the app. When an ADB-capable USB device is detected, the address field is automatically pre-selected to `USB: <device>`.
  - You can also tap the address drop-down and choose the `USB:` entry manually.
- Select display parameters and bitrate from the drop-down menus, same as the WiFi flow.
- Hit **start**.
- Grant the USB permission prompt on this phone, then accept the **Allow USB debugging?** prompt on the target device (check *Always allow from this computer* to skip it next time).
- **Use the "Screen Off" button to turn off the remote device's physical screen**.

## Connecting to public network devices

>  The public network port of the device needs to be open for access

### Connection Example

- 192.168.1.222
- host.example.com:5555
- [2000:2000:2000:2000::2000]:5555

## Code Reference

- [Original scrcpy-android](https://gitlab.com/las2mile/scrcpy-android)
- [zwc456baby/ScrcpyForAndroid](https://github.com/zwc456baby/ScrcpyForAndroid)
- [scrcpy (Official)](https://github.com/Genymobile/scrcpy)

## Changes Made in This Fork

### Screen Off Feature Implementation:

1. **New Button**: "Screen Off (ADB)" button added to the main UI
2. **Logic**: Uses ADB command `input keyevent 26` to simulate power button press (turns screen off without powering off device)
3. **Confirmation Dialog**: Shows device address before executing to prevent accidental screen offs
4. **Status Feedback**: Toast notification confirms screen off command was sent
5. **Easy Recovery**: Tap the button again or tap screen to wake device up

### Files Modified:

1. `app/src/main/res/layout/activity_main.xml` - Added new Screen Off button
2. `app/src/main/res/values/strings.xml` - Added new string resources for Screen Off feature
3. `app/src/main/java/org/client/scrcpy/MainActivity.java` - Added screen off logic and button listener

## Why This Fork?

The original Scrcpy for Android app puts device to sleep using proximity sensor, which is complex and unreliable. This fork adds a **dedicated, easy-to-use "Screen Off" button** that:

- ✅ Works with any Android device
- ✅ No proximity sensor needed
- ✅ One-click screen off
- ✅ Perfect for devices with broken screens (eliminates ghost touches)
- ✅ Device remains responsive to ADB/Scrcpy commands
- ✅ Same code base as original, just with added convenience

## License

GNU General Public License v3.0 (GPL-3.0)

Same as the original scrcpy-android project
