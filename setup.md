# 环境配置指南

## 系统要求
- **OS**: macOS 14+ / Ubuntu 22.04+ / Windows 11 (WSL2)
- **RAM**: 16GB+
- **GPU**: NVIDIA GTX 1060+（可选）

## 安装步骤

```bash
# 1. 安装 Node.js 20+
node -v  # >= 20.0.0

# 2. 安装 Python 3.11
conda create -n ai-cad python=3.11
conda activate ai-cad

# 3. 安装 text-to-cad Skills
npm install -g @anthropic-ai/skills
npx skills install earthtojake/text-to-cad

# 4. 配置 LLM API
export OPENAI_API_KEY="sk-..."
# 或本地 Ollama
ollama pull codellama:13b

# 5. 验证
npx skills run cad --prompt "Create a 50mm cube" --output ./test.step
npx skills run cad-viewer --file ./test.step
```

## 故障排除
- Skills 安装失败：`rm -rf ~/.skills/cache` 后重试
- CAD Viewer 端口占用：`--port 8888`
- 尺寸偏差：检查单位，明确 mm/inch
