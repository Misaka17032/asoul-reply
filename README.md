# Asoul-reply

本项目使用来自b站评论区的30w条评论对微调[CPM](https://github.com/TsinghuaAI/CPM-1-Generate)的大模型，并且在此基础上蒸馏而成。

大模型效果：[b站视频](https://www.bilibili.com/video/BV1L44y1b7gE)

本项目是蒸馏后的模型，效果比源模型略低。

## 安装

首先安装pytorch等基础依赖，再安装[APEX](https://github.com/NVIDIA/apex#quick-start)以支持fp16：
```
pip install -r requirements.txt
git clone https://github.com/NVIDIA/apex
cd apex
pip install -v --no-cache-dir --global-option="--cpp_ext" --global-option="--cuda_ext" ./
```

或者使用智源提供的Docker容器。安装方式如下：
```
docker pull dmye/cpm:v0
```
参考运行指令如下：
```
sudo docker run --gpus '"device=0,1"' -it -v <path>:/CPM  --name=cpm  cpm:v0
```
其中`<path>`为代码所在目录，-v进行文件目录挂载

## 使用

下载好模型后放在项目根目录`models`文件夹中。

提供了命令行交互式生成：
```
bash scripts/generate_text.sh
```
运行该脚本需要两块GPU。