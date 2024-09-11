# ollama_Settings

### Ollama常用命令

1.Ollama 导入模型¶
导入模型

本指南将向您展示如何导入一个 GGUF、PyTorch 或 Safetensors 模型。

导入（GGUF）

步骤 1：编写模型文件

开始之前，您需要创建一个模型文件。这个文件就像是您模型的设计图，里面指定了模型的权重、参数、提示模板等信息。

```FROM ./mistral-7b-v0.1.Q4_0.gguf```

（可选）很多聊天模型为了能够正确回答问题，需要一个预设的提示模板。您可以通过在模型文件中添加 TEMPLATE 指令来设定一个默认的提示模板：

```FROM ./mistral-7b-v0.1.Q4_0.gguf
TEMPLATE "[INST] {{ .Prompt }} [/INST]"```

步骤 2：创建 Ollama 模型

接下来，根据您的模型文件创建一个新模型：

```ollama create example -f Modelfile```