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
misaki@HimiMisakiBenchmarkARM64:~/Workspace/ncnn/build/benchmark$ ./benchncnn 512 1 0 -1 0
loop_count = 512
num_threads = 1
powersave = 0
gpu_device = -1
cooling_down = 0
          squeezenet  min =    6.39  max =    6.47  avg =    6.41
     squeezenet_int8  min =    4.69  max =    4.77  avg =    4.71
           mobilenet  min =   11.58  max =   11.67  avg =   11.60
      mobilenet_int8  min =    6.33  max =    6.41  avg =    6.35
        mobilenet_v2  min =    7.29  max =    7.38  avg =    7.31
        mobilenet_v3  min =    6.03  max =    6.11  avg =    6.05
          shufflenet  min =    4.13  max =    4.19  avg =    4.15
       shufflenet_v2  min =    4.19  max =    4.22  avg =    4.20
             mnasnet  min =    7.18  max =    7.28  avg =    7.20
     proxylessnasnet  min =    8.58  max =    8.89  avg =    8.66
     efficientnet_b0  min =   14.03  max =   14.45  avg =   14.25
   efficientnetv2_b0  min =   16.07  max =   16.67  avg =   16.47
        regnety_400m  min =    9.79  max =   10.33  avg =   10.03
           blazeface  min =    1.51  max =    1.57  avg =    1.53
           googlenet  min =   25.70  max =   26.45  avg =   25.96
      googlenet_int8  min =   18.80  max =   19.49  avg =   19.16
            resnet18  min =   17.45  max =   18.33  avg =   17.91
       resnet18_int8  min =   13.69  max =   14.21  avg =   13.96
             alexnet  min =   18.27  max =   19.47  avg =   19.10
               vgg16  min =   98.73  max =  101.91  avg =  100.58
          vgg16_int8  min =  101.59  max =  105.64  avg =  103.66
            resnet50  min =   53.92  max =   55.47  avg =   54.74
       resnet50_int8  min =   30.40  max =   30.96  avg =   30.65
      squeezenet_ssd  min =   16.09  max =   16.64  avg =   16.31
 squeezenet_ssd_int8  min =   13.32  max =   13.91  avg =   13.66
       mobilenet_ssd  min =   24.45  max =   24.95  avg =   24.67
  mobilenet_ssd_int8  min =   13.34  max =   13.88  avg =   13.56
      mobilenet_yolo  min =   55.07  max =   56.16  avg =   55.47
  mobilenetv2_yolov3  min =   27.47  max =   28.03  avg =   27.72
         yolov4-tiny  min =   34.41  max =   35.77  avg =   34.80
           nanodet_m  min =   10.18  max =   10.49  avg =   10.24
    yolo-fastest-1.1  min =    4.17  max =    4.26  avg =    4.18
      yolo-fastestv2  min =    3.48  max =    3.56  avg =    3.50
  vision_transformer  min =  793.71  max =  800.32  avg =  796.59
          FastestDet  min =    3.62  max =    3.76  avg =    3.65
