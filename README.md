# 🛠️ LumenChain

**A specialized C++ toolchain and dependency manager designed to automate the Clang/LLVM ecosystem and provide a centralized dependency management experience for C++ developers.**

## 🚀 Overview

LumenChain is a utility that ensures a consistent development environment by managing the Clang compiler and its associated dependencies. It addresses the friction of manual toolchain setup and library linking across different Linux distributions by offering a unified, automated workflow.

## ✨ Key Features

* **Integrated Dependency Market:** Features a centralized mechanism for fetching external libraries hosted on a dedicated server. LumenChain downloads, builds, and links dependencies directly to your project.
* **Structured Dependency Management:** Implements a system that handles transitive dependencies and versioning, shielding the developer from manual `include` and `lib` path configurations.
* **Automated Clang Deployment:** Detects if Clang is present on the host system; if not, it automatically provisions the LLVM suite tailored for the detected Linux distribution.
* **Parallel Toolchain Provisioning:** Capability to create isolated, parallel toolchains. This allows users to test specific Clang versions or library builds without interfering with the system-wide default compiler.
* **Clang-Centric Optimization:** Built specifically around the LLVM ecosystem (clang, clang++, lld, and llvm-utils) to ensure high-performance builds and modern diagnostic feedback.
* **Zero-Config Integration:** Automatically generates the necessary environment variables and CMake presets to point projects to the managed toolchain and dependencies.

## ⚙️ LumenBuilder & XML Configuration

To completely abstract the complexities of standard C++ build systems, this project includes **LumenBuilder**. Acting as the core build engine, LumenBuilder introduces a structured workflow using a standardized `.xml` configuration file for each project (e.g., `lumen.xml`).

Developers simply define their project properties and dependencies in a clean XML format. LumenBuilder parses this file, resolves the dependency tree from the centralized market, and **automatically generates and executes the underlying `CMakeLists.txt` in the background**, eliminating the need to interact with CMake directly.

**Example `LumenBuilder.xml` structure:**
```xml
<project>
    <name>LumenApp</name>
    <version>1.0.0</version>
    <properties>
        <compiler>clang++</compiler>
        <cxx_standard>20</cxx_standard>
    </properties>
    <dependencies>
        <dependency>
            <name>fmt</name>
            <version>9.1.0</version>
        </dependency>
        <dependency>
            <name>gtk4</name>
            <version>latest</version>
        </dependency>
    </dependencies>
</project>
```

## 🏗️ Technical Implementation

* **Language:** C++20
* **Compiler:** Clang (Default toolchain)
* **Build System:** CMake integration
* **Dependency Logic:** Remote server-client architecture for library distribution
* **Compatibility:** Linux Desktop Environments (Fedora, Arch, Ubuntu, Debian)

## 🚦 Getting Started

**1. Clone the repository:**
```bash
git clone [https://github.com/bogdancoste/LumenChain.git](https://github.com/bogdancoste/LumenChain.git)
cd LumenChain
