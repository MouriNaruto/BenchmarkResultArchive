# benchncnn

## Build

```
mkdir Workspace
sudo apt install build-essential git cmake
cd Workspace/
git clone https://github.com/Tencent/ncnn
cd ncnn/
git checkout -b benchmark 20260113
git log
rm -rf build
cmake -B build -DCMAKE_BUILD_TYPE=Release -DNCNN_BUILD_BENCHMARK=ON -DNCNN_BUILD_TOOLS=OFF -DNCNN_BUILD_EXAMPLES=OFF -DNCNN_BUILD_TESTS=OFF -DNCNN_VULKAN=OFF
cmake --build build -j $(nproc)
ls build/benchmark/
cd build/benchmark/
```

## Tests

```
./benchncnn 512 1 0 -1 0
./benchncnn 512 2 0 -1 0
./benchncnn 512 4 0 -1 0
./benchncnn 512 8 0 -1 0
./benchncnn 512 16 0 -1 0
./benchncnn 512 32 0 -1 0
./benchncnn 512 64 0 -1 0
```

## Results

```

```
