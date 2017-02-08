**Builds and Packages of .NET Core 2.0 Runtime**

__Windows__

- Architectures:
    - x86 (support)
    - x64 (support)
    - arm32 (build and test)
    - arm64 (TODO)

- OS's
    Windows 7 SP1+ (Test on Windows 7 SP1, Win10)
    Windows Server (TODO versions and Nano)

- Builds for each architecture:
    - All OS's
      - Build and testing on latest stable supported OS version.
      - Additional testing on lowest supported OS version. 
      - Testing on Full .NET Framework for some binaries for compat.
      - Testing in UWP and CoreRT for compat.

- Packages
    - zip's
        - libraries for each build flavor
        - Source which when extracted can reproduce all the build combo's with a simple build command with parameter for build combo.
        - Pdb's matching the build for each build flavor.
    - Msi installers for each architecture
    - NuGet
        - NetCore.App packages containing results of the build that runs on all OS's.
    - Docker containers
        - TODO: What's in here.

__Linux__

- Architectures:
    - x86 (build and test for community support)
    - x64 (support)
    - arm32 (build and test)

- OS's for testing and binary distribution
    - RHEL
        - 7+
    - Centos
        - 7+
    - Debian
        - 8+ (Test on (TODO min) and 8.7 as latest)
    - Ubuntu
        - 14.04 (TODO)
        - 16.04
        - 16.10
        - 17.04 (TODO: release date April 2017)
    - Fedora
        - 25
        - 26 (Release date 6/6/2017)
    - OpenSuse
        - 42.2
    - Alpine (TODO)

- Builds for each architecture:
    - Distro Agnostic (glibc version 2.14) (TODO: Builds on which OS?)
        - Carries local dynamically linked OS dependencies.
        - Testing of the result of this build needs to happen on all OS's.
    - Distro Specific with dependencies
        - Dynamically linked against the OS copy of dependencies.
        - This is the way distros build and we build for our native package manager packages.
        - Testing is on the same OS as built on.
    - (TBD: Distro Specific without dependencies)
        - This would be to provide RID specific capabilities for standalone apps that can be distro specific without needing to install dependencies.
        - Testing on this would be on the OS it was built on.
    - Docker containers
        - TODO: What's in here.

- Packages
    - tar.gz's
        - Contains Distro Agnostic binaries.
        - (TBD: Contains the Distro Specific without depencies binaries)
        - Source which when extracted can reproduce all the build combo's with a simple build command with parameter for build combos.
        - Pdb's matching the build for each build flavor.
    - rpm and deb
        - Contains Distro Specific with dependencies build assets and references dependencies through package manager.
            - This is how people get the latest. As soon as a version is in a distro, they get it there.
    - NuGet
        - NetCore.App packages Distro Agnostic binaries
        - (TBD: Distro Specific withtout dependencies for using specific RID's)

__OSX__

- Architectures:
    - x64 (support)

- OS's
    - OSX 10.11+ (Tested on 10.11 and 10.12: TODO: 10.13 dates?)

- Builds for each architecture:
    - All OS's
      - Additional testing on lowest supported OS.

- Packages
    - tar.gz's
        - binaries
        - Source which when extracted can reproduce all the build combos with a simple build command with parameter for build combos.
        - Pdb's matching the build for each build flavor.
    - pkg of binaries
    - (TBD - Brew)
    - NuGet
        - NetCore.App packages binary build that will run on any OS.
