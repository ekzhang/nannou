# Platform-specific Setup

Depending on what OS you are running, you might require an extra step or two.

- **All Platforms**

  For now, nannou requires that you have both `python` and `cmake` installed.
  These are required by a tool called `shaderc`. The role of this tool is to
  compile GLSL shaders to SPIR-V so that we may run them using the system's
  Vulkan implementation. There are a few attempts at pure-rust alternatives to
  this tool in the works and we hope to switch to one of these in the near
  future to avoid the need for these extra dependencies.

- **macOS**: Ensure that you have xcode-tools installed:

  ```bash
  xcode-select --install
  ```

  In order to add support for [Vulkan](https://www.khronos.org/vulkan/) (the
  graphics backend used by nannou) to macOS, nannou will prompt you and attempt
  to automatically download and install the [MoltenVK
  SDK](https://github.com/KhronosGroup/MoltenVK). MoltenVK is a driver-level
  implementation of the Vulkan graphics and compute API, that runs on Apple's
  Metal graphics and compute framework on both iOS and macOS. If you wish to
  update your MoltenVK SDK version, simply remove the currently installed SDK
  (this should be at `~/.vulkan_sdk`) and nannou will prompt you about
  downloading and installing the next version the next time you attempt to build
  a nannou project.

- **Linux**: ensure you have the following system packages installed:

  - **alsa dev package**

    For Fedora users:
    ```bash
    sudo dnf install alsa-lib-devel
    ```

    For Debian/Ubuntu users:
    ```bash
    sudo apt-get install libasound2-dev
    ```

    For Arch users:
    ```bash
    sudo pacman -S alsa-lib
    ```

  - **curl lib dev package**

    Nannou depends on the `curl-sys` crate. Some Linux distributions use
    LibreSSL instead of OpenSSL (such as AlpineLinux, Voidlinux, possibly
    [others](https://en.wikipedia.org/wiki/LibreSSL#Adoption) if manually
    installed).

- **Windows**: Install the `ninja` tool.

  This tool is another required by the `shaderc` tool as mentioned under the
  "All Platforms" section above. Installation of this tool can be a little
  finicky so we are aiming to improve this section of the guide soon, but for
  now, here is a link to the [ninja
  releases](https://github.com/ninja-build/ninja/releases).