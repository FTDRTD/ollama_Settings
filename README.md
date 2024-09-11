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

```FROM ./mistral-7b-v0.1.Q4_0.gguf```

```TEMPLATE "[INST] {{ .Prompt }} [/INST]"```

步骤 2：创建 Ollama 模型

接下来，根据您的模型文件创建一个新模型：

```ollama create example -f Modelfile```

配置并行处理请求的数量

```OLLAMA_NUM_PARALLEL```

同时加载的模型数量

```OLLAMA_MAX_LOADED_MODELS```

我们在平时使用ollama过程中会遇到不少问题，比如模型镜像加载在C 盘有没有办法切换到其他盘符、启动ollama 只能127.0.0.1 不能使用IP 访问等问题。这些问题都是可以借助ollama 属性设置来解决。

     1 OLLAMA_HOST=0.0.0.0 解决外网访问问题

     2 OLLAMA_MODELS=E:\ollamaimagers   解决模型默认下载C 盘的问题

     3 OLLAMA_KEEP_ALIVE=24h     设置模型加载到内存中保持24个小时(默认情况下，模型在卸载之前会在内存中保留 5 分钟)

     4.OLLAMA_HOST=0.0.0.0:8080  解决修改默认端口11434端口

     5.OLLAMA_NUM_PARALLEL=2  设置2个用户并发请求

     6.OLLAMA_MAX_LOADED_MODELS=2 设置同时加载多个模型

     7.OLLAMA_FLASH_ATTENTION 
     flash attention 可以显著减少注意力机制计算的时间，使得Transformer模型在训练和推理时能够更快地处理大量数据，而且它通过优化内存访问模式，减少了计算过程中的内存占用。这不仅有助于降低内存开销，还减少了计算过程中的内存带宽瓶颈。