# Final h-encore
a tool to push h-encore exploit for PS VITA/PS TV automatically

# CREDITS
see [CREDITS.md](CREDITS.md)

# Prebuilt binaries for windows/macOS
Check [latest release](https://github.com/soarqin/finalhe/releases/latest)

# Notes on windows
Please install QcmaDriver_winusb.exe(can be downloaded from releases) if you have not installed USB driver for PS Vita

# Prerequisites for build
1. For OSX/macOS: install [brew](https://brew.sh), install libusb & qt through brew (```brew install libusb qt```)
2. For Linux:
   1. (Debian/Ubuntu) install build-essential, libxml2-dev, libusb-dev, zlib-dev or zlib1g-dev, qtbase5-dev, qttools5, cmake(if use cmake to build)
   2. (Fedora/CentOS) group install "Development Tools", install libxml2-devel, libusb-devel, zlib-devel, qt5-qtbase-devel, qt5-qtbase, cmake3(if use cmake to build)
   3. (Arch) install base-devel, libxml2, libusb, zlib, qt5, cmake(if use cmake to build)

# Build from source
You can choose either qmake or cmake to build
1. cmake: just run cmake to generate Makefile for compiling, for OSX/macOS it cannot produce app bundle, and you need to specify CMAKE_PREFIX_PATH if Qt is not installed in default location:
```
cmake -DCMAKE_PREFIX_PATH=<Path of Qt Root> <Path of Project Root>
```
2. qmake: just run qmake to generate Makefile for compiling, run ```make lcopy``` in ```src``` folder to compile translations and copy them to binary folder.

# Contribute to translations
1. For coders that using Qt:
   1. If you are using qmake, add your language to this line in src/src.pro: ```TRANSLATIONS += ...```, and re-generate Makefile from qmake, the run ```make lupdate``` in src folder, you will get new generated .ts files in src/languages

      If you are using cmake, add your language to this line in src/CMakeLists.txt: ```set(TRANSLATION_FILES ...```, and re-generate Makefile/project from cmake, compile it, you will get new generated .ts files in src/languages
   2. Open .ts files with Qt Linquist tool and translate strings into native language
   3. If you are using qmake, run ```make lcopy``` in src folder and you will get compiled .qm files in languages folder

      If you are using cmake, compile the project and you will get compiled .qm files in language folder

2. For non-coders:
   1. Copy translations/en_US.ts to a new file with filename in [IETF language tag](https://datahub.io/core/language-codes/r/3.html) form (but replace "-" with "_")
   2. Open the .ts file, it is just in xml format, go through all elements of ```<translation type="unfinished">``` to translate, and remove the property ```type="unfinished"``` from translated items
