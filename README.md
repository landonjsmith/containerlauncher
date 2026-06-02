# Container Launcher

Container Launcher is a minimal native macOS GUI for launching Linux containers from Apple's `container` CLI.

As a personal project, I wanted a fast way to spin up a container without having to remember the exact command every time.
The entire app is written in Objective-C++ and built on Cocoa, with no third-party dependencies. It compiles to a self-contained `.app` bundle via CMake and links only against Apple's own Cocoa framework.

Container Launcher detects whether the `container` CLI is installed and whether the container system service is running, and surfaces inline banners to guide you through either step if something isn't ready, so you don't have to go hacking your way through the terminal. :-)

For the latest release information, please check the releases tab.

## Requirements

- Apple Silicon Mac (arm64)
- macOS 13.0+
- Xcode Command Line Tools: `xcode-select --install`
- CMake: `brew install cmake`
- Apple's `container` CLI installed at `/usr/local/bin/container` or `/opt/homebrew/bin/container`

## Building from Source

Requires an Apple Silicon Mac running macOS 13.0 or later.

Install the dependencies if you haven't already:
```bash
xcode-select --install
brew install cmake
```

Clone the repository and build:
```bash
git clone https://github.com/your-username/ContainerLauncher.git
cd ContainerLauncher
mkdir build && cd build
cmake .. -DCMAKE_BUILD_TYPE=Release
make -j$(sysctl -n hw.logicalcpu)
```

The compiled app bundle will be at `build/ContainerLauncher.app`. To install it:
```bash
cp -r build/ContainerLauncher.app /Applications/
```
## DMG NOTE: 
If you choose to install the pre-compiled DMG on your host Macintosh, you will have to allow the application to run via the security settings. 
This is simply because the application isn't signed with Apple's trusted developer certificates. I'm too poor to afford them. :-)
