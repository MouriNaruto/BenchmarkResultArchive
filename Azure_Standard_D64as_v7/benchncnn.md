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
```

With AVX512

```
cd ~/Workspace/ncnn/
rm -rf build
cmake -B build -DCMAKE_BUILD_TYPE=Release -DNCNN_BUILD_BENCHMARK=ON -DNCNN_BUILD_TOOLS=OFF -DNCNN_BUILD_EXAMPLES=OFF -DNCNN_BUILD_TESTS=OFF -DNCNN_VULKAN=OFF
cmake --build build -j $(nproc)
ls build/benchmark/
cd build/benchmark/
```

Without AVX512

```
cd ~/Workspace/ncnn/
rm -rf build
cmake -B build -DCMAKE_BUILD_TYPE=Release -DNCNN_BUILD_BENCHMARK=ON -DNCNN_BUILD_TOOLS=OFF -DNCNN_BUILD_EXAMPLES=OFF -DNCNN_BUILD_TESTS=OFF -DNCNN_VULKAN=OFF -DNCNN_AVX512=OFF -DNCNN_AVX512VNNI=OFF
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

## Results (With AVX512)

```
misaki@HimiMisakiBenchmarkAMD64:~/Workspace/ncnn/build/benchmark$ ./benchncnn 512 1 0 -1 0
loop_count = 512
num_threads = 1
powersave = 0
gpu_device = -1
cooling_down = 0
          squeezenet  min =    3.05  max =    3.12  avg =    3.07
     squeezenet_int8  min =    2.11  max =    2.17  avg =    2.13
           mobilenet  min =    5.36  max =    6.21  avg =    5.40
      mobilenet_int8  min =    4.61  max =    4.76  avg =    4.63
        mobilenet_v2  min =    3.70  max =    3.80  avg =    3.73
        mobilenet_v3  min =    3.15  max =    3.20  avg =    3.17
          shufflenet  min =    2.06  max =    2.14  avg =    2.07
       shufflenet_v2  min =    2.20  max =    2.24  avg =    2.21
             mnasnet  min =    3.75  max =    5.14  avg =    3.81
     proxylessnasnet  min =    4.39  max =    4.57  avg =    4.42
     efficientnet_b0  min =    6.17  max =    6.29  avg =    6.20
   efficientnetv2_b0  min =    7.34  max =    7.55  avg =    7.40
        regnety_400m  min =    5.82  max =    6.28  avg =    5.86
           blazeface  min =    0.70  max =    0.72  avg =    0.70
           googlenet  min =   13.67  max =   14.25  avg =   13.85
      googlenet_int8  min =    8.69  max =    8.99  avg =    8.77
            resnet18  min =   13.65  max =   14.34  avg =   13.82
       resnet18_int8  min =    8.17  max =    8.86  avg =    8.30
             alexnet  min =    9.76  max =   10.56  avg =    9.94
               vgg16  min =   58.78  max =   61.97  avg =   60.11
          vgg16_int8  min =   45.04  max =   48.17  avg =   46.30
            resnet50  min =   32.00  max =   33.84  avg =   32.43
       resnet50_int8  min =   17.30  max =   18.04  avg =   17.50
      squeezenet_ssd  min =    9.85  max =   10.44  avg =    9.95
 squeezenet_ssd_int8  min =    7.70  max =    8.01  avg =    7.83
       mobilenet_ssd  min =   11.50  max =   11.85  avg =   11.56
  mobilenet_ssd_int8  min =    8.92  max =    9.32  avg =    8.95
      mobilenet_yolo  min =   25.84  max =   27.61  avg =   25.93
  mobilenetv2_yolov3  min =   14.21  max =   14.89  avg =   14.32
         yolov4-tiny  min =   22.64  max =   23.84  avg =   23.07
           nanodet_m  min =    5.18  max =    5.53  avg =    5.21
    yolo-fastest-1.1  min =    2.13  max =    2.22  avg =    2.14
      yolo-fastestv2  min =    2.15  max =    2.18  avg =    2.16
  vision_transformer  min =  487.55  max =  495.92  avg =  489.27
          FastestDet  min =    2.20  max =    2.28  avg =    2.22
misaki@HimiMisakiBenchmarkAMD64:~/Workspace/ncnn/build/benchmark$ ./benchncnn 512 2 0 -1 0
loop_count = 512
num_threads = 2
powersave = 0
gpu_device = -1
cooling_down = 0
          squeezenet  min =    3.01  max =    3.12  avg =    3.04
     squeezenet_int8  min =    2.90  max =    3.10  avg =    2.96
           mobilenet  min =    4.04  max =    4.23  avg =    4.07
      mobilenet_int8  min =    3.29  max =    3.54  avg =    3.39
        mobilenet_v2  min =    4.09  max =    4.23  avg =    4.13
        mobilenet_v3  min =    3.35  max =    3.41  avg =    3.38
          shufflenet  min =    3.38  max =    3.54  avg =    3.41
       shufflenet_v2  min =    2.80  max =    2.88  avg =    2.82
             mnasnet  min =    3.80  max =    3.85  avg =    3.82
     proxylessnasnet  min =    4.18  max =    4.32  avg =    4.21
     efficientnet_b0  min =    5.41  max =    5.54  avg =    5.44
   efficientnetv2_b0  min =    6.73  max =    7.15  avg =    6.77
        regnety_400m  min =    6.84  max =    7.07  avg =    6.88
           blazeface  min =    1.01  max =    1.07  avg =    1.03
           googlenet  min =   10.83  max =   11.54  avg =   10.99
      googlenet_int8  min =    7.04  max =    7.29  avg =    7.11
            resnet18  min =    9.06  max =    9.66  avg =    9.21
       resnet18_int8  min =    6.06  max =    6.51  avg =    6.21
             alexnet  min =    6.28  max =    6.56  avg =    6.38
               vgg16  min =   35.92  max =   37.39  avg =   36.35
          vgg16_int8  min =   26.88  max =   28.22  avg =   27.28
            resnet50  min =   20.48  max =   21.40  avg =   20.66
       resnet50_int8  min =   13.60  max =   14.23  avg =   13.86
      squeezenet_ssd  min =    9.18  max =    9.81  avg =    9.37
 squeezenet_ssd_int8  min =    7.89  max =    8.27  avg =    7.98
       mobilenet_ssd  min =    8.71  max =    8.99  avg =    8.80
  mobilenet_ssd_int8  min =    6.28  max =    6.42  avg =    6.31
      mobilenet_yolo  min =   19.86  max =   20.59  avg =   20.02
  mobilenetv2_yolov3  min =   13.00  max =   13.38  avg =   13.06
         yolov4-tiny  min =   18.19  max =   18.93  avg =   18.37
           nanodet_m  min =    6.38  max =    6.52  avg =    6.42
    yolo-fastest-1.1  min =    3.31  max =    3.53  avg =    3.34
      yolo-fastestv2  min =    3.17  max =    3.34  avg =    3.21
  vision_transformer  min =  250.44  max =  261.90  avg =  251.33
          FastestDet  min =    3.22  max =    3.30  avg =    3.24
misaki@HimiMisakiBenchmarkAMD64:~/Workspace/ncnn/build/benchmark$ ./benchncnn 512 4 0 -1 0
loop_count = 512
num_threads = 4
powersave = 0
gpu_device = -1
cooling_down = 0
          squeezenet  min =    2.32  max =    2.38  avg =    2.35
     squeezenet_int8  min =    2.43  max =    2.52  avg =    2.47
           mobilenet  min =    2.54  max =    2.68  avg =    2.58
      mobilenet_int8  min =    2.02  max =   10.84  avg =    2.14
        mobilenet_v2  min =    3.14  max =    4.66  avg =    3.18
        mobilenet_v3  min =    2.83  max =    2.93  avg =    2.86
          shufflenet  min =    3.10  max =    4.62  avg =    3.15
       shufflenet_v2  min =    2.39  max =    2.47  avg =    2.42
             mnasnet  min =    2.97  max =    3.23  avg =    3.00
     proxylessnasnet  min =    3.10  max =    3.25  avg =    3.13
     efficientnet_b0  min =    4.21  max =    6.42  avg =    4.26
   efficientnetv2_b0  min =    5.11  max =    5.36  avg =    5.17
        regnety_400m  min =    6.71  max =    6.95  avg =    6.81
           blazeface  min =    0.93  max =    1.00  avg =    0.97
           googlenet  min =    7.15  max =    7.53  avg =    7.24
      googlenet_int8  min =    5.11  max =    5.41  avg =    5.22
            resnet18  min =    4.96  max =   16.14  avg =    5.08
       resnet18_int8  min =    3.34  max =    3.59  avg =    3.42
             alexnet  min =    3.53  max =    3.70  avg =    3.61
               vgg16  min =   20.70  max =   22.45  avg =   20.96
          vgg16_int8  min =   16.60  max =   18.46  avg =   17.05
            resnet50  min =   11.78  max =   12.43  avg =   11.94
       resnet50_int8  min =    8.06  max =    9.63  avg =    8.17
      squeezenet_ssd  min =    6.82  max =    7.60  avg =    7.00
 squeezenet_ssd_int8  min =    5.97  max =    6.29  avg =    6.10
       mobilenet_ssd  min =    5.56  max =    5.77  avg =    5.62
  mobilenet_ssd_int8  min =    4.12  max =    4.22  avg =    4.15
      mobilenet_yolo  min =   13.27  max =   14.16  avg =   13.50
  mobilenetv2_yolov3  min =    9.38  max =    9.79  avg =    9.43
         yolov4-tiny  min =   12.67  max =   13.28  avg =   12.85
           nanodet_m  min =    5.17  max =    5.44  avg =    5.23
    yolo-fastest-1.1  min =    3.35  max =    3.55  avg =    3.39
      yolo-fastestv2  min =    3.13  max =    3.22  avg =    3.17
  vision_transformer  min =  131.06  max =  136.44  avg =  131.58
          FastestDet  min =    3.11  max =    3.27  avg =    3.15
misaki@HimiMisakiBenchmarkAMD64:~/Workspace/ncnn/build/benchmark$ ./benchncnn 512 8 0 -1 0
loop_count = 512
num_threads = 8
powersave = 0
gpu_device = -1
cooling_down = 0
          squeezenet  min =    2.11  max =    2.33  avg =    2.15
     squeezenet_int8  min =    2.26  max =    2.38  avg =    2.32
           mobilenet  min =    2.01  max =    2.10  avg =    2.04
      mobilenet_int8  min =    1.61  max =    1.73  avg =    1.64
        mobilenet_v2  min =    2.85  max =    2.97  avg =    2.90
        mobilenet_v3  min =    2.66  max =    3.85  avg =    2.72
          shufflenet  min =    3.13  max =    3.24  avg =    3.19
       shufflenet_v2  min =    2.27  max =    2.41  avg =    2.31
             mnasnet  min =    2.64  max =    2.82  avg =    2.68
     proxylessnasnet  min =    2.73  max =    2.82  avg =    2.78
     efficientnet_b0  min =    3.62  max =    3.75  avg =    3.67
   efficientnetv2_b0  min =    4.72  max =    5.52  avg =    4.79
        regnety_400m  min =    6.61  max =    6.99  avg =    6.81
           blazeface  min =    0.98  max =    1.13  avg =    1.01
           googlenet  min =    6.18  max =    6.44  avg =    6.27
      googlenet_int8  min =    4.44  max =    4.61  avg =    4.50
            resnet18  min =    3.70  max =    5.01  avg =    3.77
       resnet18_int8  min =    3.08  max =    3.26  avg =    3.14
             alexnet  min =    2.24  max =    2.43  avg =    2.28
               vgg16  min =   13.85  max =   15.77  avg =   14.04
          vgg16_int8  min =   10.57  max =   11.49  avg =   10.93
            resnet50  min =    8.22  max =    8.57  avg =    8.31
       resnet50_int8  min =    6.22  max =    6.57  avg =    6.35
      squeezenet_ssd  min =    5.76  max =    6.11  avg =    5.85
 squeezenet_ssd_int8  min =    5.43  max =    5.72  avg =    5.52
       mobilenet_ssd  min =    4.27  max =    4.91  avg =    4.33
  mobilenet_ssd_int8  min =    3.05  max =    3.23  avg =    3.10
      mobilenet_yolo  min =   10.64  max =   11.34  avg =   10.87
  mobilenetv2_yolov3  min =    7.66  max =    8.00  avg =    7.73
         yolov4-tiny  min =   10.77  max =   11.44  avg =   10.95
           nanodet_m  min =    4.65  max =    4.83  avg =    4.70
    yolo-fastest-1.1  min =    3.33  max =    3.51  avg =    3.39
      yolo-fastestv2  min =    3.01  max =    3.15  avg =    3.06
  vision_transformer  min =   70.74  max =   73.98  avg =   71.04
          FastestDet  min =    3.07  max =    3.29  avg =    3.13
misaki@HimiMisakiBenchmarkAMD64:~/Workspace/ncnn/build/benchmark$ ./benchncnn 512 16 0 -1 0
loop_count = 512
num_threads = 16
powersave = 0
gpu_device = -1
cooling_down = 0
          squeezenet  min =    2.23  max =    2.47  avg =    2.28
     squeezenet_int8  min =    2.50  max =    2.62  avg =    2.56
           mobilenet  min =    2.15  max =    2.37  avg =    2.23
      mobilenet_int8  min =    1.59  max =    2.80  avg =    1.65
        mobilenet_v2  min =    2.97  max =    3.12  avg =    3.04
        mobilenet_v3  min =    2.91  max =    3.07  avg =    3.00
          shufflenet  min =    3.66  max =    3.86  avg =    3.73
       shufflenet_v2  min =    2.60  max =    2.79  avg =    2.68
             mnasnet  min =    2.85  max =    2.98  avg =    2.91
     proxylessnasnet  min =    3.01  max =    3.83  avg =    3.08
     efficientnet_b0  min =    3.93  max =    4.12  avg =    3.99
   efficientnetv2_b0  min =    5.20  max =    5.49  avg =    5.31
        regnety_400m  min =    8.34  max =    8.81  avg =    8.54
           blazeface  min =    1.18  max =    1.29  avg =    1.23
           googlenet  min =    6.19  max =    6.81  avg =    6.28
      googlenet_int8  min =    4.82  max =    5.07  avg =    4.94
            resnet18  min =    3.62  max =    4.03  avg =    3.73
       resnet18_int8  min =    3.27  max =    3.52  avg =    3.37
             alexnet  min =    1.98  max =    2.55  avg =    2.03
               vgg16  min =   13.41  max =   14.36  avg =   14.01
          vgg16_int8  min =   10.02  max =   10.36  avg =   10.13
            resnet50  min =    7.68  max =    8.25  avg =    7.86
       resnet50_int8  min =    5.88  max =    6.11  avg =    5.98
      squeezenet_ssd  min =    6.18  max =    6.69  avg =    6.36
 squeezenet_ssd_int8  min =    6.01  max =    6.36  avg =    6.17
       mobilenet_ssd  min =    4.43  max =    4.79  avg =    4.53
  mobilenet_ssd_int8  min =    3.27  max =    5.30  avg =    3.38
      mobilenet_yolo  min =   11.74  max =   12.99  avg =   12.46
  mobilenetv2_yolov3  min =    7.56  max =    7.86  avg =    7.65
         yolov4-tiny  min =   10.45  max =   11.00  avg =   10.60
           nanodet_m  min =    5.20  max =    5.38  avg =    5.28
    yolo-fastest-1.1  min =    3.76  max =    3.90  avg =    3.82
      yolo-fastestv2  min =    3.43  max =    3.58  avg =    3.49
  vision_transformer  min =   44.35  max =   45.94  avg =   44.59
          FastestDet  min =    3.39  max =    3.56  avg =    3.46
misaki@HimiMisakiBenchmarkAMD64:~/Workspace/ncnn/build/benchmark$ ./benchncnn 512 32 0 -1 0
loop_count = 512
num_threads = 32
powersave = 0
gpu_device = -1
cooling_down = 0
          squeezenet  min =    2.48  max =    2.75  avg =    2.59
     squeezenet_int8  min =    2.81  max =    3.03  avg =    2.90
           mobilenet  min =    2.39  max =    2.84  avg =    2.48
      mobilenet_int8  min =    1.87  max =    1.99  avg =    1.92
        mobilenet_v2  min =    3.39  max =    3.60  avg =    3.47
        mobilenet_v3  min =    3.40  max =    3.66  avg =    3.53
          shufflenet  min =    4.34  max =    4.58  avg =    4.45
       shufflenet_v2  min =    3.11  max =    3.32  avg =    3.21
             mnasnet  min =    3.31  max =    3.54  avg =    3.38
     proxylessnasnet  min =    3.49  max =    3.72  avg =    3.60
     efficientnet_b0  min =    4.66  max =    4.93  avg =    4.78
   efficientnetv2_b0  min =    6.06  max =    6.45  avg =    6.26
        regnety_400m  min =   10.58  max =   11.61  avg =   11.01
           blazeface  min =    1.42  max =    1.65  avg =    1.49
           googlenet  min =    6.76  max =    8.08  avg =    7.07
      googlenet_int8  min =    5.60  max =    7.10  avg =    5.80
            resnet18  min =    3.58  max =    3.92  avg =    3.70
       resnet18_int8  min =    3.53  max =    3.76  avg =    3.63
             alexnet  min =    2.05  max =    2.23  avg =    2.09
               vgg16  min =   12.94  max =   13.88  avg =   13.34
          vgg16_int8  min =   10.98  max =   11.59  avg =   11.30
            resnet50  min =    8.05  max =    8.42  avg =    8.20
       resnet50_int8  min =    6.35  max =    6.80  avg =    6.51
      squeezenet_ssd  min =    6.58  max =    7.64  avg =    6.78
 squeezenet_ssd_int8  min =    6.53  max =    6.88  avg =    6.70
       mobilenet_ssd  min =    4.73  max =    4.98  avg =    4.83
  mobilenet_ssd_int8  min =    3.81  max =    3.99  avg =    3.89
      mobilenet_yolo  min =   14.36  max =   15.85  avg =   14.96
  mobilenetv2_yolov3  min =    8.07  max =    8.43  avg =    8.29
         yolov4-tiny  min =   10.94  max =   11.62  avg =   11.10
           nanodet_m  min =    5.81  max =    6.16  avg =    5.95
    yolo-fastest-1.1  min =    4.11  max =    4.31  avg =    4.19
      yolo-fastestv2  min =    3.71  max =    4.03  avg =    3.81
  vision_transformer  min =   31.80  max =   33.94  avg =   32.34
          FastestDet  min =    3.68  max =    3.89  avg =    3.76
misaki@HimiMisakiBenchmarkAMD64:~/Workspace/ncnn/build/benchmark$ ./benchncnn 512 64 0 -1 0
loop_count = 512
num_threads = 64
powersave = 0
gpu_device = -1
cooling_down = 0
          squeezenet  min =    2.92  max =    3.32  avg =    2.99
     squeezenet_int8  min =    3.35  max =    5.85  avg =    3.41
           mobilenet  min =    2.78  max =    3.13  avg =    2.82
      mobilenet_int8  min =    2.36  max =    3.38  avg =    2.40
        mobilenet_v2  min =    3.94  max =    4.25  avg =    4.02
        mobilenet_v3  min =    4.01  max =    4.27  avg =    4.08
          shufflenet  min =    5.14  max =    6.33  avg =    5.23
       shufflenet_v2  min =    3.63  max =    6.99  avg =    3.71
             mnasnet  min =    3.68  max =   11.08  avg =    3.76
     proxylessnasnet  min =    3.94  max =   10.92  avg =    4.01
     efficientnet_b0  min =    5.33  max =   10.15  avg =    5.46
   efficientnetv2_b0  min =    7.08  max =   42.44  avg =    7.33
        regnety_400m  min =   13.65  max =   19.35  avg =   13.90
           blazeface  min =    1.75  max =    1.91  avg =    1.79
           googlenet  min =    7.83  max =    9.25  avg =    7.91
      googlenet_int8  min =    6.59  max =    7.00  avg =    6.67
            resnet18  min =    4.29  max =    5.96  avg =    4.38
       resnet18_int8  min =    4.23  max =    4.81  avg =    4.34
             alexnet  min =    2.20  max =    2.50  avg =    2.26
               vgg16  min =   14.70  max =   16.55  avg =   15.05
          vgg16_int8  min =   12.53  max =   19.73  avg =   12.83
            resnet50  min =    9.02  max =   16.46  avg =    9.26
       resnet50_int8  min =    7.42  max =    7.91  avg =    7.56
      squeezenet_ssd  min =    7.53  max =   15.76  avg =    7.64
 squeezenet_ssd_int8  min =    7.87  max =   15.31  avg =    8.07
       mobilenet_ssd  min =    5.38  max =    5.68  avg =    5.47
  mobilenet_ssd_int8  min =    4.54  max =    5.51  avg =    4.64
      mobilenet_yolo  min =   19.93  max =   26.80  avg =   20.50
  mobilenetv2_yolov3  min =    8.97  max =   10.37  avg =    9.13
         yolov4-tiny  min =   12.47  max =   20.03  avg =   12.73
           nanodet_m  min =    6.73  max =   17.09  avg =    6.93
    yolo-fastest-1.1  min =    4.97  max =    5.24  avg =    5.02
      yolo-fastestv2  min =    4.68  max =    6.10  avg =    4.73
  vision_transformer  min =   27.70  max =   35.29  avg =   28.02
          FastestDet  min =    4.48  max =    4.81  avg =    4.52
```

