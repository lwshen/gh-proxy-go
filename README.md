# gh-proxy-go

简单的 GitHub 文件代理工具。修改自 [hunshcn/gh-proxy](https://github.com/hunshcn/gh-proxy)，但是更轻量。

A simple Go proxy for GitHub API, but MUCH lighter. Ported & modified from [hunshcn/gh-proxy](https://github.com/hunshcn/gh-proxy).

## 用法

### Docker

```bash
# 直接运行，只允许代理 GitHub 链接
docker run -d -p 80:80 --name gh-proxy-go ghcr.io/lwshen/gh-proxy-go
# 允许代理任意链接
docker run -d -p 80:80 --name gh-proxy-go ghcr.io/lwshen/gh-proxy-go --allow-any-url
```

### 命令行运行

在 Releases 下载对应平台的二进制文件运行，或者使用 Go 编译后运行。

```bash
# 直接运行在 0.0.0.0:80
./gh-proxy-go

# 修改端口 / 地址
./gh-proxy-go --port 8080 --host 127.0.0.1

# 允许代理任意链接
./gh-proxy-go --allow-any-url
```

### Git Clone 代理 / Git Clone Proxy

配置 Git 使用此代理时，需要将 URL 替换为您的代理 URL，例如：

When configuring Git to use this proxy, you need to replace the URL with your proxy URL, for example:

```bash
# 替换前 / Before replacement
git clone https://github.com/username/repo.git

# 替换后 (假设代理部署在 https://your-proxy-domain.com)
# After replacement (assuming the proxy is deployed at https://your-proxy-domain.com)
git clone https://your-proxy-domain.com/github.com/username/repo.git
```

您也可以配置 Git 全局代理：

You can also configure a global Git proxy:

```bash
git config --global url."https://your-proxy-domain.com/https://github.com/".insteadOf "https://github.com/"
```

这样就可以正常使用 `git clone https://github.com/username/repo.git` 命令，Git 会自动将请求通过您的代理发送。

This way you can use the normal `git clone https://github.com/username/repo.git` command, and Git will automatically send requests through your proxy.
