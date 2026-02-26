# 2026-02-10-009: LMEE - Long-term Memory Embodied Exploration

## 📄 论文基本信息

- **标题**: Explore with Long-term Memory: A Benchmark and Multimodal LLM-based Reinforcement Learning Framework for Embodied Exploration
- **作者**: Sen Wang 等
- **年份**: 2026
- **来源**: arXiv:2601.10744
- **版本**: v1 (2026-01-11)
- **PDF**: 5.6MB
- **代码**: https://wangsen99.github.io/papers/lmee/
- **领域**: AI, CV
- **链接**: https://arxiv.org/abs/2601.10744

## 🔍 核心贡献

### 问题
- 现有主流one-shot embodied任务只关注任务完成结果
- 忽略了探索过程和memory利用

### 解决方案
- **LMEE (Long-term Memory Embodied Exploration)**: 统一探索认知和决策行为
- **MemoryExplorer**: 通过RL fine-tune MLLM，鼓励active memory querying
- **LMEE-Bench**: 多目标导航 + memory-based QA评估

### 创新
- Multi-task reward function: action prediction + frontier selection + QA
- Proactive exploration通过memory recall

## 💡 与Thesis相关

1. **Lifelong Learning**: 直接匹配24/7 continuous recording
2. **Long-term Memory**: 适合daily life experience storage
3. **Embodied Exploration**: 理解环境和位置关系

**创建时间**: 2026-02-10
