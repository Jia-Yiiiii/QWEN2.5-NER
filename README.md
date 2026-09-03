# QWEN2.5-NER
四个步骤：
bc2gm--生物医学数据集
1.数据预处理，指令微调需要把NER标注，构成指令Promp格式
2.模型设计与训练流程，对应两种微调方案，Lora只训练注意力层的低秩分解矩阵，QLora在此基础上进一步压缩显存
3.模型评估和可视化
4.模型不同微调方式对比

重点：**loss mask：只对 assistant 的 token 计算 loss，user 部分 mask 掉不参与 loss**，这是 SFT 最核心的，参考Llama‑Factory做法，将user和assistant分开tokenize,labels 里 user 部分被置‑100,然后再拼接。
