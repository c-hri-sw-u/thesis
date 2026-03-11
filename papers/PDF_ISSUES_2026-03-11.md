# 论文PDF问题报告

**检查时间：** 2026-03-11 00:41 EDT

---

## 问题总结

用户报告 `[P]-006-marc-2024.pdf` 和 `[P]-043-soar-1987.pdf` 无法打开。

---

## 检查结果

### **006 MARC (Wu et al.)**

**文件状态：** ✅ PDF文件有效（508KB，9页）

**问题：** 论文标题在index中记录**错误**

- **Index记录（错误）：** MARC: Memory-Augmented Reinforcement Learning for Conversational Agents
- **实际论文（正确）：** MARC: Memory-Augmented RL Token Compression for Efficient Video Understanding
- **来源：** arXiv:2510.07915 (ICLR 2026)
- **作者：** Peiran Wu, Zhuorui Yu, Yunze Liu, Chi-Hao Wu, Enmin Zhou, Junxiao Shen

**已修复：**
- ✅ 更新了 `papers/index.md` 中的正确信息
- ✅ PDF文件本身是正常的，可以打开

**论文内容：**
- 视频token压缩（减少95% tokens，72% GPU memory）
- retrieve-then-compress策略
- Visual Memory Retriever + C-GRPO框架
- 与thesis相关：24/7 egocentric recording的高效处理

---

### **043 Soar (Laird et al., 1987)**

**文件状态：** ❌ 损坏（只有16字节）

**问题：** 下载失败，文件损坏

**尝试过的来源：**
1. ❌ ResearchGate - 需要16字节，非PDF
2. ❌ Semantic Scholar - 无法提取
3. ❌ Academia.edu - 需要登录
4. ❌ Scribd - 需要付费

**论文信息：**
- **标题：** SOAR: An Architecture for General Intelligence
- **来源：** Artificial Intelligence, Vol 33, Issues 1-2, Pages 1-64
- **DOI：** 可能需要ACM Digital Library或Science Direct访问
- **状态：** 经典论文，可能需要付费访问

**已有资源：**
- ✅ **完整的summary：** `[S]-043-soar-1987.md` 包含所有必要信息
- ✅ **核心内容：**
  - Unified cognitive architecture
  - Universal subgoaling
  - Chunking mechanism for learning
  - Foundation for cognitive architectures research

**替代方案：**
1. **使用现有summary：** 我们已有完整的论文总结和引用信息
2. **学校图书馆：** 通过CMU图书馆访问ACM Digital Library
3. **引用书籍：** Laird, J.E. (2012). *The Soar Cognitive Architecture*. MIT Press. (包含1987年论文的核心内容)

---

## 建议的行动

### **立即可做：**

✅ **006已修复** - PDF正常，只需更新index信息（已完成）

⚠️ **043需要处理** - 选项：
1. **保持现状** - 使用现有的完整summary，引用原始论文（不需要PDF）
2. **获取PDF** - 通过CMU图书馆下载
3. **使用替代引用** - 引用Laird 2012年的Soar书籍

### **我的推荐：**

**对于Related Writing：**
- ✅ 我们已有006和043的完整summaries
- ✅ 可以直接引用，不影响写作
- ✅ Soar是经典论文，引用格式已知：
  
```
Laird, J.E., Newell, A., & Rosenbloom, P.S. (1987). 
SOAR: An Architecture for General Intelligence. 
Artificial Intelligence, 33(1-2), 1-64.
```

**PDF获取（可选）：**
- 如果真的需要原始PDF，可以通过CMU图书馆的ACM Digital Library订阅访问
- 或者联系教授/导师获取

---

## 总结

| 论文 | PDF状态 | Summary | 可用性 | 行动 |
|------|---------|---------|--------|------|
| **006 MARC** | ✅ 正常（508KB） | ✅ 完整 | ✅ 可用 | 已修复index |
| **043 Soar** | ❌ 损坏（16B） | ✅ 完整 | ✅ 可用 | 使用summary |

**结论：** 两篇论文的summaries都完整，可以直接用于Related Writing。Soar的PDF是可选的，不影响论文写作。

---

**需要你决定：**
1. 是否需要我通过CMU图书馆获取Soar 1987的PDF？
2. 还是直接使用现有的summary进行写作？
