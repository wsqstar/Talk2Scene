
# **Talk2Scene**  

**Talk2Scene** 是一款功能强大的**终端应用程序**，能够将**音频对话**自动转换为**动态动画场景**。通过先进的AI技术，它可以生成包含**角色姿态**、**表情**、**动作**、**背景**和**CG插画**的完整场景。该工具专为**内容创作者**、**教育工作者**和**AI爱好者**设计，旨在将音频内容转化为引人入胜的视觉叙事。

---

## **核心功能**  

### **1. 音频转录**  
- 支持**多语言音频输入**，使用 **OpenAI Whisper** 进行语音识别。  
- 生成带**时间戳的文本**，确保场景同步精准。  
- 本地缓存转录结果，避免重复处理。  

### **2. 场景生成**  
- 使用 **GPT-4** 智能解析文本并生成**场景组件**：  
  - **STA（姿态）**：如站立、坐下或倚靠等角色姿态。  
  - **EXP（表情）**：如中性、微笑或惊讶等面部表情。  
  - **ACT（动作）**：如举手、耸肩等动画动作。  
  - **BG（背景）**：如咖啡厅、实验室等场景背景。  
  - **CG（插画）**：在关键时刻自动插入**CG插画**。  
- 支持**多角色对话分离**，生成独立的角色时间线。  

### **3. 增量视频渲染**  
- 分块渲染视频，优化内存使用。  
- 支持**淡入淡出过渡**，确保场景切换流畅。  
- 生成带**音频同步**的预览视频。  

### **4. 动态状态管理**  
- 使用**状态机**确保姿态和表情之间的自然过渡。  
- 跟踪场景历史，保持角色行为一致。  

### **5. AI驱动的CG插画**  
- 使用 GPT-4 自动检测**CG插入点**。  
- 支持通过 **DALL·E** 或 **Stable Diffusion** 生成**AI插画**。  
- 允许手动上传自定义CG资源。  

### **6. 性能监控**  
- 跟踪**系统指标**，如CPU、内存和渲染时间。  
- 生成**详细性能报告**，便于优化。  

---

## **安装指南**  

### **环境要求**  
- **Python 3.8+**  
- **FFmpeg**（用于视频处理）  
- **OpenAI API 密钥**（用于 Whisper 和 GPT-4）  

### **安装步骤**  
1. 克隆仓库：  
   ```bash
   git clone https://github.com/your-repo/talk2scene.git
   cd talk2scene
   ```  

2. 安装依赖：  
   ```bash
   pip install -r requirements.txt
   ```  

3. 设置目录结构：  
   ```bash
   mkdir -p input output config assets/{sta,exp,act,bg,cg}
   ```  

4. 将**音频文件**（`input_audio.wav`）放入 `input` 目录。  

5. 运行应用程序：  
   ```bash
   python talk2scene.py
   ```  

---

## **使用说明**  

### **输入**  
- 将音频文件放入 `input` 目录。  
- 支持格式：`.wav`, `.mp3`。  

### **输出**  
- **CSV 文件**：包含场景元数据（时间戳、文本、姿态、表情等）。  
- **视频文件**：完整渲染的视频，包含动画和音频。  
- **JSON 文件**：存储中间数据，支持中断后恢复处理。  

### **示例 CSV 输出**  
| 时间戳   | 文本                          | STA（姿态）      | EXP（表情）      | ACT（动作）    | BG（背景）      | CG（插画）        |  
|----------|-------------------------------|-----------------|-----------------|---------------|----------------|------------------|  
| 0.00s    | "大家好，欢迎来到节目！"       | STA_Stand_Default| EXP_Smile       | ACT_Wave      | BG_Studio      | CG_Intro         |  
| 3.50s    | "今天，我们讨论人工智能。"     | STA_Sit_Normal  | EXP_Thinking    | ACT_Shrug     | BG_Lab         | CG_AI_Impact     |  

---

## **配置说明**  

### **角色配置**  
编辑 `config/character_config.yaml` 以自定义角色资源：  
```yaml
paths:
  sta_dir: assets/sta  # 姿态图片路径
  exp_dir: assets/exp  # 表情图片路径
  act_dir: assets/act  # 动作动画路径
  bg_dir: assets/bg    # 背景图片路径
  cg_dir: assets/cg    # CG插画路径
```  

### **API 密钥**  
设置 OpenAI API 密钥为环境变量：  
```bash
export OPENAI_API_KEY="your-api-key"
```  

---

## **性能优化**  
- **增量渲染**：通过分块渲染减少内存占用。  
- **并行处理**：并发处理场景，加快执行速度。  
- **本地缓存**：存储中间结果，避免重复计算。  

---

## **未来计划**  
- **实时预览**：在视频生成过程中启用实时预览。  
- **图形界面**：为非技术用户开发友好的图形界面。  
- **多平台支持**：优化对 Windows、macOS 和 Linux 的支持。  
- **情感检测**：分析音频情感，动态调整表情和动作。  
- **API 集成**：支持与第三方服务集成，生成资源。  

---

## **许可证**  
本项目采用 **MIT 许可证**。详情请参阅 [LICENSE](LICENSE) 文件。  

---

## **贡献指南**  
欢迎贡献代码！请阅读我们的 [贡献指南](CONTRIBUTING.md) 了解详情。  


---

**© 2024 Talk2Scene**  
**由 AI 助手开发 ❤️**  
