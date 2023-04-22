# tricks简介

## default_configs

包含不同任务在不同数据集上的默认配置（task_name_dataset_name.yaml，例如text_clf_smp2020_ewect_usual.yaml指在smp2020-ewect-usual数据集上的文本分类任务配置文件）

## center_controller

指定配置文件与trick_name（例如eight_bit、fgm），一键运行

## 如何运行

> 具体的对比实验可以`trick_name/readme.md`中查看，包括在不同数据集上添加策略前后的性能变化

```shell
python center_controller.py 
    --whole_model BertCLF 
    --trick_name fgm 
    --task_config default_configs/text_clf_smp2020_ewect_usual.yaml > tricks.text_classification.log 2>&1 &
```

## tricks

```angular2html
trick_name
   ├── __init__.py
   ├── README.md
   └── specialModels.py
```

* specialModels.py

  > trick的mini-pytorch-lightning实现

* README.md

  > 1. pytorch实现（伪代码）
  >2. trick对模型性能的影响
  > 2. 参考资料

## 竞赛策略

> 本项目涉及且已实现的竞赛策略

|    Trick     |    Target    |             Description              | Text CLF | ToDo |
| :----------: | :----------: | :----------------------------------: | :------: | :--: |
|  eight-bit   |   加速训练   |   8bit，降低显存开销，加快训练速度   |    √     |      |
|     fgm      |  增强鲁棒性  |    对抗训练，在embedding上加扰动     |    √     |      |
| unsup simcse | 增强语义理解 | 对比学习，额外增加一个对正负例的损失 |    √     |      |