misaki@HimiMisakiBenchmarkARM64:~/Workspace/ncnn/build/benchmark$ ./benchncnn 512 2 0 -1 0
loop_count = 512
num_threads = 2
powersave = 0
gpu_device = -1
cooling_down = 0
          squeezenet  min =    3.54  max =    3.72  avg =    3.59
     squeezenet_int8  min =    2.71  max =    2.83  avg =    2.76
           mobilenet  min =    6.06  max =    6.28  avg =    6.15
      mobilenet_int8  min =    3.44  max =    3.60  avg =    3.50
        mobilenet_v2  min =    4.08  max =    4.30  avg =    4.16
        mobilenet_v3  min =    3.47  max =    3.69  avg =    3.54
          shufflenet  min =    2.74  max =    2.85  avg =    2.79
       shufflenet_v2  min =    2.61  max =    2.92  avg =    2.65
             mnasnet  min =    4.09  max =    4.29  avg =    4.17
     proxylessnasnet  min =    4.77  max =    4.97  avg =    4.84
     efficientnet_b0  min =    7.75  max =    8.01  avg =    7.85
   efficientnetv2_b0  min =    8.95  max =    9.22  avg =    9.05
        regnety_400m  min =    6.77  max =    7.23  avg =    7.02
           blazeface  min =    1.00  max =    1.22  avg =    1.01
           googlenet  min =   13.25  max =   14.07  avg =   13.62
      googlenet_int8  min =   10.35  max =   10.60  avg =   10.43
            resnet18  min =    8.78  max =    9.35  avg =    8.89
       resnet18_int8  min =    7.03  max =    7.25  avg =    7.09
             alexnet  min =    8.98  max =    9.64  avg =    9.22
               vgg16  min =   50.37  max =   51.34  avg =   50.73
          vgg16_int8  min =   52.02  max =   56.48  avg =   52.99
            resnet50  min =   27.38  max =   28.07  avg =   27.68
       resnet50_int8  min =   15.05  max =   15.91  avg =   15.25
      squeezenet_ssd  min =    9.05  max =    9.53  avg =    9.23
 squeezenet_ssd_int8  min =    7.91  max =    8.10  avg =    7.97
       mobilenet_ssd  min =   12.55  max =   12.80  avg =   12.61
  mobilenet_ssd_int8  min =    6.99  max =    7.27  avg =    7.04
      mobilenet_yolo  min =   29.69  max =   30.18  avg =   29.87
  mobilenetv2_yolov3  min =   15.63  max =   15.96  avg =   15.71
         yolov4-tiny  min =   19.00  max =   19.79  avg =   19.29
           nanodet_m  min =    6.35  max =    6.65  avg =    6.40
    yolo-fastest-1.1  min =    2.94  max =    3.07  avg =    2.97
      yolo-fastestv2  min =    2.51  max =    2.61  avg =    2.54
  vision_transformer  min =  424.01  max =  447.52  avg =  434.38
          FastestDet  min =    2.56  max =    2.71  avg =    2.59
misaki@HimiMisakiBenchmarkARM64:~/Workspace/ncnn/build/benchmark$ ./benchncnn 512 4 0 -1 0
loop_count = 512
num_threads = 4
powersave = 0
gpu_device = -1
cooling_down = 0
          squeezenet  min =    2.04  max =    2.46  avg =    2.07
     squeezenet_int8  min =    1.72  max =    1.81  avg =    1.74
           mobilenet  min =    3.11  max =    3.23  avg =    3.14
      mobilenet_int8  min =    1.92  max =    2.02  avg =    1.94
        mobilenet_v2  min =    2.31  max =    2.46  avg =    2.35
        mobilenet_v3  min =    2.15  max =    2.34  avg =    2.18
          shufflenet  min =    2.08  max =    2.29  avg =    2.11
       shufflenet_v2  min =    1.71  max =    1.96  avg =    1.73
             mnasnet  min =    2.43  max =    2.61  avg =    2.46
     proxylessnasnet  min =    2.72  max =    2.84  avg =    2.75
     efficientnet_b0  min =    4.29  max =    4.43  avg =    4.32
   efficientnetv2_b0  min =    5.17  max =    5.39  avg =    5.22
        regnety_400m  min =    5.22  max =    5.41  avg =    5.27
           blazeface  min =    0.75  max =    1.06  avg =    0.76
           googlenet  min =    7.14  max =    7.42  avg =    7.21
      googlenet_int8  min =    5.97  max =    6.23  avg =    6.06
            resnet18  min =    4.69  max =    4.95  avg =    4.78
       resnet18_int8  min =    3.97  max =    4.12  avg =    4.02
             alexnet  min =    4.67  max =    5.12  avg =    4.98
               vgg16  min =   25.81  max =   26.52  avg =   26.16
          vgg16_int8  min =   26.35  max =   27.23  avg =   26.72
            resnet50  min =   14.21  max =   14.82  avg =   14.47
       resnet50_int8  min =    8.33  max =    8.98  avg =    8.59
      squeezenet_ssd  min =    5.86  max =    6.29  avg =    6.03
 squeezenet_ssd_int8  min =    4.93  max =    5.29  avg =    5.02
       mobilenet_ssd  min =    6.81  max =    7.17  avg =    6.95
  mobilenet_ssd_int8  min =    4.04  max =    4.31  avg =    4.18
      mobilenet_yolo  min =   17.36  max =   17.67  avg =   17.49
  mobilenetv2_yolov3  min =    9.04  max =    9.34  avg =    9.12
         yolov4-tiny  min =   12.01  max =   12.36  avg =   12.16
           nanodet_m  min =    4.14  max =    4.28  avg =    4.18
    yolo-fastest-1.1  min =    2.33  max =    2.47  avg =    2.37
      yolo-fastestv2  min =    1.90  max =    2.03  avg =    1.93
  vision_transformer  min =  225.61  max =  241.58  avg =  233.70
          FastestDet  min =    1.88  max =    2.21  avg =    1.90
