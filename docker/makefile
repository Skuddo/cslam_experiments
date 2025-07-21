ROBOT_ID=0

build-lidar:
	docker build -f Dockerfile.lidar . -t swarmslam-lidar
# build-mono:
# 	docker build -f Dockerfile.mono . -t swarmslam-mono
build-stereo:
	docker build -f Dockerfile.stereo . -t swarmslam-stereo

cpu-run-lidar:
	docker run -itd --rm --ipc host --net host --pid host --name swarmslam-lidar swarmslam-lidar
# cpu-run-mono:
# 	docker run -itd --rm --ipc host --net host --pid host --name swarmslam-mono swarmslam-mono
cpu-run-stereo:
	docker run -itd --rm --ipc host --net host --pid host --name swarmslam-stereo swarmslam-stereo

gpu-run-lidar:
	docker run -itd --gpus all -v /dev:/dev -e NVIDIA_DRIVER_CAPABILITIES=all --rm --ipc host --net host --pid host --name swarmslam-lidar swarmslam-lidar
# gpu-run-mono:
# 	docker run -itd --gpus all -v /dev:/dev -e NVIDIA_DRIVER_CAPABILITIES=all --rm --ipc host --net host --pid host --name swarmslam-mono swarmslam-mono
gpu-run-stereo:
	docker run -itd --gpus all -v /dev:/dev -e NVIDIA_DRIVER_CAPABILITIES=all --rm --ipc host --net host --pid host --name swarmslam-stereo swarmslam-stereo

# agx_run:
# 	docker run -itd --runtime nvidia --gpus all -v /dev:/dev -e NVIDIA_DRIVER_CAPABILITIES=all --rm --ipc host --net host --pid host --name swarmslam swarmslam

start:
	docker start swarmslam
stop:
	docker stop swarmslam
kill:
	docker kill swarmslam

attach-lidar:
	docker exec -it swarmslam-lidar bash
# attach-mono:
# 	docker exec -it swarmslam-mono bash
attach-stereo:
	docker exec -it swarmslam-stereo bash

swarmslam-lidar:
	docker exec -it swarmslam-lidar bash -c "ros2 launch cslam_experiments experiment_lidar.launch.py robot_id:=$(ROBOT_ID)"
# swarmslam-mono:
# 	docker exec -it swarmslam-mono bash -c "ros2 launch cslam_experiments experiment_mono.launch.py robot_id:=$(ROBOT_ID)"
swarmslam-stereo:
	docker exec -it swarmslam-stereo bash -c "ros2 launch cslam_experiments kitti_stereo.launch.py robot_id:=$(ROBOT_ID)"
