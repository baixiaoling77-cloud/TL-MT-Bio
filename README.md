# 数字资源4.11 基于迁移学习的环境化学品生物蓄积性预测

**教学网页：<https://baixiaoling77-cloud.github.io/TL-MT-Bio/>**

本仓库 Fork 自 [Azukix/TL-MT-Bio](https://github.com/Azukix/TL-MT-Bio)，保留原项目的数据、代码、结果与提交历史，并增加书稿配套教学网页、资源索引、运行导读及二维码。原始研究与代码贡献归原作者所有。

## 资源入口

- [数据与划分](data/)
- [单任务 BCF 模型](RGCNBCF.py)、[BMF 模型](RGCNBMF.py)、[BAF 模型](RGCNBAF.py)
- [KOW 源任务预训练](RGCNKOW.py)
- [多任务模型](MT.py)、[迁移模型](TLMT.py)
- [已有性能结果](result/)
- [网页二维码 PNG](resource-4-11-qr.png)、[印刷用二维码 SVG](resource-4-11-qr.svg)

## 运行导读

```sh
git clone https://github.com/baixiaoling77-cloud/TL-MT-Bio.git
cd TL-MT-Bio
```

代码依赖 PyTorch、DGL、RDKit、NumPy、pandas 等，具体版本需与原代码及 CUDA 环境相容。此教学整理没有重新训练模型，也没有验证一套可直接安装的锁定环境。

运行前需逐项核对：

1. `data/KOWall3.csv` 当前表头为 `smiles,BCF,BAF,BMF,group`，GitHub 显示 2,845 行（含表头），未见 KOW 列。这不是书稿所述约 1.7 万条 KOW 源域数据；完整源数据需另行补齐。
2. 检查 `.bin`、`_group.csv` 与 CSV 的分子顺序、终点顺序和划分一致。不得仅凭文件名推断内容。
3. `TLMT.py` 预期权重名为 `KOW3-512512512_early_stop.pth`；`RGCNKOW.py` 当前任务名却为 `KOW3-512512256`。使用前必须核对路径、网络维度和权重相容性，不能直接顺序执行后假定能够运行。
4. 检查每个脚本的 `args`，补齐输入与权重后，按源任务预训练、单任务/多任务基线、迁移训练的顺序运行。`TLMT.py` 当前冻结图网络层，训练其余参数。
5. 比较同一终点时，应使用一致的数据划分与标签尺度。结果区分 training、valid 与 test；回归脚本使用 R²。多次运行应报告均值、标准差及随机种子。

准备完成后的流程示例：

```sh
python RGCNKOW.py
python RGCNBCF.py
python MT.py
python TLMT.py
```

## 二维码与页面维护

二维码固定指向 `https://baixiaoling77-cloud.github.io/TL-MT-Bio/`。更新网页和配套资源时无需重印二维码；若重命名账号或仓库则应重新检查链接并生成新码。印刷建议宽度 30–35 mm，保持黑白和四周留白，优先使用 SVG，并在最终排版后实物扫码验证。

## 引文

Xiao et al., 2024（沿用书稿引文；完整题录参见书稿参考文献）。
