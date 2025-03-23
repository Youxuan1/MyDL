# 神奇的包管理器 uv

对于不同的项目，通常需要不同的 python 依赖。然而，如果都用 conda 或者 pip 来管理的话，就会显得很麻烦。当然还有个中缘由了，反正我发现这个 uv 还挺好用的，风评也挺好，叫“现代化”版本管理工具。他能实现每个项目提供单独的虚拟环境。

## 创建新项目

可以用 uv init 命令创建新的 python 项目，并通过 --python [版本号] 来指定 python 版本。

```bash
uv init hello-world --python 3.9
```

运行以后就会自动创建 main.py, .venv/, pyproject.toml, .python-version, README.md。

如果有已经写好的项目，就不用写项目名（但是还是要指定 python 版本，不然后面还要到 pyproject.toml里面改了以后 uv lock --upgrade）

## 运行文件

```bash
uv run main.py
```

## 安装 python 库

```bash
uv add numpy==2.1
```

## 删除 python 库

```bash
uv remove requests
```

## 安装并锁定 python 版本

```bash
uv python install 3.9
uv python pin 3.9

uv venv --python 3.12.0
uv run --python pypy@3.8 --python
```

## 保存依赖列表文件

保存在 uv.lock里面

```
uv lock
```

或者，传统地

```bash
uv pip freeze > requirements.txt 
```

## 同步环境

想复制别人的环境，只需要有pyproject.toml和uv.lock文件

```bash
uv venv --python [版本号]
uv sync
```

或者，传统地

```bash
uv pip install -r requirements.txt
```

## 查看依赖树

别的好多命令都跟直接用pip差不多，反正前面加个uv就对了。

另外，既然都用 uv 了，一般也不需要激活环境。要激活的话也是在.venv/bin/activate激活，取消激活直接输入deactivate。

```bash
uv pip tree
```

