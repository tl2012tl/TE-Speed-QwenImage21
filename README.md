# TE-Speed-QwenImage21  1.0

Qwen Image 2.1 ComfyUI专用推理加速节点。


## 1.0 

本插件使用输出预测策略作为核心实现。
- 默认 `reuse_threshold=0.06`，可在节点中调节速度与画质平衡,越大越快,目前已为测试最佳值。
- `step_cache=te_predictor` 为标准模式，最多连续预测 1 步。
- `step_cache=speed` 为速度模式，最多连续预测 2 步；连续预测会增加画质偏差风险。
- `speed` 会在标准模式上增加一次连续输出预测，实际加速取决于采样器、分辨率和阈值设置。


## 使用方式

工作流连接顺序：

`UNETLoader` → `QwenImage21Cache`（可选） → `TE-Speed Qwen Image 2.1` → `KSampler`


本插件不能替代 Qwen Image 2.1 的官方 Prefix KV Cache，也不建议直接把
标准模型改成极低采样步数；TE Predictor 的作用是保持原采样调度但减少用时。
