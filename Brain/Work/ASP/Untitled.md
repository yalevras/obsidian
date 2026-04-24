Pillow dupe

NISA takes raw image files and if compressed they are converted to JPG.


There is EXIF metadata on this files

First target
Unpack a jpg file and identify if it is grayscale YCbCr -> RGB

https://github.com/winlibs/libjpeg




ok so on vm

directory has asp and asp-lib-linalg
in asp
mkdir build
cd build
cmake ..
ccmake .
make
sudo make install
aspc to test that it worked

now in asp-lib-linalg
cd build
rm -r ./*
cmake ..
ccmake .        build_shared_libs ON, build_test_targets ON
make
make test




Need to support recognizing IHDR IDAT and IEND