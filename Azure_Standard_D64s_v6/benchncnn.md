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
misaki@HimiMisakiBenchmarkIntel64:~/Workspace/ncnn/build/benchmark$ ./benchncnn 512 1 0 -1 0
loop_count = 512
num_threads = 1
powersave = 0
gpu_device = -1
cooling_down = 0
          squeezenet  min =    4.87  max =    5.13  avg =    4.89
     squeezenet_int8  min =    4.49  max =    4.57  avg =    4.52
           mobilenet  min =    7.91  max =    8.02  avg =    7.94
      mobilenet_int8  min =    7.04  max =    7.15  avg =    7.07
        mobilenet_v2  min =    6.31  max =    6.42  avg =    6.33
        mobilenet_v3  min =    4.96  max =    5.02  avg =    4.99
          shufflenet  min =    3.23  max =    3.32  avg =    3.26
       shufflenet_v2  min =    3.33  max =    3.40  avg =    3.36
             mnasnet  min =    5.85  max =    5.97  avg =    5.87
     proxylessnasnet  min =    6.59  max =    6.70  avg =    6.62
     efficientnet_b0  min =    9.42  max =   11.31  avg =    9.46
   efficientnetv2_b0  min =   10.40  max =   10.56  avg =   10.45
        regnety_400m  min =    7.91  max =   10.56  avg =    7.95
           blazeface  min =    1.07  max =    1.12  avg =    1.08
           googlenet  min =   17.27  max =   17.59  avg =   17.34
      googlenet_int8  min =   12.27  max =   12.47  avg =   12.34
            resnet18  min =   14.53  max =   15.05  avg =   14.58
       resnet18_int8  min =    9.80  max =   10.22  avg =    9.90
             alexnet  min =   11.49  max =   12.46  avg =   11.64
               vgg16  min =  102.94  max =  109.09  avg =  104.08
          vgg16_int8  min =   78.74  max =   83.18  avg =   79.86
            resnet50  min =   38.27  max =   42.39  avg =   39.06
       resnet50_int8  min =   23.34  max =   24.53  avg =   23.52
      squeezenet_ssd  min =   13.16  max =   13.29  avg =   13.19
 squeezenet_ssd_int8  min =   12.25  max =   12.34  avg =   12.27
       mobilenet_ssd  min =   16.45  max =   16.56  avg =   16.48
  mobilenet_ssd_int8  min =   13.86  max =   15.55  avg =   13.92
      mobilenet_yolo  min =   37.41  max =   37.80  avg =   37.59
  mobilenetv2_yolov3  min =   22.35  max =   22.53  avg =   22.42
         yolov4-tiny  min =   29.03  max =   31.28  avg =   29.24
           nanodet_m  min =    8.50  max =    8.63  avg =    8.54
    yolo-fastest-1.1  min =    3.82  max =    3.88  avg =    3.85
      yolo-fastestv2  min =    3.72  max =    3.81  avg =    3.74
  vision_transformer  min =  663.72  max =  670.45  avg =  665.62
          FastestDet  min =    3.72  max =    4.68  avg =    3.75
