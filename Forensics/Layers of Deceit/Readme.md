# Layers of Deceit - CTFlearn (Forensics 30pts)

## 🧩 Challenge Description

> We found this image in a suspect's email backup. It doesn't look out of place... but our analysts are convinced this isn't just any image. Find out what it's really hiding.

**Attachment:** `floww3r.jpg`  
**Category:** Forensics  
**Points:** 30  
**Author:** Naufal24

---

## 🧠 Challenge Design

This challenge uses:
- Visual steganography via white-on-white clue (RGB 240 vs 255)
- `steghide` with a hidden password
- Misdirection through file name and EXIF comment metadata

### Real password hidden in the image:
- Embedded as light gray-white text on flower petals
- Value: `4n14ym4bar` (obfuscated form of "anjaymabar")

### Misdirections:
- EXIF comment: `wh4t4reY0uD01n6h3r3`
- File name: `floww3r.jpg`

---

## 🔎 Solving Steps

1. Check metadata using `exiftool`:
    ```bash
    exiftool floww3r.jpg
    ```

2. Open the image in GIMP or Photoshop.
   - Use **Levels/Curves** or **Channel Mixer**
   - Focus on **blue channel** or extreme contrast
   - Reveal hidden text on the petal

3. Once password is found: `4n14ym4bar`

4. Extract flag with `steghide`:
    ```bash
    steghide extract -sf floww3r.jpg -p 4n14ym4bar
    ```

5. Output will contain:
    ```
    CTFlearn{h4ck3d}
    ```

---

## 💡 Lessons Learned

- Not all clues are textual — pixel values matter
- Metadata ≠ reliable clue
- Try multiple layers: channel, comment, name

---

## 📁 Files

- `floww3r.jpg` — main challenge image (not included here, link to CTFlearn or placeholder)

---

## 📜 License

Open-source for learning. Do not submit elsewhere without proper credit.
