# This Fork has been moved [Here](https://github.com/FT-Autonomous/f1tenth-gym-quickstart)

Go to that repository for most recent version^

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
$ cd src
$ py simulator.py
```

## Making your own Driver

### Structure of a Driver

Let's take a look at the most basic Driver, which is in the file [starting_point.py](./src/starting_point.py)

```python
class SimpleDriver:    

    def process_lidar(self, ranges):
        speed = 5.0
        steering_angle = 0.0
        return speed, steering_angle
```

A Driver is just a class that has a ```process_lidar``` function which takes in LiDAR data and returns a speed to drive at along with a steering angle.

```ranges```: an array of 1080 distances (ranges) detected by the LiDAR scanner. As the LiDAR scanner takes readings for the full 360&deg;, the angle between each range is 2&pi;/1080 (in radians).

```steering_angle```: an angle in the range [-&pi;/2, &pi;/2], i.e. [-90&deg;, 90&deg;] in radians, with 0&deg; meaning straight ahead.

### Choosing a Driver

Let's look at the [simulator.py](./src/simulator.py) file. The section shown below is all we need to worry about.

```python
...
# import your drivers here
from follow_the_gap import GapFollower

# choose your driver here
driver = GapFollower()
...
```

As shown in the comments above, we can import Drivers and then choose which one we want to use. Let's import our SimpleDriver and choose it

```python
...
# import your drivers here
from follow_the_gap import GapFollower
from starting_point import SimpleDriver

# choose your driver here
driver = SimpleDriver()
...
```

Now if you run the simulator.py file again, it uses our SimpleDriver

```bash
$ py simulator.py
```

To see some more complex processing, take a look at the GapFollower Driver in [follow_the_gap.py](./src/follow_the_gap.py) which implements the [Follow The Gap Method](https://www.youtube.com/watch?v=7VLYP-z9hTw&ab_channel=Real-TimemLABUPenn)! Notice that it still has a ```process_lidar``` function which takes in LiDAR data and returns a speed and steering angle. That's all we'll ever need.

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