misaki@HimiMisakiBenchmarkIntel64:~/Workspace/ncnn/build/benchmark$ ./benchncnn 512 2 0 -1 0
loop_count = 512
num_threads = 2
powersave = 0
gpu_device = -1
cooling_down = 0
          squeezenet  min =    3.26  max =    3.49  avg =    3.31
     squeezenet_int8  min =    2.90  max =    4.09  avg =    2.94
           mobilenet  min =    4.47  max =    4.56  avg =    4.50
      mobilenet_int8  min =    3.84  max =    3.94  avg =    3.88
        mobilenet_v2  min =    4.19  max =    4.30  avg =    4.24
        mobilenet_v3  min =    3.81  max =    3.92  avg =    3.87
          shufflenet  min =    3.42  max =    5.23  avg =    3.47
       shufflenet_v2  min =    2.87  max =    2.96  avg =    2.91
             mnasnet  min =    4.06  max =    4.20  avg =    4.10
     proxylessnasnet  min =    4.48  max =    4.59  avg =    4.53
     efficientnet_b0  min =    5.94  max =    7.13  avg =    6.02
   efficientnetv2_b0  min =    6.97  max =    8.24  avg =    7.05
        regnety_400m  min =    7.06  max =    8.03  avg =    7.12
           blazeface  min =    1.03  max =    1.11  avg =    1.06
           googlenet  min =   10.97  max =   11.28  avg =   11.07
      googlenet_int8  min =    7.52  max =    7.68  avg =    7.59
            resnet18  min =    8.32  max =    8.61  avg =    8.36
       resnet18_int8  min =    5.35  max =    5.50  avg =    5.39
             alexnet  min =    6.36  max =    6.62  avg =    6.41
               vgg16  min =   53.24  max =   56.32  avg =   53.93
          vgg16_int8  min =   41.55  max =   44.76  avg =   42.65
            resnet50  min =   21.58  max =   23.22  avg =   21.88
       resnet50_int8  min =   12.47  max =   13.24  avg =   12.57
      squeezenet_ssd  min =    8.84  max =    9.05  avg =    8.91
 squeezenet_ssd_int8  min =    7.75  max =    8.10  avg =    7.81
       mobilenet_ssd  min =    9.47  max =    9.58  avg =    9.52
  mobilenet_ssd_int8  min =    7.66  max =    7.84  avg =    7.73
      mobilenet_yolo  min =   21.73  max =   22.14  avg =   21.88
  mobilenetv2_yolov3  min =   14.36  max =   14.64  avg =   14.46
         yolov4-tiny  min =   18.95  max =   19.73  avg =   19.10
           nanodet_m  min =    6.87  max =    7.05  avg =    6.95
    yolo-fastest-1.1  min =    3.34  max =    3.44  avg =    3.39
      yolo-fastestv2  min =    3.53  max =    3.67  avg =    3.59
  vision_transformer  min =  337.14  max =  343.88  avg =  338.89
          FastestDet  min =    3.47  max =    3.72  avg =    3.54
misaki@HimiMisakiBenchmarkIntel64:~/Workspace/ncnn/build/benchmark$ ./benchncnn 512 4 0 -1 0
loop_count = 512
num_threads = 4
powersave = 0
gpu_device = -1
cooling_down = 0
          squeezenet  min =    2.43  max =    2.70  avg =    2.48
     squeezenet_int8  min =    2.16  max =    2.31  avg =    2.19
           mobilenet  min =    2.86  max =    2.99  avg =    2.90
      mobilenet_int8  min =    2.26  max =    2.32  avg =    2.29
        mobilenet_v2  min =    3.18  max =    3.29  avg =    3.24
        mobilenet_v3  min =    2.85  max =    2.99  avg =    2.90
          shufflenet  min =    2.75  max =    2.88  avg =    2.80
       shufflenet_v2  min =    2.41  max =    2.52  avg =    2.44
             mnasnet  min =    3.03  max =    3.17  avg =    3.07
     proxylessnasnet  min =    3.25  max =    3.38  avg =    3.29
     efficientnet_b0  min =    4.34  max =    4.44  avg =    4.37
   efficientnetv2_b0  min =    5.03  max =    5.21  avg =    5.11
        regnety_400m  min =    6.33  max =    8.40  avg =    6.37
           blazeface  min =    0.98  max =    1.07  avg =    1.01
           googlenet  min =    7.25  max =    7.59  avg =    7.35
      googlenet_int8  min =    4.94  max =    5.06  avg =    4.98
            resnet18  min =    4.75  max =    5.22  avg =    4.91
       resnet18_int8  min =    3.19  max =    6.17  avg =    3.25
             alexnet  min =    3.68  max =    3.87  avg =    3.74
               vgg16  min =   28.09  max =   29.17  avg =   28.40
          vgg16_int8  min =   21.59  max =   23.28  avg =   22.09
            resnet50  min =   12.96  max =   14.14  avg =   13.23
       resnet50_int8  min =    7.21  max =    7.45  avg =    7.29
      squeezenet_ssd  min =    6.41  max =    7.84  avg =    6.49
 squeezenet_ssd_int8  min =    5.56  max =    5.71  avg =    5.60
       mobilenet_ssd  min =    5.88  max =    6.01  avg =    5.93
  mobilenet_ssd_int8  min =    4.57  max =    4.84  avg =    4.61
      mobilenet_yolo  min =   14.46  max =   14.78  avg =   14.59
  mobilenetv2_yolov3  min =   10.34  max =   11.77  avg =   10.45
         yolov4-tiny  min =   13.64  max =   15.67  avg =   13.80
           nanodet_m  min =    5.71  max =    5.87  avg =    5.78
    yolo-fastest-1.1  min =    3.00  max =    3.15  avg =    3.05
      yolo-fastestv2  min =    3.08  max =    3.22  avg =    3.14
  vision_transformer  min =  174.31  max =  177.93  avg =  175.36
          FastestDet  min =    3.18  max =    3.31  avg =    3.23
