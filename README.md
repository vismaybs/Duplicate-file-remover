# Duplicate File Remover

A Python utility script that scans the current directory, detects duplicate files using MD5 content hashing, and automatically removes redundant files to free up disk space.

---

## Features

* **Memory-Efficient Hashing:** Reads files in 64 KB chunks (`BLOCKSIZE = 65536`) to prevent memory overflow when processing large files.


* **Exact Binary Comparison:** Uses MD5 hashes (`hashlib.md5()`) to identify true duplicate files regardless of their filenames.


* **Automated Cleanup:** Automatically deletes detected duplicate files using `os.remove()`.


* **Execution Summary:** Outputs a list of deleted filenames or notifies you if no duplicate files were found.



---

## How It Works

1. **Directory Scanning:** The script lists all entries in the working directory and filters out subdirectories using `os.path.isfile()`.


2. **Hash Generation:** Each file is passed through the `hashFile()` function, which reads binary data in chunks and computes a unique MD5 hex digest.


3. **Duplicate Detection:** Hashes are stored in a key-value map (`hashMap`). If a hash already exists in the dictionary, the file is identified as a duplicate, logged in `deletedFiles`, and deleted immediately.



---

## Prerequisites

* **Python 3.x**
* No third-party package installations are required (uses standard library modules `os` and `hashlib`).



---

## Usage

1. Copy or place the `duplicatefileremover.py` script into the directory containing the files you wish to clean.


2. Open a terminal or command prompt in that directory.


3. Run the script:

```bash
python duplicatefileremover.py
```[cite: 33]

---

## Project Structure

```text
├── duplicatefileremover.py   # Main Python script for hash calculation and file deletion
└── README.md                 # Project documentation
```[cite: 33]

---

> **Note:** Backup important files before running the script, as deleted files are permanently removed by `os.remove()` and are not sent to the system trash or recycle bin[cite: 33].

```
