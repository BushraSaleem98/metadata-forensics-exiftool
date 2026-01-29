# Metadata Forensics Using ExifTool (Kali Linux)

## 📌 Project Overview
This project demonstrates how metadata can be analyzed, modified, and removed from digital images using ExifTool in Kali Linux.

Metadata reveals valuable information such as device details, timestamps, software used, and GPS coordinates. In forensic investigations, this information helps analysts trace the origin and authenticity of files. At the same time, attackers or privacy-conscious users may attempt to manipulate or remove this data.

This lab explores both forensic analysis and basic anti-forensics techniques in a controlled environment.

---

## 🛠️ Tools & Technologies
- Kali Linux
- ExifTool
- Oracle VirtualBox
- Linux Terminal
- JPEG Image File

---

## 📚 Key Concepts

### Digital Footprint
A digital footprint (or digital shadow) is the trail of data left behind when users interact with digital devices, applications, and online services.

### Metadata
Metadata is structured information that describes a file, such as author, creation date, camera model, GPS coordinates, file size, and format. It is often referred to as "data about data."

---

## ⚙️ Lab Procedure

### Step 1: Verify or Install ExifTool
ExifTool is usually pre-installed in Kali Linux. To ensure the latest version is available:

```bash
sudo apt update
sudo apt install exiftool -y
```

---

### Step 2: Acquire the Target Image
Download or select an image file for analysis.

```bash
wget <image-url> -O target.jpg
```

---

### Step 3: Perform Basic Metadata Reconnaissance
View all metadata embedded in the image:

```bash
exiftool target.jpg
```

This reveals information such as camera model, timestamps, software, and GPS data.

---

### Step 4: Extract GPS Coordinates (Geolocation Analysis)
If GPS data exists, extract the coordinates:

```bash
exiftool -gpslatitude -gpslongitude target.jpg
```

The coordinates can be entered into a map service to determine where the image was captured.

---

### Step 5: Anti-Forensics (Modifying Metadata)

#### 5.1 Modify the Artist Tag
Add or modify ownership information:

```bash
exiftool -Artist="Demo User" target.jpg
```

#### 5.2 Spoof the GPS Location
Change the GPS coordinates (example: Eiffel Tower, Paris):

```bash
exiftool -GPSLatitude=48.8584 -GPSLongitude=2.2945 target.jpg
```

Verify the changes:

```bash
exiftool target.jpg
```

---

### Step 6: Clean Tracks (Remove Metadata)
Remove all metadata before sharing the image publicly:

```bash
exiftool -all= target.jpg
```

Verify that metadata has been removed:

```bash
exiftool target.jpg
```

Only basic file attributes should remain.

---

## 📷 Screenshots
Screenshots for each step are available in the `/screenshots` folder.

---

## 🎯 Learning Outcomes
- Learned how metadata reveals hidden information in digital files.
- Performed basic forensic analysis using ExifTool.
- Extracted geolocation data from images.
- Practiced modifying and spoofing metadata.
- Understood privacy and anti-forensic implications.

---

## ⚠️ Ethical Disclaimer
This project is for educational purposes only.  
Do not analyze or modify files without proper authorization.

---

## 👩‍💻 Author
**Bushra Saleem**  
Cybersecurity Learner | Aspiring SOC Analyst  
Karachi, Pakistan
