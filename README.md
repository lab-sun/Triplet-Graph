# <p align="center">Triplet-Graph: Global Metric Localization based on Semantic Triplet Graph for Autonomous Vehicles</p>


This is the code for Triplet-Graph. [[paper]](https://ieeexplore.ieee.org/abstract/document/10414178)


If you find TripletGraph helpful, please consider citing:
```bibtex
@ARTICLE{ma2024triplet,
  author={Ma, Weixin and Huang, Shoudong and Sun, Yuxiang},
  journal={IEEE Robotics and Automation Letters}, 
  title={Triplet-Graph: Global Metric Localization Based on Semantic Triplet Graph for Autonomous Vehicles}, 
  year={2024},
  volume={9},
  number={4},
  pages={3155-3162}}
```


# Install
## Operation System
Tested on Ubuntu 20.04

## Dependencies
* ROS
* Ceres
* yaml-cpp 

## Build
```text
mkdir -p ~/tripletgraph_ws/src
cd ~/tripletgraph_ws/src
git clone https://github.com/lab-sun/Triplet-Graph.git
cd ..
catkin_make
source devel/setup.bash
```
## Data preparation
* **Pair list**
  
We evaluate our method on **SeamnticKitti** dataset following paper SSC: Semantic Scan Context for Large-Scale Place Recognition.

* **LiDAR scans**

Please download LiDAR scans from the offical website of SemanticKitti dataset. Sequence-00, 02, 05, 06, 07, and 08 are used.

* **Semantic label**
  
We use semantic label from SemanticKitti and RangeNet++. 

For your convenience, you can download all required data [here](https://drive.google.com/file/d/1_BmwHdPqelCiq7tuWky8qiTGhJ1i5ER2/view?usp=sharing) (onely seq-06 is available). Unzip `test_data.zip` to folder `src/Triplet-Graph`.

## Run
We provide three different `launch` files.

*Note that you should replace file paths as yours appropriately in `config_kitti.yaml`. 


* `tripletgraph_single_pair.launch` This launch file will only run TripletGraph on a single pair of LiDAR scan for the evaluated sequence with visualization using rviz. Please use the following command:
```text
roslaunch tripletgraph tripletgraph_single_pair.launch
```

* `tripletgraph_part_seq.launch` This launch file will run TripletGraph on part of pairs of LiDAR scans for the evaluated sequence with visualization using rviz. Please use the following command:
```text
roslaunch tripletgraph tripletgraph_part_seq.launch
```

* `tripletgraph_entire_seq.launch` This launch file will run TripletGraph on all pairs of LiDAR scans for the evaluated sequence without visualization(for acceleration). It will take some time to be finished. Once finished, you should be able to find results in `/your path/tripletgraph_ws/src/tripletgraph/results/`, including `score.txt`, `rte.txt`, and `rre.txt`.
```text
roslaunch tripletgraph tripletgraph_entire_seq.launch
```


## Evaluation
Based on results files (or you can download [raw data](https://drive.google.com/file/d/1p4qHxb7Et9dQ9k5rIngomVKqlAmFTogm/view?usp=sharing) for results reported in the paper), you can use `eval.py` to get the final results. Copy `eval.py` into the your result folder, and then run command `python3 eval.py`. `numpy`, `sklearn`, and `matplotlib` are required dependences for `eval.py`.

# Contact
If you have any questions, please contact:
* Weixin Ma [<weixin.ma@connect.polyu.hk>]
  
You are also very welcome to check my personal [Github](https://github.com/Weixin-Ma) for more frequent update.


# Support Material
Here are the support material [docs/appendix.pdf](docs/appendix.pdf), which investigates the effects of some important parameters in Triplet-Graph. 


