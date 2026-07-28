# Chapter 7 – Disk Imaging and Disk Acquisition

> **Learning Objectives**
>
> By the end of this chapter, you will understand:
>
> - What disk imaging is
> - Why forensic disk imaging is necessary
> - The difference between disk imaging and file copying
> - Types of disk images
> - Bit-stream imaging
> - Image verification using cryptographic hashes
> - Write blockers and their importance
> - Common disk image formats
> - Best practices for forensic disk acquisition

---

# 1. Introduction

Imagine a detective finds an important notebook at a crime scene.

Instead of giving the original notebook to every investigator, an exact photocopy is created.

The original notebook is locked away in secure storage.

Every investigator studies the copy.

Why?

Because if someone accidentally writes on the original notebook, tears a page, or spills coffee on it, the original evidence is permanently damaged.

Digital investigations follow the same principle.

Investigators almost never analyze the original hard drive.

Instead, they create an exact forensic copy called a **disk image**.

---

# 2. What is Disk Imaging?

A **disk image** is an exact bit-for-bit copy of a storage device.

Every bit stored on the original device is copied into a forensic image.

This includes:

- Operating system files
- User documents
- Deleted files
- Hidden files
- File system metadata
- Unallocated space
- Slack space
- Boot records

A forensic image is much more than a backup.

It captures everything stored on the device.

---

# 3. Why Not Simply Copy the Files?

Many beginners believe they can simply copy files using Windows Explorer.

This is incorrect.

Copying files only captures visible data.

It does **not** preserve important forensic evidence such as:

- Deleted files
- Partition information
- File system metadata
- Slack space
- Unallocated space
- Master Boot Record (MBR)
- GUID Partition Table (GPT)

These areas often contain valuable evidence.

---

# 4. File Copy vs Disk Image

| File Copy | Disk Image |
|-----------|------------|
| Copies selected files | Copies every bit on the storage device |
| Misses deleted files | Includes deleted files |
| Misses slack space | Includes slack space |
| Misses unallocated space | Includes unallocated space |
| Not suitable for forensic investigations | Standard forensic practice |

A forensic investigation requires a disk image—not just copied files.

---

# 5. What is Bit-Stream Imaging?

Bit-stream imaging means copying every single bit from the source device to the forensic image.

Imagine reading a book.

A normal file copy copies only the printed words.

Bit-stream imaging copies:

- Every page
- Blank pages
- Torn pages
- Notes written in the margins
- Hidden messages between pages

Nothing is ignored.

This complete copy allows investigators to recover evidence that users believe has been deleted.

---

# 6. Types of Disk Acquisition

### Physical Acquisition

Copies the entire storage device.

Includes:

- All partitions
- Deleted data
- Unallocated space
- Slack space

This is the preferred method whenever possible.

---

### Logical Acquisition

Copies only selected files and folders.

Useful when:

- Full imaging is not possible.
- Storage is encrypted but currently unlocked.
- Time constraints exist.

However, logical acquisition captures less evidence.

---

# 7. What is a Write Blocker?

A **write blocker** is a hardware or software mechanism that prevents any data from being written to the original storage device.

Its purpose is simple:

> Allow investigators to read evidence without modifying it.

Without a write blocker, even connecting a drive to a computer may change:

- Access timestamps
- System metadata
- Log entries

Using a write blocker helps preserve evidence integrity.

---

# 8. Common Disk Image Formats

Several formats are used in digital forensics.

| Format | Description |
|--------|-------------|
| RAW (DD) | Exact bit-for-bit copy without compression |
| E01 | EnCase Evidence File format with compression and metadata |
| AFF | Advanced Forensic Format |
| AFF4 | Modern version of AFF with improved capabilities |

Different forensic tools support different image formats.

---

# 9. Verifying the Disk Image

Creating a disk image is only part of the process.

Investigators must verify that the image is identical to the original device.

This is done using cryptographic hash values.

Example:

```
Original Drive

SHA-256

↓

8C9F4D...

↓

Forensic Image

SHA-256

↓

8C9F4D...
```

If both hash values match, investigators can demonstrate that the forensic image accurately represents the original evidence.

---

# 10. Real-World Example

A company's laptop is suspected of containing malware used to steal confidential documents.

The investigator:

1. Removes the SSD from the laptop.
2. Connects it through a hardware write blocker.
3. Creates a forensic image in E01 format.
4. Calculates the SHA-256 hash of the original SSD.
5. Calculates the SHA-256 hash of the forensic image.
6. Confirms that both hashes match.
7. Stores the original SSD securely.
8. Performs all analysis using the forensic image.

This process preserves the original evidence while allowing a complete forensic investigation.

---

# 11. Common Mistakes

New investigators often make mistakes such as:

- Analyzing the original drive directly.
- Forgetting to verify hash values.
- Failing to use a write blocker.
- Interrupting the imaging process.
- Not documenting acquisition details.
- Using consumer backup software instead of forensic imaging tools.

These mistakes can compromise evidence integrity.

---

# 12. Best Practices

Professional investigators should:

- Create a forensic image before analysis.
- Use trusted forensic imaging tools.
- Use hardware write blockers whenever possible.
- Calculate cryptographic hash values before and after imaging.
- Verify the integrity of every forensic image.
- Store original evidence securely.
- Document every step of the imaging process.

These practices ensure that evidence remains accurate, reproducible, and defensible.

---

# Key Terms

| Term | Meaning |
|------|---------|
| Disk Image | A bit-for-bit copy of a storage device |
| Bit-Stream Imaging | Copying every bit from a storage device |
| Physical Acquisition | Acquisition of the entire storage device |
| Logical Acquisition | Acquisition of selected files and folders |
| Write Blocker | A device or software that prevents modification of evidence |
| E01 | A widely used forensic disk image format |
| RAW (DD) | An uncompressed bit-for-bit disk image |

---

# Chapter Summary

In this chapter, you learned:

- What disk imaging is
- Why investigators create forensic images instead of copying files
- The difference between physical and logical acquisition
- What bit-stream imaging means
- Why write blockers are essential
- Common forensic image formats
- How cryptographic hashes verify image integrity
- Best practices for disk acquisition

Disk imaging is one of the most fundamental skills in digital forensics. It ensures that investigators preserve the original evidence while working from an exact, verifiable copy that can be analyzed without risking modification.

---

# Review Questions

1. What is a forensic disk image?
2. How does disk imaging differ from copying files?
3. What is bit-stream imaging?
4. Why are deleted files included in a forensic image?
5. What is the purpose of a write blocker?
6. Why are cryptographic hash values calculated after imaging?
7. Compare physical acquisition and logical acquisition.
8. Name three common forensic disk image formats.

---

# Practical Exercise

You are assigned to investigate a workstation suspected of being used to exfiltrate sensitive company data.

Prepare a disk acquisition plan by answering the following:

- Would you perform a physical or logical acquisition? Why?
- Which forensic image format would you choose?
- How would you prevent accidental modification of the original drive?
- How would you verify the integrity of the forensic image?
- What documentation would you record during the acquisition process?

Design your plan as if you were preparing to present it to a senior DFIR investigator.

---

# What's Next?

In the next chapter, we will study **Memory Acquisition**, where you will learn why RAM is considered one of the most valuable—and most volatile—sources of digital evidence, and how investigators capture it before it disappears.