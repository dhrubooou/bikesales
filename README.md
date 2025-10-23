# ERPBackend

A high-performance **Enterprise Resource Planning (ERP)** backend system built with modern C++ technologies, AWS SDK, and gRPC integration.  
This project provides a scalable, secure, and modular backend foundation for enterprise-grade applications, featuring **SSL/TLS security**, **AWS S3 integration**, and **cross-platform build support** for Windows and Linux.

---

## 🚀 Overview

The **ERPBackend** repository includes:
- A modular backend system for enterprise operations.
- Integration with **AWS SDK (S3)** for cloud storage and secure file handling.
- **gRPC** support for client-server communication.
- Built-in **SSL/TLS** encryption for secure data transfer.
- Cross-platform support via **CMake presets** for Windows and Linux builds.

---

## 🧩 Repository Setup

### Clone the Repository

```bash
git clone git@github.com:DarkStar1997/ERPBackend
cd ERPBackend
```
## ⚙️ Build Configuration

The project uses **CMake Presets** to simplify configuration and builds.

### List Available Presets
```bash
cmake --list-presets
```
# For Windows
```bash
cmake --preset win-rel
cmake --build --preset win-rel
```
# For Linux
```bash
cmake --preset lin-rel
cmake --build --preset lin-rel
```