misaki@HimiMisakiBenchmarkIntel64:~/Workspace/ncnn/build/benchmark$ ./benchncnn 512 8 0 -1 0
loop_count = 512
num_threads = 8
powersave = 0
gpu_device = -1
cooling_down = 0
          squeezenet  min =    2.25  max =    2.43  avg =    2.28
     squeezenet_int8  min =    2.08  max =    2.16  avg =    2.11
           mobilenet  min =    2.23  max =    2.37  avg =    2.28
      mobilenet_int8  min =    1.69  max =    1.75  avg =    1.71
        mobilenet_v2  min =    2.84  max =    2.93  avg =    2.88
        mobilenet_v3  min =    2.56  max =    6.93  avg =    2.61
          shufflenet  min =    2.77  max =    2.86  avg =    2.80
       shufflenet_v2  min =    2.39  max =    2.47  avg =    2.42
             mnasnet  min =    2.64  max =    2.75  avg =    2.68
     proxylessnasnet  min =    2.77  max =    2.88  avg =    2.82
     efficientnet_b0  min =    3.52  max =    3.64  avg =    3.56
   efficientnetv2_b0  min =    4.38  max =    4.52  avg =    4.44
        regnety_400m  min =    6.22  max =    9.01  avg =    6.26
           blazeface  min =    1.01  max =    1.07  avg =    1.03
           googlenet  min =    6.05  max =    6.37  avg =    6.14
      googlenet_int8  min =    4.33  max =    4.47  avg =    4.37
            resnet18  min =    3.66  max =    4.22  avg =    3.73
       resnet18_int8  min =    2.74  max =    2.88  avg =    2.79
             alexnet  min =    2.41  max =    2.66  avg =    2.46
               vgg16  min =   18.34  max =   19.57  avg =   18.77
          vgg16_int8  min =   13.51  max =   14.27  avg =   13.77
            resnet50  min =    8.97  max =    9.43  avg =    9.13
       resnet50_int8  min =    5.30  max =    5.52  avg =    5.36
      squeezenet_ssd  min =    5.68  max =    8.24  avg =    5.75
 squeezenet_ssd_int8  min =    5.08  max =    5.19  avg =    5.12
       mobilenet_ssd  min =    4.57  max =    4.87  avg =    4.64
  mobilenet_ssd_int8  min =    3.45  max =    3.56  avg =    3.49
      mobilenet_yolo  min =   11.58  max =   12.11  avg =   11.76
  mobilenetv2_yolov3  min =    8.80  max =    9.10  avg =    8.88
         yolov4-tiny  min =   12.09  max =   12.81  avg =   12.25
           nanodet_m  min =    5.54  max =    5.70  avg =    5.60
    yolo-fastest-1.1  min =    2.94  max =    3.05  avg =    2.97
      yolo-fastestv2  min =    3.05  max =    3.18  avg =    3.09
  vision_transformer  min =   92.37  max =   97.02  avg =   93.10
          FastestDet  min =    3.14  max =    3.27  avg =    3.19
