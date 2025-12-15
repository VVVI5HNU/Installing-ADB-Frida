### 📥 1. Install ADB (Android Debug Bridge)

#### **On Kali Linux / Ubuntu**
ADB is available via package manager:
```
sudo apt update
sudo apt install android-tools-adb android-tools-fastboot
```

#### **On macOS (Homebrew)**
```
brew install android-platform-tools
```

#### **Verify installation**
```
adb version
```

---

### 📥 2. Install Frida (Host Machine)

Frida consists of two parts:
1. **frida-tools** → installed on your computer  
2. **frida-server** → runs on Android device  


#### **Install Frida tools on Kali/Linux/macOS**
```
pip install frida-tools
```

#### **Verify installation**
```
frida --version
```

---

### 📥 3. Download frida-server (for your Android device)

1. Go to the official Frida releases page:  
   👉 https://github.com/frida/frida/releases  
2. Download the frida-server file matching your device architecture:
   - arm  
   - arm64  
   - x86  
   - x86_64
   - 
#### **To Check Device Architecture**
Connect your device and run this command in adb shell
```
getprop ro.product.cpu.abi
```

Example filename:  
```
frida-server-16.1.3-android-arm64.xz
```

3. Extract it:
```
unxz frida-server-*.xz
chmod +x frida-server-*
```

---

### 📥 4. Push frida-server to the device

```
adb push frida-server /data/local/tmp/
adb shell
su
chmod 755 /data/local/tmp/frida-server
```

---

### ▶️ 5. Start Frida server on the device
```
/data/local/tmp/frida-server &
```

---

### 📶 6. Confirm Frida connection
On your computer:
```
frida-ps -aU
```

If you see a list of running apps, setup is complete.

---

