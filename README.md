# TE-Speed-QwenImage21  1.0

Qwen Image 2.1 ComfyUI专用推理加速节点,提速30-40%。


## 1.0 

本插件使用输出预测策略作为核心实现。
- 默认 `reuse_threshold=0.06`，可在节点中调节速度与画质平衡,越大越快,目前已为测试最佳值。


## 使用方式

工作流连接顺序：

`UNETLoader` → `QwenImage21Cache`（可选） → `TE-Speed Qwen Image 2.1` → `KSampler`


本插件不能替代 Qwen Image 2.1 的官方 Prefix KV Cache，也不建议直接把
标准模型改成极低采样步数；TE Predictor 的作用是保持原采样调度但减少用时。
