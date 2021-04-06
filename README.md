# The F1TENTH Gym environment

This is a fork of the [F1TENTH Gym Repository](https://github.com/f1tenth/f1tenth_gym) designed to be as lightweight as possible.

## Prerequisites

### Required

* [Python](https://realpython.com/installing-python/)

### Recommended

* [Visual Studio Code](https://www.toolsqa.com/blogs/install-visual-studio-code/)
* [git](https://www.atlassian.com/git/tutorials/install-git)

## Quickstart

Clone this repository. If you don't want to use git, you may alternatively [download](https://github.com/davidnugent2425/f1tenth_gym/archive/main.zip) this repository as a zip file (you will then have to extract and rename the folder).

```bash
$ git clone https://github.com/davidnugent2425/f1tenth_gym.git
```

Go into the repository and install the required packages. If you don't want to use the command line to navigate to the repository, you may open the folder in Visual Studio Code or another code editor of your choice. Note: [pip](https://pypi.org/project/pip/) is a package manager for Python packages.

```
$ cd f1tenth_gym
$ pip install --user -e gym/
```

Then to make sure it's working, go into the src directory and run the simulator

```bash
cd src
py simulator.py
```

## Known issues (from original repo)
- On MacOS Big Sur and above, when rendering is turned on, you might encounter the error:
```
ImportError: Can't find framework /System/Library/Frameworks/OpenGL.framework.
```
You can fix the error by installing a newer version of pyglet:
```bash
$ pip3 install pyglet==1.5.11
```
And you might see an error similar to
```
gym 0.17.3 requires pyglet<=1.5.0,>=1.4.0, but you'll have pyglet 1.5.11 which is incompatible.
```
which could be ignored. The environment should still work without error.

## Citing
If you find this Gym environment useful, please consider citing:

```
@inproceedings{okelly2020f1tenth,
  title={F1TENTH: An Open-source Evaluation Environment for Continuous Control and Reinforcement Learning},
  author={O’Kelly, Matthew and Zheng, Hongrui and Karthik, Dhruv and Mangharam, Rahul},
  booktitle={NeurIPS 2019 Competition and Demonstration Track},
  pages={77--89},
  year={2020},
  organization={PMLR}
}
```
