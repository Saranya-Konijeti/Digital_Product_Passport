# 📷 QR Scanner Troubleshooting Guide

## ✅ What I Fixed

1. **Better Error Messages** - Shows specific error types
2. **Camera Permission Detection** - Checks permissions on component mount
3. **Debug Info Display** - Shows what's happening at each step
4. **Enhanced Error Alerts** - Clear instructions for users
5. **Console Logging** - Better debugging in browser dev tools
6. **Improved UI** - Black background for better camera preview

---

## 🔍 BEFORE YOU START

### Requirements
- **Browser:** Chrome, Edge, Firefox, or Safari (recent versions)
- **Camera:** Webcam must be connected and working
- **HTTPS or Localhost:** Localhost (http://localhost:8080) ✅ works
- **Permissions:** Browser camera permission must be granted

---

## 🛠️ TROUBLESHOOTING STEPS

### Step 1: Check Browser Support
Your browser must support `getUserMedia` API.

**Test in Browser Console:**
```javascript
// Open DevTools (F12) → Console tab → paste this:
navigator.mediaDevices.getUserMedia({ video: true })
  .then(stream => {
    console.log('✅ Camera API works!');
    stream.getTracks().forEach(track => track.stop());
  })
  .catch(err => console.error('❌ Error:', err));
```

---

### Step 2: Check Camera Permissions

#### **Chrome/Edge:**
1. Click the **Lock 🔒** icon next to URL
2. Find "Camera" permission
3. Change from "Ask" or "Block" → **Allow**
4. Refresh page

#### **Firefox:**
1. Click the **Lock 🔒** icon next to URL
2. Find "Permissions" section
3. Find Camera → Change to **Allow**
4. Refresh page

#### **Safari:**
1. Go to Safari → **Settings** (⌘ + ,)
2. Go to **Privacy** tab
3. Find **Camera** → Check websites allowed
4. Refresh page

---

### Step 3: Check if Camera Works

**Test Your Camera:**
```
Windows:
1. Open Settings → Privacy & security
2. Find Camera
3. Check if any apps have camera access
4. Try opening built-in Camera app

Mac:
1. Open Spotlight (⌘ + space)
2. Type "Photo Booth" and open
3. Check if camera works

Linux:
1. Open terminal
2. Type: `ls /dev/video*`
3. Should show video devices
```

---

### Step 4: Clear Browser Cache

Sometimes browser cache causes issues.

**Chrome/Edge:**
1. Press **Ctrl + Shift + Delete** (Windows) or **⌘ + Shift + Delete** (Mac)
2. Select "All time"
3. Check "Cookies and other site data"
4. Check "Cached images and files"
5. Click **Clear data**
6. Go back to http://localhost:8080/scan and try again

**Firefox:**
1. Press **Ctrl + Shift + Delete** (Windows) or **⌘ + Shift + Delete** (Mac)
2. Click **Clear Now**

---

### Step 5: Check Network

**If using localhost:**
- Make sure dev server is running: `npm run dev`
- Check URL: http://localhost:8080 (not https)
- Localhost ✅ does NOT require HTTPS

**If using your IP (like 192.168.x.x):**
- HTTPS ⚠️ may be required
- Try using localhost instead

---

### Step 6: Open Browser Console for Debugging

Press **F12** (or **Cmd + Option + I** on Mac) to open DevTools.

Go to **Console** tab and look for:

**✅ Good signs:**
```
Camera permission granted
Scanner ready
Point camera at QR code
Scanned: ...
```

**❌ Problems:**
```
NotAllowedError: Permission denied
NotFoundError: No camera found
NotReadableError: Camera busy/in use
```

---

## 🐛 COMMON ISSUES & SOLUTIONS

### Issue 1: "Camera permission denied"
**Causes:**
- User clicked "Block" instead of "Allow"
- Permission was never asked
- Browser is blocking camera

**Solutions:**
1. **Reset permissions:**
   - Chrome: Settings → Privacy & security → Site settings → Camera → Clear all
   - Firefox: Settings → Privacy & security → Permissions → Camera → Remove
   
2. **Try incognito/private window:**
   - Chrome: Ctrl + Shift + N (or Cmd + Shift + N on Mac)
   - Firefox: Ctrl + Shift + P (or Cmd + Shift + P on Mac)
   - Go to http://localhost:8080/scan
   - Grant permission when asked

3. **Check antivirus:**
   - Some antivirus software blocks camera access
   - Whitelist your browser or disable temporarily

---

### Issue 2: "No camera found" or "Camera not readable"

**Causes:**
- Camera is disconnected
- Camera is being used by another app
- Camera driver not installed

**Solutions:**
1. **Close other apps using camera:**
   - Zoom, Teams, OBS, Discord, etc.
   - Close all video apps and try again

2. **Check camera is connected:**
   - Try opening built-in camera app
   - Try other video apps (Zoom, Skype) to confirm camera works

3. **Update camera driver (Windows):**
   - Right-click Start → Device Manager
   - Find Cameras section
   - Right-click camera → Update driver
   - Restart computer

4. **Try different browser:**
   - If Chrome doesn't work, try Firefox or Edge

---

### Issue 3: "Camera works but doesn't scan QR codes"

**Causes:**
- QR code not in focus
- QR code too small or too far
- Camera needs better lighting
- QR code is damaged

**Solutions:**
1. **Position QR code properly:**
   - Hold QR code 10-20cm from camera
   - Make sure it's in the center frame
   - Try different angles

2. **Improve lighting:**
   - Ensure good lighting on QR code
   - Avoid glare and shadows
   - Move to brighter location

3. **Test with a standard QR code:**
   - Open https://www.qr-code-generator.com/
   - Generate a simple QR code
   - Try scanning that instead

4. **Check QR code validity:**
   - Make sure QR code is not damaged/faded
   - Try printing a new one or displaying on screen

---

### Issue 4: "Scanner works on phone but not on desktop"

**Causes:**
- Desktop camera has issues
- Mobile browser permissions differ
- Port/network issue

**Solutions:**
1. **Try different device:**
   - Test on phone/tablet
   - If it works there, desktop camera might be the issue

2. **Use phone's camera instead:**
   - Open http://your-computer-ip:8080/scan on phone
   - Grant camera permission
   - This should work better

---

## 📱 USING ON MOBILE/PHONE

**To access from phone:**

1. **Find your computer IP:**
   ```
   Windows:
   - Open Command Prompt
   - Type: ipconfig
   - Look for IPv4 Address (usually 192.168.x.x)
   
   Mac:
   - System Preferences → Network
   - Look for IP address
   
   Linux:
   - Open terminal
   - Type: hostname -I
   ```

2. **On phone, go to:**
   ```
   http://YOUR_COMPUTER_IP:8080
   Example: http://192.168.1.100:8080
   ```

3. **Grant camera permission when asked**

4. **Try scanning QR codes**

---

## 🔧 TECHNICAL DETAILS

### What the Scanner Does:
1. **Checks** if browser supports `getUserMedia` API
2. **Requests** camera permission
3. **Initializes** html5-qrcode library
4. **Streams** camera video in real-time
5. **Detects** QR codes in video feed
6. **Returns** QR code content (URL or product ID)

### Backend Requirements:
- **html5-qrcode** library ✅ installed
- **Camera device** accessible
- **Permissions** granted by user
- **Localhost or HTTPS** (for security)

---

## 🆘 IF NOTHING WORKS

### Open Browser Console and Check for Errors:

1. Press **F12** to open DevTools
2. Go to **Console** tab
3. Look for red error messages
4. Copy-paste the error here

### Common Error Messages:

**Error: `NotAllowedError: Permission denied`**
- Solution: Grant camera permission in browser settings

**Error: `NotFoundError: Requested device not found`**
- Solution: Check camera is connected and working

**Error: `TypeError: navigator.mediaDevices is undefined`**
- Solution: Your browser doesn't support camera API
- Try Chrome, Firefox, or Edge instead

**Error: `Html5QrcodeScanner is not a function`**
- Solution: html5-qrcode library not loaded properly
- Run: `npm install html5-qrcode`
- Restart: `npm run dev`

---

## ✅ TEST CHECKLIST

- [ ] Browser is Chrome, Firefox, Edge, or Safari
- [ ] Camera is connected and working
- [ ] Camera permission is ALLOWED in browser
- [ ] No other app is using camera
- [ ] Running on http://localhost:8080 (not https)
- [ ] npm run dev is running
- [ ] Browser console shows no red errors
- [ ] You can see camera preview when clicking "Start Camera Scanner"
- [ ] Debug info shows "Scanner ready"

---

## 🆘 If You Still Have Issues:

1. **Open Browser Console** (F12)
2. **Check for error messages**
3. **Take a screenshot** of:
   - The error message
   - Browser address bar showing localhost:8080
4. **Try on a different browser** (Chrome if using Firefox, etc.)
5. **Restart dev server**: Stop (Ctrl+C) and run `npm run dev` again

---

## 📞 Quick Fix Checklist

```
❌ Camera not working?
→ Check if connected
→ Close other apps using camera
→ Restart browser

❌ Permission denied?
→ Clear browser cache (Ctrl+Shift+Delete)
→ Check browser settings
→ Try incognito window

❌ QR not scanning?
→ Position closer to camera
→ Improve lighting
→ Try different QR code
→ Check QR code validity

❌ Still not working?
→ Open F12 console
→ Check for error messages
→ Restart npm dev server
→ Try different browser
```

---

**Last Updated:** January 24, 2026  
**Status:** Enhanced with better debugging
