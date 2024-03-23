# WSL 內建立 Flutter 開發環境

> Windows 子系統 Linux 版 （WSL） 是 Windows 的一項功能，可讓您在 Windows 電腦上執行 Linux 環境，而不需要個別的虛擬機或雙開機。

## Linux setup

### Install Java
To install the JDK, execute the following command, which will also install the JRE:
```sh
sudo apt install default-jdk
```
Add the following two lines to `/etc/profile` (setting the `JAVA_HOME` environment variable):
```
export JAVA_HOME="/usr/lib/jvm/java-11-openjdk-amd64"
export PATH="$JAVA_HOME/bin:$PATH"
```
Open a new terminal window to automatically source the file.

### Install Linux toolchain
For Linux desktop development, you need the following in addition to the Flutter SDK:
```sh
sudo apt install clang cmake ninja-build pkg-config libgtk-3-dev liblzma-dev
```

### Install Google Chrome (if needed)
Refer to Microsoft's instructions below.

## Install Flutter

### Install Flutter manually
1. Create a `Downloads` directory if it doesn’t already exist, and navigate to it.
```sh
mkdir -p $HOME/Downloads && cd "$_"
```
2. Download the latest stable [release](https://docs.flutter.dev/development/tools/sdk/releases?tab=linux) of the Flutter SDK _(Right-click and select “Copy link” to copy the address of the archive.):_
```sh
wget <latest stable of the Flutter SDK URL>
```
3. Create an `Applications` directory if it doesn’t already exist, and navigate to it.
```sh
mkdir -p $HOME/Applications && cd "$_"
```
4. Extract the Flutter files from the archive in the `Downloads` directory to the `Applications` directory.
```sh
tar xfv $HOME/Downloads/$(ls -d $HOME/Downloads/flutter*.tar.xz | xargs basename)
```

### Update your path

```bash
nano ~/.bashrc
```
Add the following line to `.bashrc`:
```
export PATH="$HOME/Applications/flutter/bin:$PATH"
```
run
```bash
source  ~/.bashrc
```

其他的 shell

ex: `.zshrc`

### Run flutter doctor

Run the following command to see if there are any dependencies you need to install to complete the setup (for verbose output, add the -v flag):
```sh
flutter doctor
```

## Install Android Studio

1. [Android Studio 系統需求](https://developer.android.com/codelabs/basic-android-kotlin-compose-install-android-studio?hl=zh-tw#5)
2. Download the latest stable of Android Studio. [download](https://developer.android.com/studio/?gclid=Cj0KCQiAjJOQBhCkARIsAEKMtO3zEhdK4_I0CEZic3UH4dl-9gVXuHFR9dCl3TOHKjmv3xWLU3UxfhYaApfAEALw_wcB&gclsrc=aw.ds&hl=zh-tw)
```sh
mkdir -p $HOME/Downloads && cd "$_"
```
3. Create an `Applications` directory if it doesn’t already exist, and navigate to it.
```bash
mkdir -p $HOME/Applications && cd "$_"
```
4. Extract the Flutter files from the archive in the `Downloads` directory to the `Applications` directory.
```bash
tar xfv $HOME/Downloads/$(ls -d $HOME/Downloads/android-studio*.tar.gz | xargs basename)
```
5. Configure flutter to use this installation
```bash
flutter config --android-studio-dir $HOME/Applications/android-studio/
```
6. create an alias
```bash
alias android-studio=$HOME/Applications/android-studio/bin/studio.sh
```
> 可以將上述指令加入環境變數中. ex:`.bashrc`, `.zshrc`
7. Run the studio
```bash
android-studio
```

### Agree to Android Licenses
```sh
flutter doctor --android-licenses
```

## References
- [Set up a WSL development environment](https://learn.microsoft.com/en-us/windows/wsl/setup/environment)
- [Install Google Chrome for Linux](https://learn.microsoft.com/en-us/windows/wsl/tutorials/gui-apps#install-google-chrome-for-linux)
- [Installing Android Studio on WSL2 for Flutter](https://addshore.com/2022/01/installing-android-studio-on-wsl2-for-flutter/)
- [開始安裝時遇到的各種令人厭煩的issues](https://ithelp.ithome.com.tw/articles/10341701)