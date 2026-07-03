# PROJECT_MAP.md

项目路径：`D:\0630\work`

## Workflow 核心链路

- 主流程：`modules\orchestrator\engine.py`
- 状态/数据库字段：`modules\orchestrator\state.py`
- 路由入口：`server.py`、`modules\orchestrator\routes.py`
- 分镜生成：`modules\storyboard\generator.py`
- 分镜提示词：`modules\storyboard\prompts.py`
- 场景池：`modules\storyboard\scene_pool.py`
- 生图提示词：`modules\keyframe\extractor.py`
- 图片评分：`modules\scorer\scorer.py`
- 口播文案：`modules\orchestrator\engine.py` 内 `_generate_copy()`
- 历史/通用文案模块：`modules\wenan`
- 最终视频提示词：`modules\video_prompt\assembler.py`
- 视频生成提交：`modules\video_generation\client.py`
- 前端：`src`

## 定位规则

- 不改 `workflow_*.txt`，这些只是输出结果。
- 不用前端兜底后端生成问题。
- Workflow 内容问题优先查后端生成链路，不先查 `src`。
- 改代码后要验证，必须重启 `server.py` 后重新生成 workflow。
- 验证前确认 `server.py` 进程启动时间晚于相关代码文件修改时间。

## 常见问题定位

- `S101S101`、`盖盖盖`、污染词清洗：先查 `modules\orchestrator\engine.py`
- 原始参考资料大段进入最终提示词：先查 `modules\video_prompt\assembler.py`
- 分镜内容方向不对：先查 `modules\storyboard\prompts.py`
- 生图提示词产品外观不对：先查 `modules\keyframe\extractor.py`
- 口播文案卖点/合规/购买引导不对：先查 `modules\orchestrator\engine.py` 的 `_generate_copy()`
- 图片评分误判：先查 `modules\scorer\scorer.py`
- 视频任务提交参数不对：先查 `modules\video_generation\client.py`