misaki@HimiMisakiBenchmarkARM64:~/Workspace/ncnn/build/benchmark$ ./benchncnn 512 8 0 -1 0
loop_count = 512
num_threads = 8
powersave = 0
gpu_device = -1
cooling_down = 0
          squeezenet  min =    1.40  max =    1.64  avg =    1.43
     squeezenet_int8  min =    1.33  max =    1.42  avg =    1.35
           mobilenet  min =    1.80  max =    1.91  avg =    1.83
      mobilenet_int8  min =    1.29  max =    1.37  avg =    1.32
        mobilenet_v2  min =    1.79  max =    1.98  avg =    1.83
        mobilenet_v3  min =    1.57  max =    1.74  avg =    1.60
          shufflenet  min =    1.79  max =    2.40  avg =    1.82
       shufflenet_v2  min =    1.33  max =    1.75  avg =    1.35
             mnasnet  min =    1.70  max =    1.97  avg =    1.72
     proxylessnasnet  min =    1.89  max =    2.01  avg =    1.91
     efficientnet_b0  min =    2.97  max =    3.13  avg =    3.01
   efficientnetv2_b0  min =    3.77  max =    3.92  avg =    3.83
        regnety_400m  min =    4.80  max =    4.95  avg =    4.85
           blazeface  min =    0.75  max =    0.94  avg =    0.76
           googlenet  min =    4.62  max =    4.85  avg =    4.70
      googlenet_int8  min =    4.08  max =    4.27  avg =    4.14
            resnet18  min =    2.62  max =    2.86  avg =    2.69
       resnet18_int8  min =    2.38  max =    2.60  avg =    2.44
             alexnet  min =    2.64  max =    2.90  avg =    2.77
               vgg16  min =   13.77  max =   14.28  avg =   14.05
          vgg16_int8  min =   13.76  max =   14.31  avg =   14.02
            resnet50  min =    7.94  max =    8.27  avg =    8.09
       resnet50_int8  min =    5.11  max =    5.58  avg =    5.27
      squeezenet_ssd  min =    4.38  max =    4.74  avg =    4.51
 squeezenet_ssd_int8  min =    3.79  max =    4.08  avg =    3.85
       mobilenet_ssd  min =    4.23  max =    4.33  avg =    4.27
  mobilenet_ssd_int8  min =    2.86  max =    2.99  avg =    2.92
      mobilenet_yolo  min =   11.38  max =   11.78  avg =   11.60
  mobilenetv2_yolov3  min =    6.80  max =    7.22  avg =    6.96
         yolov4-tiny  min =    8.72  max =    9.03  avg =    8.80
           nanodet_m  min =    3.36  max =    3.58  avg =    3.43
    yolo-fastest-1.1  min =    2.23  max =    2.48  avg =    2.26
      yolo-fastestv2  min =    1.82  max =    1.99  avg =    1.84
  vision_transformer  min =  124.81  max =  133.32  avg =  129.22
          FastestDet  min =    1.77  max =    2.12  avg =    1.80
