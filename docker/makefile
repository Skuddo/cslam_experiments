ROBOT_ID=0

build-lidar:
	docker build -f Dockerfile.lidar . -t swarmslam

build-stereo:
	docker build -f Dockerfile.stereo . -t swarmslam

build-mono:
	docker build -f Dockerfile.mono . -t swarmslam

cpu_run:
	docker run -itd --rm --ipc host --net host --pid host --name swarmslam swarmslam

gpu_run:
	docker run -itd --gpus all -v /dev:/dev -e NVIDIA_DRIVER_CAPABILITIES=all --rm --ipc host --net host --pid host --name swarmslam swarmslam

agx_run:
	docker run -itd --runtime nvidia --gpus all -v /dev:/dev -e NVIDIA_DRIVER_CAPABILITIES=all --rm --ipc host --net host --pid host --name swarmslam swarmslam

start:
	docker start swarmslam

stop:
	docker stop swarmslam

kill:
	docker kill swarmslam

attach:
	docker exec -it swarmslam bash

swarmslam-lidar:
	docker exec -it swarmslam bash -c "source /opt/ros/humble/setup.bash; source Swarm-SLAM/install/setup.bash; ros2 launch cslam_experiments experiment_lidar.launch.py robot_id:=$(ROBOT_ID)"

swarmslam-stereo:
	docker exec -it swarmslam bash -c "source /opt/ros/humble/setup.bash; source Swarm-SLAM/install/setup.bash; ros2 launch cslam_experiments experiment_lidar.launch.py robot_id:=$(ROBOT_ID)"

swarmslam-mono:
	docker exec -it swarmslam bash -c "source /opt/ros/humble/setup.bash; source Swarm-SLAM/install/setup.bash; ros2 launch cslam_experiments experiment_lidar.launch.py robot_id:=$(ROBOT_ID)"
