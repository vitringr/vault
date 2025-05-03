---
aliases:
  - FHS
context:
  - "[[Linux]]"
---

# Filesystem Hierarchy Standard

Standard guidelines that define the structure and organization of directories in Unix-like systems, including [[Linux]].

---

**Standard**: Complying to FHS ensures predictable directory structures across different [[Linux Distribution|Linux Distributions]].

**Compatibility**: Allows directory compatibility between different systems.

**Modular**: Follows [[Modular Design]] principles, dividing files into manageable logical groups.

## Directory Structure

The general layout and structure of directories.

### `/` Root Directory

Primary root diectory of the entire filesystem.

Contains all other directories and files.

Should not contain standalone files. Only directories.

### `/bin` Essential User Binaries

Contains core [[Command-line Interface|Command-line]] utilities.

The commands need to be available in single-user mode, potentially for repair and recovery.

Some systems merge `/bin` with `/usr/bin` via symlinks.

### `/boot` Boot Loader Files

Stores files required for system boot.

### `/dev` Device Files

Contains device files representing [[Hardware]] components.

### `/etc` Configuration Files

Contains system-wide configuration files.

### `/home` User Home Directories

Contains personal directories for users.

### `/lib` Shared Libraries

[[Library (Software Architecture)|Libraries]] essential for [[Binary File|binaries]] in `/bin` and `/sbin`.

Could also be `/lib64` for 64-bit libraries for example.

### `/mnt` Temporary Mount Points

Used for manual mounting of temporary filesystems.

### `/opt` Optional Software

Stores [[Software]] that is not part of the default system.

### `/proc` Process and Kernel Information

Virtual filesystem providing process and kernel information as files.

Generally automatically generated and populated by the system, on the fly.

### `/root` Root User Home Directory

The home directory of the root user.

### `/run` Runtime Data

Stores temporary runtime data.

Information about the running system since last boot.

### `/sbin` System Binaries

Essential system administration binaries.

### `/src` Service Data

Contains data for services.

### `/sys` System Information

[[Kernel]] and hardware information.

### `/tmp` Temporary Files

Stores temporary files that are generally not preserved between system reboots.

### `/usr` User Programs & Read-Only Data

Contains user applications, libraries, and documents.

Non-essential software.

### `/var` Variable Data Files

Contains files whose content is expected to continually change.