misaki@HimiMisakiBenchmarkARM64:~/Workspace/ncnn/build/benchmark$ ./benchncnn 512 16 0 -1 0
loop_count = 512
num_threads = 16
powersave = 0
gpu_device = -1
cooling_down = 0
          squeezenet  min =    1.27  max =    1.51  avg =    1.29
     squeezenet_int8  min =    1.33  max =    1.42  avg =    1.36
           mobilenet  min =    1.23  max =    1.40  avg =    1.24
      mobilenet_int8  min =    1.11  max =    1.19  avg =    1.13
        mobilenet_v2  min =    1.63  max =    1.84  avg =    1.66
        mobilenet_v3  min =    1.39  max =    1.77  avg =    1.43
          shufflenet  min =    1.88  max =    2.28  avg =    1.92
       shufflenet_v2  min =    1.36  max =    1.80  avg =    1.39
             mnasnet  min =    1.38  max =    1.65  avg =    1.42
     proxylessnasnet  min =    1.54  max =    1.85  avg =    1.57
     efficientnet_b0  min =    2.49  max =    2.85  avg =    2.53
   efficientnetv2_b0  min =    3.25  max =    3.59  avg =    3.35
        regnety_400m  min =    5.05  max =    5.34  avg =    5.12
           blazeface  min =    0.80  max =    0.88  avg =    0.81
           googlenet  min =    3.48  max =    3.68  avg =    3.52
      googlenet_int8  min =    3.40  max =    3.61  avg =    3.45
            resnet18  min =    1.93  max =    2.10  avg =    1.98
       resnet18_int8  min =    2.02  max =    2.13  avg =    2.05
             alexnet  min =    1.68  max =    1.84  avg =    1.77
               vgg16  min =    8.42  max =    8.63  avg =    8.50
          vgg16_int8  min =    8.23  max =    8.57  avg =    8.34
            resnet50  min =    5.10  max =    5.88  avg =    5.30
       resnet50_int8  min =    3.84  max =    4.04  avg =    3.91
      squeezenet_ssd  min =    4.20  max =    4.41  avg =    4.28
 squeezenet_ssd_int8  min =    3.51  max =    3.82  avg =    3.59
       mobilenet_ssd  min =    3.07  max =    3.37  avg =    3.18
  mobilenet_ssd_int8  min =    2.51  max =    2.75  avg =    2.57
      mobilenet_yolo  min =    9.64  max =   10.24  avg =    9.80
  mobilenetv2_yolov3  min =    5.51  max =    5.74  avg =    5.60
         yolov4-tiny  min =    7.65  max =    8.06  avg =    7.75
           nanodet_m  min =    3.01  max =    3.21  avg =    3.07
    yolo-fastest-1.1  min =    2.21  max =    2.44  avg =    2.26
      yolo-fastestv2  min =    1.90  max =    2.22  avg =    1.95
  vision_transformer  min =   73.19  max =   81.55  avg =   75.35
          FastestDet  min =    1.75  max =    2.00  avg =    1.78
misaki@HimiMisakiBenchmarkARM64:~/Workspace/ncnn/build/benchmark$ ./benchncnn 512 32 0 -1 0
loop_count = 512
num_threads = 32
powersave = 0
gpu_device = -1
cooling_down = 0
          squeezenet  min =    1.27  max =    1.38  avg =    1.29
     squeezenet_int8  min =    1.47  max =    1.56  avg =    1.50
           mobilenet  min =    1.09  max =    1.30  avg =    1.12
      mobilenet_int8  min =    1.16  max =    1.26  avg =    1.19
        mobilenet_v2  min =    1.65  max =    1.78  avg =    1.68
        mobilenet_v3  min =    1.57  max =    1.66  avg =    1.59
          shufflenet  min =    2.30  max =    2.42  avg =    2.34
       shufflenet_v2  min =    1.57  max =    1.68  avg =    1.60
             mnasnet  min =    1.50  max =    1.63  avg =    1.53
     proxylessnasnet  min =    1.69  max =    1.80  avg =    1.71
     efficientnet_b0  min =    2.52  max =    2.72  avg =    2.56
   efficientnetv2_b0  min =    3.67  max =    3.85  avg =    3.74
        regnety_400m  min =    6.96  max =    7.28  avg =    7.12
           blazeface  min =    1.04  max =    1.12  avg =    1.06
           googlenet  min =    3.49  max =    3.82  avg =    3.56
      googlenet_int8  min =    3.61  max =    3.93  avg =    3.68
            resnet18  min =    1.96  max =    2.20  avg =    2.00
       resnet18_int8  min =    2.20  max =    2.31  avg =    2.24
             alexnet  min =    1.62  max =    1.74  avg =    1.66
               vgg16  min =    6.69  max =    7.15  avg =    6.76
          vgg16_int8  min =    6.65  max =    7.07  avg =    6.74
            resnet50  min =    4.38  max =    4.61  avg =    4.45
       resnet50_int8  min =    3.81  max =    4.03  avg =    3.86
      squeezenet_ssd  min =    4.72  max =    5.11  avg =    4.83
 squeezenet_ssd_int8  min =    4.06  max =    4.29  avg =    4.11
       mobilenet_ssd  min =    3.05  max =    3.25  avg =    3.10
  mobilenet_ssd_int8  min =    2.80  max =    2.99  avg =    2.85
      mobilenet_yolo  min =   10.68  max =   11.15  avg =   10.83
  mobilenetv2_yolov3  min =    5.30  max =    5.60  avg =    5.38
         yolov4-tiny  min =    7.47  max =    7.76  avg =    7.55
           nanodet_m  min =    3.50  max =    3.69  avg =    3.56
    yolo-fastest-1.1  min =    2.60  max =    2.78  avg =    2.63
      yolo-fastestv2  min =    2.31  max =    2.44  avg =    2.35
  vision_transformer  min =   46.21  max =   49.20  avg =   47.48
          FastestDet  min =    2.16  max =    2.27  avg =    2.20
