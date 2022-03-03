# hydrone Gym env
<img src="https://github.com/ROBOTIS-GIT/emanual/blob/master/assets/images/platform/hydrone/logo_hydrone.png" width="300">

This is a gym env to work with the hydrone gazebo simulations, allowing the use of [OpenAI Baselines](https://github.com/openai/baselines) and [Stable Baselines](https://github.com/hill-a/stable-baselines) deep reinforcement learning algorithms in the robot navigation training. See the `examples` folder to check some Python programs.

This project is a part of the development of some gazebo environments to apply deep-rl algorithms.

[Research Gazebo environments for hydrone robot](https://github.com/ITTcs/hydrone_simulations)

## Installation

```
git clone https://github.com/ITTcs/gym-hydrone
cd ITTcs/gym-hydrone
pip install -e .
```

This is an example using the OpenAI Baselines `DDPG` algorithm in a hydrone environment.

`.\examples\openai_baselines_ddpg.py`:

```python
import gym
import gym_hydrone
import rospy
import baselines.run as run
import os

env_name = 'hydrone_Circuit_Simple_Continuous-v0'
alg = 'ddpg'
num_timesteps = '1e4'

name_ref = env_name + '_' + num_timesteps + '_' + alg

my_args = [
    '--alg=' + alg,
    '--env=' + env_name,
    '--num_timesteps=' + num_timesteps]

os.environ["OPENAI_LOG_FORMAT"] = "csv"
os.environ["OPENAI_LOGDIR"] = './logs/' + name_ref

rospy.init_node(env_name.replace('-', '_'))

run.main(my_args)
```

Before running a Python program you first need run the specified environment. To the `hydrone_Circuit_Simple_Continuous-v0` env for example, would be:

```
roslaunch hydrone_gazebo hydrone_circuit_simple.launch
```

These resouces are part of a master's thesis where we use the Python [fuzzylab](https://github.com/ITTcs/fuzzylab) library to create fuzzy logic controllers with the implementation of deep reinforcement learning algorithms.

To cite this repository in publications:

    @misc{gymhydrone,
      author = {Avelar, Eduardo},
      title = {gym-hydrone},
      year = {2019},
      publisher = {GitHub},
      journal = {GitHub repository},
      howpublished = {\url{https://github.com/ITTcs/gym-hydrone}},
    }
# hydrone_gym