misaki@HimiMisakiBenchmarkIntel64:~/Workspace/ncnn/build/benchmark$ ./benchncnn 512 16 0 -1 0
loop_count = 512
num_threads = 16
powersave = 0
gpu_device = -1
cooling_down = 0
          squeezenet  min =    2.24  max =    2.44  avg =    2.26
     squeezenet_int8  min =    2.17  max =    2.30  avg =    2.20
           mobilenet  min =    2.04  max =    2.15  avg =    2.08
      mobilenet_int8  min =    1.51  max =    3.09  avg =    1.53
        mobilenet_v2  min =    2.80  max =    2.90  avg =    2.83
        mobilenet_v3  min =    2.58  max =    2.69  avg =    2.62
          shufflenet  min =    3.03  max =    3.11  avg =    3.06
       shufflenet_v2  min =    2.56  max =    2.66  avg =    2.58
             mnasnet  min =    2.60  max =    2.68  avg =    2.63
     proxylessnasnet  min =    2.77  max =    2.84  avg =    2.80
     efficientnet_b0  min =    3.47  max =    5.14  avg =    3.52
   efficientnetv2_b0  min =    4.55  max =    4.72  avg =    4.61
        regnety_400m  min =    7.30  max =    7.49  avg =    7.37
           blazeface  min =    1.12  max =    1.18  avg =    1.14
           googlenet  min =    5.87  max =    8.36  avg =    5.94
      googlenet_int8  min =    4.33  max =    4.61  avg =    4.39
            resnet18  min =    3.46  max =    3.58  avg =    3.50
       resnet18_int8  min =    2.73  max =    2.84  avg =    2.77
             alexnet  min =    2.09  max =    2.36  avg =    2.14
               vgg16  min =   14.36  max =   15.26  avg =   14.69
          vgg16_int8  min =   10.53  max =   11.27  avg =   10.75
            resnet50  min =    7.96  max =    8.26  avg =    8.06
       resnet50_int8  min =    4.80  max =    4.97  avg =    4.85
      squeezenet_ssd  min =    5.93  max =    6.11  avg =    5.99
 squeezenet_ssd_int8  min =    5.33  max =    6.15  avg =    5.37
       mobilenet_ssd  min =    4.33  max =    4.61  avg =    4.41
  mobilenet_ssd_int8  min =    3.20  max =    3.29  avg =    3.25
      mobilenet_yolo  min =   12.23  max =   13.06  avg =   12.41
  mobilenetv2_yolov3  min =    8.27  max =    8.64  avg =    8.34
         yolov4-tiny  min =   11.84  max =   12.90  avg =   12.01
           nanodet_m  min =    5.91  max =    6.00  avg =    5.95
    yolo-fastest-1.1  min =    3.16  max =    3.24  avg =    3.20
      yolo-fastestv2  min =    3.31  max =    3.41  avg =    3.34
  vision_transformer  min =   52.39  max =   54.43  avg =   52.79
          FastestDet  min =    3.37  max =    3.48  avg =    3.41
misaki@HimiMisakiBenchmarkIntel64:~/Workspace/ncnn/build/benchmark$ ./benchncnn 512 32 0 -1 0
loop_count = 512
num_threads = 32
powersave = 0
gpu_device = -1
cooling_down = 0
          squeezenet  min =    2.39  max =    5.09  avg =    2.53
     squeezenet_int8  min =    2.41  max =    2.55  avg =    2.49
           mobilenet  min =    2.12  max =    2.35  avg =    2.25
      mobilenet_int8  min =    1.56  max =    1.67  avg =    1.62
        mobilenet_v2  min =    3.01  max =    3.26  avg =    3.16
        mobilenet_v3  min =    2.87  max =    3.08  avg =    3.01
          shufflenet  min =    3.52  max =    3.79  avg =    3.69
       shufflenet_v2  min =    2.90  max =    3.16  avg =    3.03
             mnasnet  min =    2.79  max =    3.02  avg =    2.93
     proxylessnasnet  min =    2.98  max =    3.21  avg =    3.14
     efficientnet_b0  min =    3.85  max =    4.15  avg =    4.05
   efficientnetv2_b0  min =    5.28  max =    5.56  avg =    5.45
        regnety_400m  min =    9.68  max =   10.41  avg =    9.81
           blazeface  min =    1.33  max =    1.45  avg =    1.39
           googlenet  min =    6.35  max =    6.72  avg =    6.58
      googlenet_int8  min =    4.98  max =    5.32  avg =    5.06
            resnet18  min =    3.69  max =    3.99  avg =    3.87
       resnet18_int8  min =    2.98  max =    3.20  avg =    3.12
             alexnet  min =    2.10  max =    2.43  avg =    2.25
               vgg16  min =   13.61  max =   14.70  avg =   14.07
          vgg16_int8  min =   10.00  max =   11.30  avg =   10.26
            resnet50  min =    8.25  max =    8.85  avg =    8.59
       resnet50_int8  min =    5.18  max =    5.45  avg =    5.34
      squeezenet_ssd  min =    6.52  max =    6.75  avg =    6.67
 squeezenet_ssd_int8  min =    6.00  max =    6.28  avg =    6.11
       mobilenet_ssd  min =    4.53  max =    4.96  avg =    4.73
  mobilenet_ssd_int8  min =    3.50  max =    3.67  avg =    3.57
      mobilenet_yolo  min =   14.89  max =   15.54  avg =   15.20
  mobilenetv2_yolov3  min =    8.48  max =    8.96  avg =    8.79
         yolov4-tiny  min =   12.17  max =   12.86  avg =   12.51
           nanodet_m  min =    6.65  max =    6.92  avg =    6.82
    yolo-fastest-1.1  min =    3.56  max =    3.76  avg =    3.68
      yolo-fastestv2  min =    3.72  max =    3.96  avg =    3.89
  vision_transformer  min =   33.45  max =   36.96  avg =   33.96
          FastestDet  min =    3.68  max =    3.93  avg =    3.86
