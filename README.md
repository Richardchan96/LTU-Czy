## Training

1. To train our baseline model, please run the following command:

    ```bash
    th main.lua         # This model is not our final model!
    ```

    * Here are some optional arguments you can adjust. If you have any problem, please refer following lines. You can check out details in `NTIRE2017/code/opts.lua`.
        ```bash
        # You can train the model with multiple GPU. (Not multi-scale model.)
        -nGPU       [n]

        # Number of threads for data loading.
        -nThreads   [n]   

        # Please specify this directory. Default is /var/tmp/dataset
        -datadir    [$makeData]  

        # You can make an experiment folder with the name you want.
        -save       [Folder name]

        # You can resume your experiment from the last checkpoint.
        # Please do not set -save and -load at the same time.
        -load       [Folder name]     

        # png < t7 < t7pack - requires larger memory
        # png > t7 > t7pack - requires faster CPU & Storage
        -datatype   [png | t7 | t7pack]     

        # Please increase the splitBatch when you see 'out of memory' during training.
        # S should be the power of 2. (1, 2, 4, ...)
        -splitBatch [S]

        # Please reduce the chopSize when you see 'out of memory' during test.
        # The optimal size of S can be vary depend on your maximum GPU memory.
        -chopSize   [S]
        ```

2. To train our EDSR and MDSR, please use the `training.sh` in `NTIRE2017/code` directory. You have to uncomment the line you want to execute.

    ```bash
    cd $makeReposit/NTIRE2017/code
    sh training.sh
    ```

    <U>Some model may require pre-trained **bicubic scale 2** or **bicubic multiscale** model.</U> Here, we assume that you already downloaded `bicubic_x2.t7` and `bicubic_multiscale.t7` in the `NTIRE2017/demo/model` directory. Otherwise, you can create them yourself. It is also possible to start the traning from scratch by removing `-preTrained` option in `training.sh`.

<br>
