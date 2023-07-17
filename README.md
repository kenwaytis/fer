## About The Project

A RESTful API server running in a Docker container that provides face expression services. CPU only.
The neural network model and inference code is derived from [Jiaxin-Ye/TIM-Net_SER](https://github.com/Jiaxin-Ye/TIM-Net_SER).

SER benchmark corpora from TIM-Net_SER paper Table 1.Evaluation measures are UAR(%) / WAR(%):

| Model   | CASIA         | EMODB         | EMOVO         | IEMOCAP       | RAVDESS       | SAVEE         |
| ------- | ------------- | ------------- | ------------- | ------------- | ------------- | ------------- |
| TIM-Net | 94.67 / 94.67 | 95.17 / 95.70 | 92.00 / 92.00 | 72.50 / 71.65 | 91.93 / 92.08 | 86.31 / 87.71 |

## Usage

### 1. Environmental requirements

Requires Docker engine or Docker Desktop.

All other dependencies and models are included in the pre-built Docker image, but of course you can build the exact same image from scratch based on the source code.

### 2. Installation

1. Clone the repo

```shell
git clone https://github.com/kenwaytis/fer.git
```

2. (opsition) Start the server with the default Docker Image

```shell
docker compose up
```

3. (opsition) Build the image from scratch

   3.1 Modify the docker-compose.yml file from

```
image: paidax/fer:cpu_0.3
```

​		to

```
image: namespace/fer:cpu_0.3
```

​		3.2 Start the server

```
docker compose up
```

### 3. API interface description

- Because fastAPI was used to build the server, you can view the automatically generated documentation instructions at **localhost:9000/docs**.

- Description:

**URL:**

localhost:9000/fer

**Request method:**

POST

**json description:**

| field name | required or not | type   | note                     |
| ---------- | --------------- | ------ | ------------------------ |
| image      | yes             | string | URL address of the image |

**Request json example:**

```json
{
  "image": "http://test.xxxx.jpg"
}
```

## Acknowledgments

**[TIM-Net_SER](https://github.com/Jiaxin-Ye/TIM-Net_SER)**

```
@inproceedings{TIMNET,
  title={Temporal Modeling Matters: A Novel Temporal Emotional Modeling Approach for Speech Emotion Recognition},
  author = {Ye, Jiaxin and Wen, Xincheng and Wei, Yujie and Xu, Yong and Liu, Kunhong and Shan, Hongming},
  booktitle = {ICASSP 2023-2023 IEEE International Conference on Acoustics, Speech and Signal Processing (ICASSP), Rhodes Island, Greece, June 4-10, 2023},
  pages={1--5},
  year = {2023}
}
```

