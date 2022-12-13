# Alpha Science AUV

This repository contains source codes for ALPHA Science AUV.

<img
  src="https://raw.githubusercontent.com/uri-ocean-robotics/alpha_auv/noetic-devel/docs/images/alpha_auv_cad.png"
  alt="ALPHA AUV - CAD Model"
  style="display: inline-block; margin: 0 auto; max-width: 600px">

## Directory Structure

`alpha_sci_auv`
Meta Package for ALPHA AUV.

`alpha_sci_bringup`
Launch files for firing up the vehicle and simulator.

`alpha_sci_config`
Configuration files for devices, vehicle controller, mission controller, and etc.

`alpha_sci_description`
URDF descriptions, 3D Mesh, and launch files for the ALPHA AUV.

`alpha_sci_stonefish`
Stonefish descriptions for ALPHA AUV.

`alpha_sci_viz`
Contains configuration for RViZ.

## Installation

### MVP Installation

Currently MVP packages should be build from the source.
Target platform must be Ubuntu 20.04 because of the dependencies.

Pull repository and other dependencies
```bash
git clone --single-branch --branch noetic-devel https://github.com/uri-ocean-robotics/mvp_msgs
git clone --single-branch --branch noetic-devel https://github.com/uri-ocean-robotics/mvp_control
git clone --single-branch --branch noetic-devel https://github.com/uri-ocean-robotics/mvp_mission
git clone --single-branch --branch noetic-devel https://github.com/uri-ocean-robotics/stonefish_mvp
```

### ALPHA AUV Simulation and Hardware Installation

Pull repository and other dependencies
```bash
git clone https://github.com/uri-ocean-robotics/alpha_auv
cd alpha_auv
git submodule update --init --recursive
```

Install pip and setup python3 as default
```bash
sudo apt install python3-pip
```

### Install Stonefish Simulator

Pull the stonefish simulator library repository in **somewhere other than ROS workspace**.
Follow the installation instuctions at the [Stonefish Readme](https://stonefish.readthedocs.io/en/latest/install.html).

```bash
git clone https://github.com/uri-ocean-robotics/stonefish
```

Install the dependencies

```bash
sudo apt install libglm-dev libsdl2-dev
```

Build the stonefish library and install it.

```bash
cd stonefish
mkdir build
cd build
cmake -DCMAKE_BUILD_TYPE=Release ..
make -j$(nproc)
sudo make install
```

### Install Dependencies

Install dependencies
```bash
rosdep install --from-paths src --ignore-src --rosdistro ${ROS_DISTRO} -y
```

### Test the installation
To run the simulation
```bash
roslaunch alpha_sci_bringup bringup_simulation.launch
```

## Quick Start

Run the simulation and MVP Helm

```bash
roslaunch alpha_sci_bringup bringup_simulation.launch
```

Enable the controller
```bash
rosservice call /alpha/controller/enable
```

Start the local path tracking mission
```bash
rosservice call /alpha/helm/change_state "state: 'survey_local'"
```

## Citation

If you find this software useful in your research, please cite:

> Note, this work is published in OCEANS 2022 conference. Once the paper is publicly available, bibtex entry
will be updated with the one from IEEExplore.

```
@inproceedings{
    ALPHA_PAPER,
    title = {Acrobatic Low-cost Portable Hybrid AUV (ALPHA): System Design and Preliminary Results},
    author={Zhou, Mingxi and Gezer, Emir Cem and McConnell, William and Yuan, Chengzhi},
    booktitle={OCEANS 2022: Hampton Roads},
    year={2022},
    organization={IEEE}
}
```

## Funding
This work is supported by the [National Science Foundation](https://www.nsf.gov/) award [#2154901](https://www.nsf.gov/awardsearch/showAward?AWD_ID=2154901&HistoricalAwards=false)