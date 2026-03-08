# Generative Agents: Interactive Simulacra of Human Behavior

**作者：** Joon Sung Park, Joseph C. O'Brien, Carrie J. Cai, Meredith Ringel Morris, Percy Liang, Michael S. Bernstein
**来源：** ACM Symposium on User Interface Software and Technology (UIST '23)
**年份：** 2023
**Topics：** 2.3

## 摘要
生成代理是一种模拟可信人类行为的计算软件代理。该工作提出了一种架构，扩展了大型语言模型以使用自然语言存储代理体验的完整记录，随时间将这些记忆综合成更高级别的反思，并动态检索它们来规划行为。

## 主要贡献
- 提出了生成代理架构，扩展LLM以存储、综合和检索代理体验
- 创建了受The Sims启发的交互式沙盒环境，包含25个代理
- 代理产生可信的个体和涌现的社会行为（如自主传播聚会邀请、协调时间）
- 通过消融实验证明观察、规划和反思各组件对代理行为可信性的关键贡献

## 与我thesis的相关性
生成代理的观察-规划-反思三阶段架构为我的个性化代理设计提供了重要的结构参考。其使用自然语言存储体验的方法可以应用于我的egocentric life logging系统的记忆表示。

## 关键引用
> "We instantiate generative agents to populate an interactive sandbox environment inspired by The Sims, where end users can interact with a small town of twenty five agents using natural language."
> "By fusing large language models with computational, interactive agents, this work introduces architectural and interaction patterns for enabling believable simulations of human behavior."
