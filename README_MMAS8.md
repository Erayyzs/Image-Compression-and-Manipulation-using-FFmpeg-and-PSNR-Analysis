# Image Compression and Manipulation using FFmpeg and PSNR Analysis

This repository contains the eighth lab assignment for the **Multimedia Information Systems** course, completed by **Eray Samet Gündüz** and **Emre Yılmaz**. The project focuses on understanding the effects of various image compression techniques and transformations using **FFmpeg**, along with PSNR (Peak Signal-to-Noise Ratio) analysis.

## Objectives

- Compare lossless and lossy compression formats
- Analyze the effect of compression quality on image size and visual fidelity
- Convert images between formats including JPEG and JPEG2000
- Apply image transformations (rotation and grayscale)
- Use PSNR metrics to assess compression impact

## Tools Used

- **FFmpeg**: for image conversion and transformation
- **Quality Metric Tool**: for PSNR calculation

---

## Lab Tasks and Key Steps

### 1. PNG to JPEG Conversion

Used FFmpeg to convert a lossless PNG image (`airplane.png`) to a lossy JPEG format:

```bash
ffmpeg -i airplane.png output.jpeg
```

Observation: JPEG files were significantly smaller due to lossy compression.

---

### 2. JPEG Compression with Varying Quality

Different compression levels were applied using the `-q:v` option:

```bash
ffmpeg -i output.jpeg -q:v 5 output15.jpeg
ffmpeg -i output.jpeg -q:v 20 output20.jpeg
ffmpeg -i output.jpeg -q:v 50 output50.jpeg
```

- As quality decreased (higher `q` values), image size was reduced.
- Visual artifacts became noticeable at lower quality settings.

---

### 3. Conversion to JPEG2000

Converted JPEG to JPEG2000 using FFmpeg:

```bash
ffmpeg -i output.jpeg output3.jp2
```

- JPEG2000 file size increased by nearly 7x.
- Due to viewer limitations, the quality could not be visually verified.

---

### 4. Image Rotation

Rotated the PNG image by 90 degrees:

```bash
ffmpeg -i airplane.png -vf "transpose=1" output_rotated.png
```

- Rotation caused a slight increase in file size.
- Possibly due to changes in spatial redundancy affecting compression efficiency.

---

### 5. Grayscale Conversion

Converted the image to grayscale:

```bash
ffmpeg -i airplane.png -vf format=gray greyplan.png
```

- File size reduced significantly (approx. 2.5x smaller).
- Due to removal of RGB color channels.

---

### 6. PSNR Analysis

Used Quality Metric Tool to evaluate PSNR values across images with different quality settings (5, 10, 15, 20).

- A plot was generated showing PSNR values decreasing as compression level increased.
- Demonstrated that higher compression lowers image fidelity.

---

## Conclusion

This lab provided practical insights into how compression quality, image format, and transformations affect image size and visual quality. PSNR analysis reinforced the impact of compression on perceptual quality.