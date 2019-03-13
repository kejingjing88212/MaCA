# MaCA
![](https://img.shields.io/badge/language-python-green.svg)
![](https://img.shields.io/badge/platform-linux-green.svg)
![](https://img.shields.io/badge/platform-mac-green.svg)
![](https://img.shields.io/badge/stability-experimental-green.svg)

Multi-agent Combat Arena (MaCA) is a heterogeneous multi-agent distributed decision and control technology reasearch platform produced by CETC-TFAI team. It focuses on the application of AI technologies e.g. reinforcement learning in multi-agent cooperation and confrontation

![](https://leonfg.github.io/maca/resource/maca.gif)

## System Requirements
- Linux 64-bit or Mac OS with Python 3.6
- numpy 1.14.2 or later
- pygame 1.9.3 or later

There is no limitation on agents' structure. You can write rule-based algorithms or use deep learning frameworks.
## Quick Start Guide
### Installation
```bash
pip install numpy pygame
git clone https://github.com/CETC-TFAI/MaCA.git
cd MaCA
export PYTHONPATH=$(pwd)/environment:$PYTHONPATH
```
### Run a combat between two agents
[fight.py](fight.py) can execute two agents. It uses two instances of a fixed-rule agent to fight each other by default.
```bash
python fight.py
```
You can specify agents and map by input arguments. In addition an agent should provide a call interface follows the MaCa platform specification.
### Replay
MaCa can record runtime log while playing and training. Use [replay.py](replay.py) to perform a replay.

First, run [fight.py](fight.py) and enable log record function
```bash
python fight.py --log
```
Then, run [replay.py](replay.py) to replay the log
```bash
python replay.py default_log
```
The log structure of MaCa is a set of .macalog files, they will save in path "log/log-name/".
When you run the [replay.py](replay.py), You must input a "log-name" as the parameter to specify which log you want to replay.
### Train
```bash
python train.py
```
MaCA provides an image based RL-API for deep reinforcement learning, but also a underlying data based RAW-API for other agent types e.g. fixed-rule agent development. Considering that different algorithms need different implementation methods and code structures, the training example can not be suitable for all algorithms. You can design your own algorithm and training script based on the two APIs.

