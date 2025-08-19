Here's the updated GitHub Markdown with the verification outputs you provided.

-----

### 1\. JDK Installation

**1.1. Install JDK 8**

```bash
# Download JDK 8
curl -usvc-jenkinsbuild:AP3cYNV5E1kaXfdsjZiCbrd5kf -O "https://oneartifactoryci.horizon.com/artifactory/RBMV_AWS/SOFTWARE/JDK/jdk-8u461-linux-x64.tar.gz"

# List files to verify download
ls -lrt

# Extract the archive
tar -zxvf jdk-8u461-linux-x64.tar.gz

# Remove the downloaded archive
rm -rf jdk-8u461-linux-x64.tar.gz

# Create a symbolic link for easier access
ln -s jdk1.8.0_461 jdk
```

**1.2. Install JDK 17**

```bash
# Download JDK 17
curl -usvc-jenkinsbuild:APi2kE1kaXfdsjZiCbrd5kf -O "https://oneartifactoryci.horizon.com/artifactory/RBMV_AWS/SOFTWARE/JDK/jdk-17.0.16_linux-x64_bin.tar.gz"

# Extract the archive
tar -zxvf jdk-17.0.16_linux-x64_bin.tar.gz

# Remove the downloaded archive
rm -rf jdk-17.0.16_linux-x64_bin.tar.gz

# Create a symbolic link for easier access
ln -s jdk-17.0.16 jdk17
```

**1.3. Set up Environment Variables & Verify**

```bash
# Set JAVA_HOME and update the PATH
export JAVA_HOME=/apps/opt/jdk17
export PATH=$JAVA_HOME/bin:$PATH

# Verify the Java installation
java -version
```

**Verification Output**

```
java version "17.0.16" 2025-07-15 LTS
Java(TM) SE Runtime Environment (build 17.0.16+12-LTS-247)
Java HotSpot(TM) 64-Bit Server VM (build 17.0.16+12-LTS-247, mixed mode, sharing)
```

-----

### 2\. Node.js Installation

**Note:** Run these commands as the **root** user.

```bash
# Update the system packages
sudo yum update -y

# Change to the /usr/bin directory
cd /usr/bin

# Set up the Node.js LTS repository and install Node.js
curl -fsSL https://rpm.nodesource.com/setup_lts.x | sudo bash -
sudo yum install -y nodejs

# Verify npm installation
npm -v
```

**Verification Output**

```
8.19.4
```

-----

### 3\. Spring Boot CLI Installation

**Note:** This section assumes you've manually transferred the file to the target machine using a tool like WinSCP.

```bash
# Navigate to the target installation directory
cd /apps/opt

# Extract the Spring Boot CLI archive
tar -zxvf spring-boot-cli-3.2.2-bin.tar.gz

# Remove the downloaded archive
rm -rf spring-boot-cli-3.2.2-bin.tar.gz

# Create a symbolic link for the Spring CLI
ln -s spring-boot-cli-3.2.2 spring

# Verify the installation
/apps/opt/spring/bin/spring --version
```

**Verification Output**

```
Spring CLI v3.2.2
```
