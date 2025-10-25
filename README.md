# ERPBackend

A high-performance **Enterprise Resource Planning (ERP)** backend system built with modern C++ technologies, AWS SDK, and gRPC integration.  
This project provides a scalable, secure, and modular backend foundation for enterprise-grade applications, featuring **SSL/TLS security**, **AWS S3 integration**, and **cross-platform build support** for Windows and Linux.

---

##  Overview

The **ERPBackend** repository includes:
- A modular backend system for enterprise operations.
- Integration with **AWS SDK (S3)** for cloud storage and secure file handling.
- **gRPC** support for client-server communication.
- Built-in **SSL/TLS** encryption for secure data transfer.
- Cross-platform support via **CMake presets** for Windows and Linux builds.

---

##  Repository Setup

### Clone the Repository

```bash
git clone git@github.com:DarkStar1997/ERPBackend
```
##  Build Configuration

The project uses **CMake Presets** to simplify configuration and builds.

### List Available Presets
```bash
cmake --list-presets
```
### For Windows
```bash
cmake --preset win-rel
cmake --build --preset win-rel
```
### For Linux
```bash
cmake --preset lin-rel
cmake --build --preset lin-rel
```
---
##  **Environment Configuration**

Create a `.env.aws` file in the project root with the following credentials to enable **AWS S3 integration**:

```env
AWS_ACCESS_KEY=<your-aws-access-key-id>
AWS_SECRET_KEY=<your-aws-secret-access-key>
AWS_REGION=<your-aws-region>
AWS_BUCKET_NAME=<your-s3-bucket-name>
```
> ⚠️ **Security Note:**  
> Never commit your `.env.aws` file to version control.  
> Always add it to your `.gitignore` file to keep your AWS credentials safe.

## 🔒 SSL/TLS Authentication

The **ERPBackend** project supports **SSL/TLS** to ensure secure data transmission between the backend and client.

---

### 🧩 Step 1: Generate SSL Certificates

Use **OpenSSL** to generate the necessary private and public certificates.

```bash
cd cert

# Generate a private key
openssl genpkey -algorithm RSA -out server.key

# Generate a certificate signing request (CSR)
openssl req -new -key server.key -out server.csr

# Generate a self-signed certificate (valid for 1 year)
openssl x509 -req -days 365 -in server.csr -signkey server.key -out server.crt

# Remove intermediate file
rm -rf server.csr
```
> 🗝️ The generated files — `server.key` and `server.crt` — are required for SSL/TLS communication.

### Step 2: Share the Certificate with Frontend

Provide the generated `server.crt` file to your frontend client so it can establish secure gRPC connections.


---
## 🧠 gRPC Integration

The **ERPBackend** project uses **gRPC** for efficient, scalable, and high-performance Remote Procedure Call (RPC) communication.

---

### ⚙️ Build gRPC from Source

Follow the steps below to build and install **gRPC** manually.

```bash
# Clone gRPC repository
git clone -b v1.66.1 --recurse-submodules https://github.com/grpc/grpc

# Create build directories
mkdir grpc\builddir
mkdir grpc\grpc_install

# Configure build with CMake
cmake -GNinja -S grpc -B grpc\builddir -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=grpc\grpc_install -DABSL_PROPAGATE_CXX_STD=ON -DABSL_ENABLE_INSTALL=ON

# Build the project
cmake --build grpc\builddir --config Release

# Install gRPC
cmake --install grpc\builddir
```

--
## ☁️ AWS SDK Integration

The **ERPBackend** integrates the **AWS SDK for C++** to communicate with **AWS S3** for secure and reliable file storage.

---

### ⚡ Quick Setup

To automatically build the AWS SDK and its dependencies, simply run:

```bash
fetchdeps.bat
fetchAwsSdk.bat
```
