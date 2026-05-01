# ai-agents
by langchain langgraph

#### 安装uv--新一代py包管理器
https://docs.astral.sh/uv/getting-started/installation/#standalone-installer

#### 初始化项目
##### 创建根目录

##### 进入根目录后执行初始化命令
以py version3.13为例
```
uv init -p 3.13
```

安装基础依赖
```
uv add langchain langchain-openai uvicorn langchain-community fastapi dashscope
```

安装环境管理工具: 根目录创建 .env 文件
```
uv add dotenv
```



langsmith可能需要更新依赖库
```
uv pip install --upgrade rich structlog langgraph-api langgraph
```

使用langsmith、langgraph的项目，需要配置相关环境
在 .env 文件添加
```
LANGSMITH_API_KEY=xxxx
LANGSMITH_TRACING=true
LANGSMITH_PROJECT=xxxx
```

根目录创建 langgraph.json 文件
```
{
    "dependencies": [
        "."
    ],
    "graphs": {
        "my_agent": "app/agents/default_agent.py:agent"
    },
    "env": ".env"
}
```

运行
```
uv run langgraph dev
```


#### 运行项目
开发环境 --reload开启热加载
```
uv run uviccorn app.main:app --reload --host 0.0.0.0 --port 8001
```