misaki@HimiMisakiBenchmarkARM64:~/Workspace/ncnn/build/benchmark$ ./benchncnn 512 64 0 -1 0
loop_count = 512
num_threads = 64
powersave = 0
gpu_device = -1
cooling_down = 0
          squeezenet  min =    1.52  max =    2.16  avg =    1.57
     squeezenet_int8  min =    1.79  max =   19.05  avg =    2.06
           mobilenet  min =    1.24  max =    2.50  avg =    1.29
      mobilenet_int8  min =    1.41  max =    1.90  avg =    1.45
        mobilenet_v2  min =    2.11  max =    2.90  avg =    2.21
        mobilenet_v3  min =    2.07  max =   29.34  avg =    2.24
          shufflenet  min =    3.08  max =   66.45  avg =    3.42
       shufflenet_v2  min =    2.11  max =    3.50  avg =    2.18
             mnasnet  min =    1.81  max =    2.20  avg =    1.85
     proxylessnasnet  min =    2.15  max =    2.87  avg =    2.23
     efficientnet_b0  min =    3.25  max =    4.02  avg =    3.34
   efficientnetv2_b0  min =    5.02  max =   23.60  avg =    5.33
        regnety_400m  min =   11.57  max =   75.67  avg =   12.69
           blazeface  min =    1.49  max =   11.01  avg =    1.56
           googlenet  min =    4.08  max =    4.78  avg =    4.18
      googlenet_int8  min =    4.58  max =    9.01  avg =    4.69
            resnet18  min =    2.32  max =   19.52  avg =    2.45
       resnet18_int8  min =    2.70  max =    3.12  avg =    2.79
             alexnet  min =    2.16  max =    4.41  avg =    2.25
               vgg16  min =    7.44  max =    9.87  avg =    7.60
          vgg16_int8  min =    7.86  max =   13.28  avg =    8.26
            resnet50  min =    4.98  max =    5.61  avg =    5.07
       resnet50_int8  min =    4.51  max =   18.84  avg =    4.64
      squeezenet_ssd  min =    6.33  max =   18.64  avg =    6.65
 squeezenet_ssd_int8  min =    5.22  max =   66.17  avg =    5.88
       mobilenet_ssd  min =    3.90  max =    4.42  avg =    4.02
  mobilenet_ssd_int8  min =    3.67  max =   37.05  avg =    4.08
      mobilenet_yolo  min =   17.69  max =   52.61  avg =   18.20
  mobilenetv2_yolov3  min =    6.26  max =   12.46  avg =    6.42
         yolov4-tiny  min =    9.02  max =   13.73  avg =    9.31
           nanodet_m  min =    4.21  max =    4.88  avg =    4.33
    yolo-fastest-1.1  min =    3.34  max =    3.74  avg =    3.42
      yolo-fastestv2  min =    3.23  max =   30.29  avg =    3.43
  vision_transformer  min =   48.63  max =   57.14  avg =   52.05
          FastestDet  min =    2.88  max =    3.50  avg =    2.95
```
