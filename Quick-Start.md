# Install Tooling

## Required
### [Install Visual Studio](https://visualstudio.microsoft.com/downloads)
Install Visual Studio 2019 and up.

### Install Visual Studio deps
1. Run "Visual Studio Installer"
2. Select "Modify" on visual studio "Visual Studio"
3. Check ".Net desktop development"
4. Check "Universal Windows Platform development"
5. Under "Installation details/Universal Windows Platform development" 
   1. Check the the "Windows 10 SDK (10.0.19041.0)" is checked

### Install SDKs
1. Download and install [.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/visual-studio-sdks)
2. Download and install [.NET Framework 4.6.2 Developer Pack](https://dotnet.microsoft.com/download/visual-studio-sdks)

## Optional
### [XAML Styler](https://marketplace.visualstudio.com/items?itemName=TeamXavalon.XAMLStyler)

# Clone Repo
> **Warning:** Try not to clone the repo into any location where the path is already significantly long. There is a windows an existing MAX path issue with windows (Files on paths longer than 256 cannot be found be the build tool chain). Within the project there are paths of 190 characters, so the shorter the base directory the better.

```
git clone git@github.com:windows-toolkit/WindowsCommunityToolkit.git
```