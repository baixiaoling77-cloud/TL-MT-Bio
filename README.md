# 数字资源4.11 基于迁移学习的环境化学品生物蓄积性预测

**教学网页：<https://baixiaoling77-cloud.github.io/TL-MT-Bio/>**

本仓库 Fork 自 [Azukix/TL-MT-Bio](https://github.com/Azukix/TL-MT-Bio)，保留原项目的数据、代码、结果与提交历史，并增加书稿配套教学网页、资源索引、运行导读及二维码。原始研究与代码贡献归原作者所有。

## 资源入口

- [数据与划分](data/)
- [单任务 BCF 模型](RGCNBCF.py)、[BMF 模型](RGCNBMF.py)、[BAF 模型](RGCNBAF.py)
- [KOW 源任务预训练](RGCNKOW.py)
- [多任务模型](MT.py)、[迁移模型](TLMT.py)
- [模型性能结果](result/)
- [网页二维码 PNG](resource-4-11-qr.png)、[印刷用二维码 SVG](resource-4-11-qr.svg)

## 运行导读

```sh
git clone https://github.com/baixiaoling77-cloud/TL-MT-Bio.git
cd TL-MT-Bio
```

运行环境主要包括 PyTorch、DGL、RDKit、NumPy 和 pandas。根据计算设备选择相容的软件版本，并配置 Python 环境与 CUDA 支持。

建议按以下步骤开展学习与实践：

1. 整理分子结构与目标终点，保持 CSV、分子图缓存及数据划分文件的一致性。
2. 以 KOW 数据开展源任务预训练，学习分子结构的通用表征。
3. 配置预训练权重、网络结构、输入路径和任务参数，使源任务与目标任务之间的参数迁移相匹配。
4. 比较单任务、多任务与迁移学习策略。`TLMT.py` 采用冻结图网络层的迁移策略，训练目标任务相关参数。
5. 在一致的数据划分和评价尺度下比较独立测试结果，并结合多次运行的均值、标准差分析模型稳定性。

完成数据、运行环境与权重配置后的流程示例：

```sh
python RGCNKOW.py
python RGCNBCF.py
python MT.py
python TLMT.py
```

## 二维码与页面维护

二维码固定指向 `https://baixiaoling77-cloud.github.io/TL-MT-Bio/`。更新网页和配套资源时无需重印二维码；若重命名账号或仓库则应重新检查链接并生成新码。印刷建议宽度 30–35 mm，保持黑白和四周留白，优先使用 SVG，并在最终排版后实物扫码验证。

## 引文

Xiao et al., 2024。完整题录参见本书参考文献。
