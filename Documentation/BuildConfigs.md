**Builds and Packages of .NET Core 2.0 Runtime**

__Windows__

- Architectures:
    - x86
    - x64
    - arm32
    - arm64 (TODO, confirm this one for 2.0?)

- OS's
    Windows 7+

- Builds for each architecture:
    - Portable
      - Build and testing on latest stable supported OS version.
      - Additional testing on lowest supported OS. 
      - Testing on Full .NET Framework in for some binaries for compat.
      - Testing in UWP and CoreRT for compat.

- Packages
    - zip's
        - libraries for each build flavor
        - Source which when extracted can reproduce all the build flavors with a simple build command with parameter for build flavors.
        - Pdb's matching the build for each build flavor.
    - Msi installers for each architecture
    - NuGet
        - NetCore.App packages containing results of the Portable build.

__Linux__

- Architectures:
    - x86 (TODO: Needed for community to facilitate arm32 on Linux?)
    - x64
    - arm32

- OS's for testing and binary distribution
    - RHEL
        - 7+
    - Centos 
        - 7+
    - Debian
        - 8+
    - Ubuntu
        - 14.04
        - 16.04
        - 16.10
    - Fedora
        - 23
        - 24
        - 25
    - OpenSuse
        - 13.2
        - 42.1
    - (TBD: Alpine)

- Builds each architecture:
    - Distro Agnostic Portable (TODO: glibc version?) (TODO?Builds on which OS?)
        - Carries local dynamically linked OS dependencies.
        - Testing on the result of this build needs to happen on all OS's.
    - Distro Specific OS 
        - Dynamically linked against the OS copy of dependencies.
        - This is the way distros build and we build for our native package manager packages.
        - Testing is on the same OS as built on.
    - (TBD: Distro Specific Portable) 
        - This would be to provide RID specific capabilities for standalone apps that can be distro specific without needing to install dependencies.
        - Testing on this would be on the OS it was built on.

- Packages
    - tar.gz's
        - Contains Distro Agnostic Portable (glibc version)
        - (TBD: also contains result of portable distro specific build)
        - Source which when extracted can reproduce all the build flavors with a simple build command with parameter for build flavors.
        - Pdb's matching the build for each build flavor.
    - apt and yum
        - Contains Distro Specific OS build assets and references dependencies through package manager.
            - This is how people get the latest. As soon as a version is in a distro, they get it there.
    - NuGet
        - NetCore.App packages Distro Agnostic Portable (glibc version)
        - (TBD: Distro Specific Portable for using specific RID's)

__OSX__

- Architectures:
    - x64

- OS's
    - OSX 10.11+

- Builds for each architecture:
    - Portable
      - Testing on the build OS where the build OS is highest supported stable OS.
      - Additional testing on lowest supported OS.

- Packages
    - tar.gz's
        - Portable binaries
        - Source which when extracted can reproduce all the build flavors with a simple build command with parameter for build flavors.
        - Pdb's matching the build for each build flavor.
    - pkg of Portable binaries
    - (TBD - Brew)
    - NuGet
        - NetCore.App packages Portable binary build.
