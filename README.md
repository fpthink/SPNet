## Superpoint Network for Point Cloud Oversegmentation  

by Le Hui, Jia Yuan, Mingmei Cheng, Jin Xie, Xiaoya Zhang, and Jian Yang



#####  This is a rough README.md, and we'll work through it. !!!



### Project Code

#### Requirements

* basic environment
    ```
    Python 3.6.6
    Pytorch 1.4.0
    CUDA 10.1
    ```

* compile the "libply_c" library (Please refer to [SPG](https://github.com/loicland/superpoint_graph))

  ```
  CONDAENV=YOUR_CONDA_ENVIRONMENT_LOCATION
  cd libs/ply_c
  cmake . -DPYTHON_LIBRARY=$CONDAENV/lib/libpython3.6m.so -DPYTHON_INCLUDE_DIR=$CONDAENV/include/python3.6m -DBOOST_INCLUDEDIR=$CONDAENV/include -DEIGEN3_INCLUDE_DIR=$CONDAENV/include/eigen3
  make
  cd ../../
  ```
  
* build the ops

  ```
  cd libs/pointops && python setup.py install && cd ../../
  
  Note that this may take a long time.
  ```


#### Training and Evaluation

* To train and evaluate SPNet, run the following command:

    ```
    # Train & Eval
    # Note that you should change the paths in the yaml file.
    
    sh tool/sh_train.sh s3dis 20220121 config/spnet.yaml
    
    sh tool/sh_test.sh s3dis 20220121 config/spnet.yaml 850
    ```


#### Citation

If you find the code or trained models useful, please consider citing:

```
@inproceedings{hui2021spnet,
  title={Superpoint Network for Point Cloud Oversegmentation},
  author={Hui, Le and Yuan, Jia and Cheng, Mingmei and Xie, Jin and Yang, Jian},
  booktitle={ICCV},
  year={2021}
}

```

#### Acknowledgement

Our code refers to [SPG](https://github.com/loicland/superpoint_graph) and [PointWeb](https://github.com/hszhao/PointWeb). Many thanks to SPG for a great work.