misaki@HimiMisakiBenchmarkIntel64:~/Workspace/ncnn/build/benchmark$ ./benchncnn 512 64 0 -1 0
loop_count = 512
num_threads = 64
powersave = 0
gpu_device = -1
cooling_down = 0
          squeezenet  min =    2.54  max =    2.94  avg =    2.64
     squeezenet_int8  min =    2.74  max =    4.14  avg =    2.85
           mobilenet  min =    2.34  max =    2.76  avg =    2.48
      mobilenet_int8  min =    1.89  max =    2.03  avg =    1.95
        mobilenet_v2  min =    3.41  max =    3.84  avg =    3.54
        mobilenet_v3  min =    3.44  max =    4.46  avg =    3.56
          shufflenet  min =    4.12  max =   20.37  avg =    4.31
       shufflenet_v2  min =    3.10  max =    3.41  avg =    3.23
             mnasnet  min =    3.16  max =    4.36  avg =    3.31
     proxylessnasnet  min =    3.43  max =   14.49  avg =    3.62
     efficientnet_b0  min =    4.57  max =    4.98  avg =    4.75
   efficientnetv2_b0  min =    6.06  max =   14.27  avg =    6.26
        regnety_400m  min =   12.51  max =   14.28  avg =   12.79
           blazeface  min =    1.56  max =   21.66  avg =    1.67
           googlenet  min =    7.01  max =    9.07  avg =    7.21
      googlenet_int8  min =    5.89  max =    6.36  avg =    6.00
            resnet18  min =    3.96  max =    5.39  avg =    4.13
       resnet18_int8  min =    3.55  max =    4.86  avg =    3.70
             alexnet  min =    2.27  max =    2.59  avg =    2.37
               vgg16  min =   14.62  max =   24.01  avg =   14.94
          vgg16_int8  min =   10.77  max =   13.28  avg =   11.03
            resnet50  min =    8.47  max =   10.08  avg =    8.74
       resnet50_int8  min =    6.10  max =    7.23  avg =    6.23
      squeezenet_ssd  min =    6.85  max =    7.31  avg =    7.03
 squeezenet_ssd_int8  min =    6.81  max =    8.77  avg =    6.96
       mobilenet_ssd  min =    5.06  max =    6.41  avg =    5.24
  mobilenet_ssd_int8  min =    4.23  max =   17.91  avg =    4.42
      mobilenet_yolo  min =   18.58  max =   21.99  avg =   19.00
  mobilenetv2_yolov3  min =    9.18  max =   10.55  avg =    9.49
         yolov4-tiny  min =   13.10  max =   15.28  avg =   13.45
           nanodet_m  min =    6.81  max =    7.24  avg =    6.92
    yolo-fastest-1.1  min =    4.07  max =    5.13  avg =    4.22
      yolo-fastestv2  min =    4.14  max =   15.50  avg =    4.27
  vision_transformer  min =   28.11  max =   39.27  avg =   28.71
          FastestDet  min =    4.03  max =    5.15  avg =    4.19
```

## Results (Without AVX512)

```

```
