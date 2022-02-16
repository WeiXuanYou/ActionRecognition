# ActionRecognition

## Data Preparation
![](https://i.imgur.com/OgxuM9w.png)

### 0. Dependencies:
* CUDA (driver version > 400)
* OpenCV (with CUDA support): opencv3 | opencv4
* Boost
* HDF5 (Optional)

### 1. Extract Otical Flow Frame and RGB Frames from video:
**Step1 Installing Denseflow**

    
    $git clone https://github.com/open-mmlab/denseflow.git
    $cd denseflow && mkdir build && cd build
    $cmake -DCMAKE_INSTALL_PREFIX=$HOME/app -DUSE_HDF5=no -DUSE_NVFLOW=no ..
    $make -j(cpu_num)
    $make install

**Issue 1 : The GCC version and the CUDA version are incompatible**

You can use following command to change your gcc version
    
    $sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-version 100
    
**Step2 Generate Otical Flow Frames and RGB frames**

    $git clone https://github.com/open-mmlab/mmaction2.git
    $cd mmaction2/tools/data
    $python build_rawframes.py src_dir out_folder --task both --level 1 \ 
                               --num-worker 6 --flow-type tvl1 --out-format jpg 
                               --ext webm --num-gpu your_gpu_num
**Issue 1 : src_dir and out_folder are set but not found**

ou can download build_rawframes.py from this github respository and change the output_dir_path and my_src_dir_path in the file to your path

## Reference
**DenseFlow Install**
> https://github.com/open-mmlab/denseflow

**Extract optical flow and RGB frame tools**
> https://github.com/open-mmlab/mmaction2/blob/master/docs/data_preparation.md
> 
