### **Flagyard QRRR! Forensics Challenge Writeup**


**Challenge Name:** Flagyard QRRR! Forensics

**Category:** Forensics

**Difficulty:** Medium


## **Challenge Description**

In the **Flagyard QRRR! Forensics** challenge, we were provided with a GIF file containing over 50 QR codes. Our task was to extract and scan these QR codes to uncover a hidden flag.


## **Approach and Solution**

### **Step 1: Extract Frames from the GIF**

Given that the QR codes were embedded within a GIF, the first step was to extract each frame of the GIF as a separate image.

**Tools Used:**
- **Python** with the **Pillow** library.

**Code:**
```python
from PIL import Image, ImageSequence
import os

gif_path = r"/path_to_gif/QRRR!.gif"
output_folder = r"/path_to_output_frames"

# Create the output directory if it doesn't exist
if not os.path.exists(output_folder):
    os.makedirs(output_folder)

# Open the GIF file and extract frames
with Image.open(gif_path) as gif:
    for frame_number, frame in enumerate(ImageSequence.Iterator(gif)):
        frame.save(f"{output_folder}/frame_{frame_number}.png", format="PNG")

print(f"Extracted {frame_number + 1} frames from the GIF.")
```

**Outcome:**
- We successfully extracted all the frames, which were saved as individual PNG files.

### **Step 2: Scan the Extracted QR Codes**

Next, we needed to scan each of these extracted frames for QR codes to decode the hidden messages.

**Tools Used:**
- **Python** with the **OpenCV** library (as `pyzbar` had dependency issues).

**Code:**
```python
import cv2
import os

frames_folder = r"/path_to_output_frames"

# Loop through each PNG file and scan for QR codes
for filename in os.listdir(frames_folder):
    if filename.endswith(".png"):
        img_path = os.path.join(frames_folder, filename)
        img = cv2.imread(img_path)
        
        # Initialize the QRCode detector
        detector = cv2.QRCodeDetector()
        
        # Detect and decode
        data, vertices_array, binary_qrcode = detector.detectAndDecode(img)
        
        if data:
            print(f"{filename}: {data}")
        else:
            print(f"{filename}: No QR code found")

print("QR code scanning complete.")
```

**Outcome:**
- We successfully scanned all frames and extracted the encoded data from the QR codes.

### **Step 3: Decode the QR Code Messages**

The QR code messages followed a pattern:
```
SyntL{...}
```
Recognizing this, we applied a **ROT13 cipher** to decode the messages.

**Analysis:**
- `SyntL` decoded to `FlagY`.
- The content inside `{...}` was also ROT13 encoded.

**Decoding Example:**
```python
import codecs

encoded_message = "SyntL{Pbatengf_h_tbg_vggg}"
decoded_prefix = codecs.decode(encoded_message[:5], 'rot_13')
decoded_content = codecs.decode(encoded_message[5:], 'rot_13')
decoded_message = f"{decoded_prefix}{decoded_content}"
print(decoded_message)
```

**Decoded Message:**
- `FlagY{Congratulations_u_got_ittt}`

### **Step 4: Identify the Flag**

Upon decoding, one message stood out:
- `FlagY{Congratulations_u_got_ittt}`

This was clearly the intended flag for the challenge.


## **Flag**

```
FlagY{Congratulations_u_got_ittt}
```


## **Lessons Learned**

- **GIF File Handling:** Extracting frames from a GIF can be crucial in forensics challenges where each frame may contain different data.
- **QR Code Scanning:** It's important to have alternative tools like OpenCV ready when facing library dependencies.
- **ROT13 Cipher:** Recognizing common encoding patterns, like ROT13, is key in quickly deciphering encoded data.


## **Conclusion**

The **Flagyard QRRR! Forensics** challenge was a great exercise in both forensic image analysis and cryptography. By systematically extracting, scanning, and decoding the data, we successfully uncovered the hidden flag and deepened our understanding of handling complex data hiding techniques in CTF challenges.


Writeup by: Nodirjon