gl4es for works on termux ( bugs not stable )

compilling: 
apt install xorgproto xcb* git cmake mesa-demos make build-essential clang llvm -y &&
git clone --depth 1 https://github.com/Mateus2022/gl4es-termux.git

cd gl4es-termux 

cmake -DDEFAULT_ES=2 -DNO_GBM=ON -DCMAKE_SYSTEM_NAME=Linux . && make -j8 

using:
| Environment Variable | Behavior |
|----------------------|----------|
| `LIBGL_FB=0`         | Does not work |
| `LIBGL_FB=1`         | Works but shows a black screen with high/strange FPS |
| `LIBGL_FB=2`         | Works but with a black screen and high/strange FPS |
| `LIBGL_FB=3`         | Works with low FPS in `glxgears` but shows an image in X11 |

gl4es-termux folder:
LD_LIBRARY_PATH=lib:/system/lib64 LIBGL_FB=3 glxgears 
