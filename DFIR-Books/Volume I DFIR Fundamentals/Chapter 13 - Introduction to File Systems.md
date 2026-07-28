# Chapter 13 – Introduction to File Systems

> **Learning Objectives**
>
> By the end of this chapter, you will understand:
>
> - What a file system is
> - Why file systems are essential in digital forensics
> - How operating systems organize data on storage devices
> - The basic components of a file system
> - The difference between files, directories, clusters, and sectors
> - Common file systems used by different operating systems
> - Why understanding file systems is important for DFIR investigations

---

# 1. Introduction

Imagine entering a library containing one million books.

There are no shelves.

There are no labels.

There are no categories.

Every book is lying randomly on the floor.

Finding a single book would take days.

Now imagine the same library with:

- Shelves
- Book numbers
- Categories
- Floor maps
- Librarians
- Catalogs

Finding a book now takes only a few minutes.

A computer faces the same challenge.

A storage device may contain millions of files.

Without an organized system, the operating system would never know:

- Where a file begins.
- Where it ends.
- Which space is free.
- Which files belong to which user.

The system responsible for organizing all of this is called the **File System**.

---

# 2. What is a File System?

A **file system** is the method an operating system uses to organize, store, retrieve, and manage data on a storage device.

Simply put,

> **A file system is the filing cabinet of a computer.**

It keeps track of:

- File names
- Folder structure
- File locations
- Permissions
- Metadata
- Free space
- Deleted files

Without a file system, a storage device would simply contain billions of bits with no meaningful organization.

---

# 3. Why Are File Systems Important in DFIR?

Every forensic investigation involves data stored on a device.

Understanding the file system helps investigators answer questions such as:

- Where is a file stored?
- When was it created?
- Has it been modified?
- Was it deleted?
- Can it be recovered?
- Which user owned the file?
- Is any hidden data present?

Many forensic artifacts exist because of the way file systems manage data.

---

# 4. How Does a File System Work?

When you save a document, the operating system does much more than simply write the file.

It must:

1. Choose a location on the storage device.
2. Allocate space for the file.
3. Record the file name.
4. Store metadata.
5. Update directory information.
6. Mark the allocated space as occupied.

When you open the file later, the operating system consults the file system to locate the stored data.

---

# 5. Basic Components of a File System

Although different file systems have different designs, most contain similar components.

### Files

A file stores information such as:

- Documents
- Images
- Videos
- Programs
- Databases

---

### Directories (Folders)

Directories organize files into logical groups.

Example:

```text
Documents
│
├── Resume.docx
├── Notes.pdf
└── Report.xlsx
```

Directories make storage easier to manage.

---

### Sectors

A **sector** is the smallest physical unit of storage on a disk.

Historically, most sectors were **512 bytes**.

Modern storage devices often use **4096-byte (4 KB)** sectors.

---

### Clusters

A **cluster** is one or more sectors grouped together by the file system.

Files are stored in clusters rather than individual sectors.

For example:

```
Sector + Sector + Sector + Sector

↓

Cluster
```

Clusters improve storage management and performance.

---

# 6. File Metadata

Every file contains information **about the file itself**.

This information is called **metadata**.

Examples include:

- File name
- File size
- Creation time
- Modification time
- Last access time
- Owner
- Permissions
- Storage location

Investigators often rely on metadata even when the file contents are unavailable.

---

# 7. Free Space and Allocated Space

Storage devices contain two basic types of space.

### Allocated Space

Currently used by existing files.

---

### Unallocated Space

Previously used or never used.

Deleted files often leave remnants in unallocated space until new data overwrites them.

Forensic investigators frequently examine this area to recover deleted evidence.

---

# 8. File Deletion

Many users believe deleting a file removes it permanently.

In reality, most operating systems simply:

- Remove the file's directory entry.
- Mark its storage space as available.

The actual file contents often remain until they are overwritten by new data.

This is why deleted files can sometimes be recovered during forensic investigations.

---

# 9. Common File Systems

Different operating systems use different file systems.

| Operating System | Common File Systems |
|------------------|---------------------|
| Windows | NTFS, FAT32, exFAT |
| Linux | EXT4, XFS, Btrfs |
| macOS | APFS, HFS+ |

Each file system stores data differently.

Understanding these differences helps investigators locate evidence more effectively.

---

# 10. Real-World Example

A company suspects an employee deleted confidential engineering documents before leaving.

The investigator creates a forensic image of the employee's SSD.

Although the documents no longer appear in Windows Explorer, examination of the file system reveals:

- Deleted file metadata.
- Unallocated clusters containing portions of the deleted files.
- Original timestamps.
- File names.
- Directory structure.

Because the investigator understands how the file system manages deleted files, the documents are successfully recovered.

---

# 11. Common Mistakes

New investigators often:

- Assume deleted files are permanently erased.
- Ignore metadata.
- Confuse sectors with clusters.
- Analyze only visible files.
- Forget to examine unallocated space.
- Misinterpret timestamps stored by the file system.

Understanding file system behavior helps avoid these mistakes.

---

# 12. Best Practices

Professional investigators should:

- Understand the file system used by the target device.
- Preserve original storage media.
- Examine metadata carefully.
- Analyze allocated and unallocated space.
- Correlate file system evidence with other artifacts.
- Document findings thoroughly.

A strong understanding of file systems improves the accuracy of every forensic investigation.

---

# Remember This

- A file system organizes data on storage devices.
- Without a file system, an operating system cannot locate files.
- Files contain both data and metadata.
- Deleted files often remain recoverable until overwritten.
- Unallocated space can contain valuable forensic evidence.
- File system knowledge is fundamental to digital forensics.

---

# Key Terms

| Term | Meaning |
|------|---------|
| File System | A method used by an operating system to organize and manage data |
| File | A collection of stored digital information |
| Directory | A container used to organize files |
| Sector | The smallest physical storage unit on a disk |
| Cluster | One or more sectors allocated together by the file system |
| Metadata | Information describing a file rather than its contents |
| Allocated Space | Storage currently assigned to files |
| Unallocated Space | Storage available for new data that may still contain remnants of deleted files |

---

# Chapter Summary

In this chapter, you learned:

- What a file system is
- How operating systems organize storage
- The basic components of a file system
- The difference between sectors and clusters
- The role of metadata
- How deleted files remain recoverable
- Why file system knowledge is essential for DFIR investigations

A file system is much more than a storage mechanism—it is a roadmap that tells investigators where data is located, how it is organized, and what traces remain after files have been created, modified, or deleted.

---

# Review Questions

1. What is a file system?
2. Why are file systems important in digital forensics?
3. What is the difference between a sector and a cluster?
4. What is file metadata?
5. What happens when a file is deleted?
6. Why is unallocated space important during an investigation?
7. Name three common file systems used by Windows.
8. How can metadata help reconstruct user activity?

---

# Practical Exercise

A workstation has been seized during an insider threat investigation.

Before examining any files, prepare a file system analysis plan by answering:

- Which file system is used on the storage device?
- Which metadata fields would you examine first?
- Which areas of the disk would you inspect for deleted files?
- How would you determine whether deleted data is recoverable?
- How would file system metadata support your investigation timeline?

Your goal is to demonstrate how understanding file system fundamentals improves digital forensic investigations.

---

# What's Next?

In the next chapter, we will explore **Operating System Internals**, learning how Windows, Linux, and macOS manage processes, memory, users, and storage—and why this knowledge is essential for interpreting forensic evidence correctly.