## Results (Without AVX512)

```
misaki@HimiMisakiBenchmarkAMD64:~/Workspace/ncnn/build/benchmark$ ./benchncnn 512 1 0 -1 0
loop_count = 512
num_threads = 1
powersave = 0
gpu_device = -1
cooling_down = 0
          squeezenet  min =    5.23  max =    5.47  avg =    5.26
     squeezenet_int8  min =    2.91  max =    2.99  avg =    2.93
           mobilenet  min =    9.79  max =   10.28  avg =    9.83
      mobilenet_int8  min =    6.12  max =    6.45  avg =    6.14
        mobilenet_v2  min =    6.14  max =    6.24  avg =    6.17
        mobilenet_v3  min =    4.89  max =    5.17  avg =    4.92
          shufflenet  min =    2.92  max =    3.09  avg =    2.95
       shufflenet_v2  min =    3.21  max =    4.54  avg =    3.23
             mnasnet  min =    6.19  max =    6.35  avg =    6.22
     proxylessnasnet  min =    7.49  max =    8.59  avg =    7.52
     efficientnet_b0  min =   14.91  max =   15.64  avg =   14.99
   efficientnetv2_b0  min =   15.83  max =   17.45  avg =   15.99
        regnety_400m  min =    8.44  max =    8.81  avg =    8.48
           blazeface  min =    0.82  max =    0.85  avg =    0.83
           googlenet  min =   23.07  max =   24.18  avg =   23.29
      googlenet_int8  min =   13.67  max =   14.31  avg =   13.78
            resnet18  min =   20.52  max =   21.77  avg =   20.92
       resnet18_int8  min =   11.86  max =   12.41  avg =   12.00
             alexnet  min =   15.25  max =   16.89  avg =   15.56
               vgg16  min =   94.69  max =  100.51  avg =   95.59
          vgg16_int8  min =   65.95  max =   69.48  avg =   66.82
            resnet50  min =   53.29  max =   56.36  avg =   53.69
       resnet50_int8  min =   25.35  max =   27.04  avg =   25.55
      squeezenet_ssd  min =   14.97  max =   15.50  avg =   15.14
 squeezenet_ssd_int8  min =   10.25  max =   10.86  avg =   10.42
       mobilenet_ssd  min =   20.69  max =   21.83  avg =   20.78
  mobilenet_ssd_int8  min =   11.79  max =   12.38  avg =   11.83
      mobilenet_yolo  min =   46.22  max =   48.51  avg =   46.35
  mobilenetv2_yolov3  min =   23.23  max =   24.54  avg =   23.35
         yolov4-tiny  min =   35.22  max =   37.03  avg =   35.65
           nanodet_m  min =    7.68  max =    7.78  avg =    7.70
    yolo-fastest-1.1  min =    2.88  max =    3.06  avg =    2.90
      yolo-fastestv2  min =    2.75  max =    2.82  avg =    2.76
  vision_transformer  min =  339.55  max =  354.86  avg =  341.84
          FastestDet  min =    3.09  max =    3.12  avg =    3.10
misaki@HimiMisakiBenchmarkAMD64:~/Workspace/ncnn/build/benchmark$ ./benchncnn 512 2 0 -1 0
loop_count = 512
num_threads = 2
powersave = 0
gpu_device = -1
cooling_down = 0
          squeezenet  min =    3.84  max =    3.94  avg =    3.87
     squeezenet_int8  min =    3.48  max =    3.65  avg =    3.53
           mobilenet  min =    6.12  max =    6.26  avg =    6.15
      mobilenet_int8  min =    4.19  max =    4.46  avg =    4.26
        mobilenet_v2  min =    5.07  max =    5.28  avg =    5.10
        mobilenet_v3  min =    4.06  max =    4.23  avg =    4.09
          shufflenet  min =    3.70  max =    3.83  avg =    3.73
       shufflenet_v2  min =    3.09  max =    4.38  avg =    3.12
             mnasnet  min =    4.80  max =    4.90  avg =    4.83
     proxylessnasnet  min =    5.34  max =    5.57  avg =    5.37
     efficientnet_b0  min =    9.68  max =   10.01  avg =    9.73
   efficientnetv2_b0  min =   10.50  max =   11.00  avg =   10.60
        regnety_400m  min =    7.90  max =    8.24  avg =    7.94
           blazeface  min =    1.04  max =    1.12  avg =    1.07
           googlenet  min =   15.48  max =   16.18  avg =   15.68
      googlenet_int8  min =    9.39  max =    9.84  avg =    9.48
            resnet18  min =   12.38  max =   13.10  avg =   12.55
       resnet18_int8  min =    7.77  max =    8.28  avg =    7.96
             alexnet  min =    8.89  max =    9.38  avg =    9.07
               vgg16  min =   53.83  max =   56.74  avg =   54.85
          vgg16_int8  min =   37.73  max =   39.08  avg =   38.04
            resnet50  min =   31.36  max =   32.68  avg =   31.60
       resnet50_int8  min =   17.11  max =   18.15  avg =   17.52
      squeezenet_ssd  min =   11.28  max =   12.05  avg =   11.52
 squeezenet_ssd_int8  min =    8.99  max =    9.47  avg =    9.14
       mobilenet_ssd  min =   12.81  max =   13.46  avg =   12.92
  mobilenet_ssd_int8  min =    7.83  max =    8.23  avg =    7.89
      mobilenet_yolo  min =   30.17  max =   31.36  avg =   30.34
  mobilenetv2_yolov3  min =   16.71  max =   17.32  avg =   16.79
         yolov4-tiny  min =   23.81  max =   24.99  avg =   24.07
           nanodet_m  min =    7.41  max =    8.34  avg =    7.51
    yolo-fastest-1.1  min =    3.55  max =    3.61  avg =    3.57
      yolo-fastestv2  min =    3.51  max =    3.64  avg =    3.56
  vision_transformer  min =  177.35  max =  185.49  avg =  178.18
          FastestDet  min =    3.51  max =    3.56  avg =    3.53
misaki@HimiMisakiBenchmarkAMD64:~/Workspace/ncnn/build/benchmark$ ./benchncnn 512 4 0 -1 0
loop_count = 512
num_threads = 4
powersave = 0
gpu_device = -1
cooling_down = 0
          squeezenet  min =    2.69  max =    2.82  avg =    2.71
     squeezenet_int8  min =    2.48  max =    2.65  avg =    2.54
           mobilenet  min =    3.55  max =    3.72  avg =    3.58
      mobilenet_int8  min =    2.55  max =    2.79  avg =    2.63
        mobilenet_v2  min =    3.43  max =    4.53  avg =    3.46
        mobilenet_v3  min =    3.15  max =    3.25  avg =    3.18
          shufflenet  min =    3.18  max =    3.33  avg =    3.22
       shufflenet_v2  min =    2.55  max =    2.68  avg =    2.59
             mnasnet  min =    3.31  max =    3.38  avg =    3.34
     proxylessnasnet  min =    3.65  max =    3.79  avg =    3.67
     efficientnet_b0  min =    6.03  max =    7.18  avg =    6.07
   efficientnetv2_b0  min =    6.77  max =    7.10  avg =    6.84
        regnety_400m  min =    7.30  max =    7.65  avg =    7.41
           blazeface  min =    0.89  max =    0.99  avg =    0.95
           googlenet  min =    9.32  max =   10.68  avg =    9.42
      googlenet_int8  min =    6.27  max =    6.53  avg =    6.32
            resnet18  min =    6.93  max =    7.70  avg =    7.06
       resnet18_int8  min =    4.16  max =    4.42  avg =    4.28
             alexnet  min =    4.78  max =    5.13  avg =    4.92
               vgg16  min =   30.20  max =   31.60  avg =   30.64
          vgg16_int8  min =   21.71  max =   22.91  avg =   22.04
            resnet50  min =   17.74  max =   18.49  avg =   17.92
       resnet50_int8  min =   10.23  max =   10.67  avg =   10.34
      squeezenet_ssd  min =    7.60  max =    8.20  avg =    7.77
 squeezenet_ssd_int8  min =    6.29  max =    7.40  avg =    6.39
       mobilenet_ssd  min =    7.37  max =    7.59  avg =    7.44
  mobilenet_ssd_int8  min =    4.80  max =    5.04  avg =    4.84
      mobilenet_yolo  min =   18.93  max =   19.98  avg =   19.12
  mobilenetv2_yolov3  min =   10.72  max =   11.16  avg =   10.79
         yolov4-tiny  min =   15.47  max =   16.38  avg =   15.77
           nanodet_m  min =    5.81  max =    5.99  avg =    5.85
    yolo-fastest-1.1  min =    3.27  max =    3.38  avg =    3.32
      yolo-fastestv2  min =    3.13  max =    3.33  avg =    3.17
  vision_transformer  min =   94.34  max =   99.51  avg =   94.77
          FastestDet  min =    3.13  max =    3.28  avg =    3.17
misaki@HimiMisakiBenchmarkAMD64:~/Workspace/ncnn/build/benchmark$ ./benchncnn 512 8 0 -1 0
loop_count = 512
num_threads = 8
powersave = 0
gpu_device = -1
cooling_down = 0
          squeezenet  min =    2.19  max =    2.34  avg =    2.22
     squeezenet_int8  min =    2.16  max =    2.24  avg =    2.20
           mobilenet  min =    2.40  max =    2.57  avg =    2.44
      mobilenet_int8  min =    1.67  max =    1.74  avg =    1.70
        mobilenet_v2  min =    2.89  max =    2.98  avg =    2.93
        mobilenet_v3  min =    2.71  max =    2.83  avg =    2.75
          shufflenet  min =    3.21  max =    3.36  avg =    3.26
       shufflenet_v2  min =    2.31  max =    2.41  avg =    2.35
             mnasnet  min =    2.69  max =    2.84  avg =    2.73
     proxylessnasnet  min =    2.94  max =    3.11  avg =    2.99
     efficientnet_b0  min =    4.77  max =    4.90  avg =    4.82
   efficientnetv2_b0  min =    5.33  max =    5.62  avg =    5.42
        regnety_400m  min =    7.18  max =    7.49  avg =    7.33
           blazeface  min =    0.98  max =    1.07  avg =    1.02
           googlenet  min =    6.82  max =    7.08  avg =    6.91
      googlenet_int8  min =    4.98  max =    5.23  avg =    5.05
            resnet18  min =    4.63  max =    4.79  avg =    4.71
       resnet18_int8  min =    2.95  max =    3.22  avg =    3.05
             alexnet  min =    2.93  max =    3.06  avg =    2.98
               vgg16  min =   17.60  max =   18.43  avg =   17.77
          vgg16_int8  min =   12.29  max =   12.75  avg =   12.37
            resnet50  min =   10.98  max =   11.53  avg =   11.10
       resnet50_int8  min =    6.76  max =    7.16  avg =    6.85
      squeezenet_ssd  min =    6.18  max =    6.73  avg =    6.39
 squeezenet_ssd_int8  min =    5.24  max =    5.47  avg =    5.34
       mobilenet_ssd  min =    4.96  max =    5.07  avg =    5.01
  mobilenet_ssd_int8  min =    3.42  max =    3.65  avg =    3.48
      mobilenet_yolo  min =   14.16  max =   14.89  avg =   14.46
  mobilenetv2_yolov3  min =    8.26  max =    8.70  avg =    8.32
         yolov4-tiny  min =   11.31  max =   11.92  avg =   11.48
           nanodet_m  min =    5.19  max =    5.35  avg =    5.25
    yolo-fastest-1.1  min =    3.30  max =    3.47  avg =    3.35
      yolo-fastestv2  min =    3.13  max =    3.26  avg =    3.18
  vision_transformer  min =   53.74  max =   56.87  avg =   54.04
          FastestDet  min =    3.11  max =    3.23  avg =    3.17
misaki@HimiMisakiBenchmarkAMD64:~/Workspace/ncnn/build/benchmark$ ./benchncnn 512 16 0 -1 0
loop_count = 512
num_threads = 16
powersave = 0
gpu_device = -1
cooling_down = 0
          squeezenet  min =    2.20  max =    2.31  avg =    2.24
     squeezenet_int8  min =    2.27  max =    2.38  avg =    2.32
           mobilenet  min =    2.09  max =    2.26  avg =    2.14
      mobilenet_int8  min =    1.53  max =    1.62  avg =    1.57
        mobilenet_v2  min =    2.85  max =    3.04  avg =    2.90
        mobilenet_v3  min =    2.74  max =    2.88  avg =    2.80
          shufflenet  min =    3.52  max =    4.89  avg =    3.59
       shufflenet_v2  min =    2.45  max =    2.57  avg =    2.51
             mnasnet  min =    2.62  max =    2.77  avg =    2.66
     proxylessnasnet  min =    2.83  max =    2.99  avg =    2.89
     efficientnet_b0  min =    4.19  max =    4.46  avg =    4.26
   efficientnetv2_b0  min =    5.16  max =    5.51  avg =    5.26
        regnety_400m  min =    7.83  max =    9.62  avg =    8.02
           blazeface  min =    1.12  max =    1.26  avg =    1.17
           googlenet  min =    6.33  max =    6.74  avg =    6.44
      googlenet_int8  min =    4.78  max =    5.31  avg =    4.86
            resnet18  min =    3.78  max =    3.94  avg =    3.83
       resnet18_int8  min =    2.87  max =    3.04  avg =    2.93
             alexnet  min =    2.10  max =    2.27  avg =    2.14
               vgg16  min =   13.16  max =   13.64  avg =   13.37
          vgg16_int8  min =    9.61  max =   10.20  avg =    9.72
            resnet50  min =    8.60  max =    8.86  avg =    8.68
       resnet50_int8  min =    5.97  max =    6.32  avg =    6.15
      squeezenet_ssd  min =    5.81  max =    6.19  avg =    6.00
 squeezenet_ssd_int8  min =    5.37  max =    6.09  avg =    5.46
       mobilenet_ssd  min =    4.29  max =    4.62  avg =    4.37
  mobilenet_ssd_int8  min =    3.19  max =    3.41  avg =    3.26
      mobilenet_yolo  min =   13.34  max =   14.07  avg =   13.73
  mobilenetv2_yolov3  min =    7.59  max =    7.89  avg =    7.69
         yolov4-tiny  min =   10.11  max =   10.79  avg =   10.37
           nanodet_m  min =    5.37  max =    5.61  avg =    5.44
    yolo-fastest-1.1  min =    3.53  max =    3.65  avg =    3.59
      yolo-fastestv2  min =    3.23  max =    3.39  avg =    3.31
  vision_transformer  min =   35.67  max =   36.48  avg =   35.93
          FastestDet  min =    3.27  max =    3.44  avg =    3.33
misaki@HimiMisakiBenchmarkAMD64:~/Workspace/ncnn/build/benchmark$ ./benchncnn 512 32 0 -1 0
loop_count = 512
num_threads = 32
powersave = 0
gpu_device = -1
cooling_down = 0
          squeezenet  min =    2.47  max =    2.78  avg =    2.52
     squeezenet_int8  min =    2.68  max =    2.84  avg =    2.74
           mobilenet  min =    2.31  max =    2.53  avg =    2.37
      mobilenet_int8  min =    1.71  max =    1.84  avg =    1.78
        mobilenet_v2  min =    3.31  max =    3.54  avg =    3.40
        mobilenet_v3  min =    3.38  max =    3.54  avg =    3.45
          shufflenet  min =    4.42  max =    4.62  avg =    4.53
       shufflenet_v2  min =    3.12  max =    3.27  avg =    3.21
             mnasnet  min =    3.08  max =    3.30  avg =    3.18
     proxylessnasnet  min =    3.35  max =    3.50  avg =    3.41
     efficientnet_b0  min =    4.78  max =    5.05  avg =    4.93
   efficientnetv2_b0  min =    6.19  max =    6.57  avg =    6.42
        regnety_400m  min =   11.23  max =   11.97  avg =   11.64
           blazeface  min =    1.40  max =    1.54  avg =    1.47
           googlenet  min =    6.85  max =    7.21  avg =    6.96
      googlenet_int8  min =    5.56  max =    5.77  avg =    5.66
            resnet18  min =    3.83  max =    4.44  avg =    3.93
       resnet18_int8  min =    3.17  max =    3.33  avg =    3.23
             alexnet  min =    2.06  max =    2.25  avg =    2.11
               vgg16  min =   12.12  max =   12.82  avg =   12.39
          vgg16_int8  min =    9.33  max =   10.70  avg =    9.45
            resnet50  min =    8.45  max =    8.79  avg =    8.55
       resnet50_int8  min =    6.26  max =    6.62  avg =    6.43
      squeezenet_ssd  min =    6.44  max =    6.74  avg =    6.57
 squeezenet_ssd_int8  min =    6.28  max =    6.65  avg =    6.42
       mobilenet_ssd  min =    4.62  max =    5.24  avg =    4.68
  mobilenet_ssd_int8  min =    3.69  max =    3.90  avg =    3.78
      mobilenet_yolo  min =   17.08  max =   18.83  avg =   18.16
  mobilenetv2_yolov3  min =    8.06  max =    8.31  avg =    8.16
         yolov4-tiny  min =   10.17  max =   10.60  avg =   10.39
           nanodet_m  min =    6.25  max =    6.56  avg =    6.40
    yolo-fastest-1.1  min =    4.16  max =    4.34  avg =    4.25
      yolo-fastestv2  min =    3.83  max =    4.04  avg =    3.92
  vision_transformer  min =   30.37  max =   33.12  avg =   30.94
          FastestDet  min =    3.85  max =    4.09  avg =    3.95
misaki@HimiMisakiBenchmarkAMD64:~/Workspace/ncnn/build/benchmark$ ./benchncnn 512 64 0 -1 0
loop_count = 512
num_threads = 64
powersave = 0
gpu_device = -1
cooling_down = 0
          squeezenet  min =    2.86  max =    4.39  avg =    2.92
     squeezenet_int8  min =    3.12  max =    3.42  avg =    3.20
           mobilenet  min =    2.57  max =    2.92  avg =    2.64
      mobilenet_int8  min =    2.11  max =    2.34  avg =    2.17
        mobilenet_v2  min =    3.77  max =    5.27  avg =    3.89
        mobilenet_v3  min =    3.88  max =    5.25  avg =    3.98
          shufflenet  min =    5.05  max =   13.10  avg =    5.23
       shufflenet_v2  min =    3.61  max =    5.79  avg =    3.70
             mnasnet  min =    3.58  max =    3.78  avg =    3.64
     proxylessnasnet  min =    3.85  max =    4.10  avg =    3.93
     efficientnet_b0  min =    5.57  max =   12.98  avg =    5.69
   efficientnetv2_b0  min =    7.09  max =   14.16  avg =    7.27
        regnety_400m  min =   13.09  max =   21.23  avg =   13.42
           blazeface  min =    1.64  max =    1.85  avg =    1.70
           googlenet  min =    7.39  max =    7.92  avg =    7.55
      googlenet_int8  min =    6.38  max =    8.56  avg =    6.46
            resnet18  min =    4.00  max =    5.19  avg =    4.11
       resnet18_int8  min =    3.63  max =    4.96  avg =    3.72
             alexnet  min =    2.15  max =    2.42  avg =    2.18
               vgg16  min =   13.49  max =   21.20  avg =   13.89
          vgg16_int8  min =   10.29  max =   18.64  avg =   10.48
            resnet50  min =    9.04  max =   14.31  avg =    9.18
       resnet50_int8  min =    7.24  max =   16.60  avg =    7.46
      squeezenet_ssd  min =    7.18  max =    8.72  avg =    7.28
 squeezenet_ssd_int8  min =    7.17  max =    8.81  avg =    7.31
       mobilenet_ssd  min =    4.97  max =    5.35  avg =    5.04
  mobilenet_ssd_int8  min =    4.39  max =   11.82  avg =    4.48
      mobilenet_yolo  min =   19.90  max =   23.57  avg =   20.68
  mobilenetv2_yolov3  min =    8.64  max =   12.98  avg =    8.88
         yolov4-tiny  min =   11.37  max =   13.51  avg =   11.57
           nanodet_m  min =    7.00  max =   14.01  avg =    7.09
    yolo-fastest-1.1  min =    4.73  max =   11.79  avg =    4.87
      yolo-fastestv2  min =    4.46  max =   11.84  avg =    4.54
  vision_transformer  min =   29.36  max =   36.71  avg =   29.64
          FastestDet  min =    4.29  max =    5.33  avg =    4.36
```
