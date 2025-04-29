

## 项目简介



## 项目特色



## 项目截图

## 项目源码


## 项目文档




## 项目启动


- **环境准备**

| 环境类型       | 版本要求                     | 下载链接                     |
|----------------|-----------------------------|-----------------------------|
| **开发工具**   | Visual Studio Code (最新版) | [官方下载](https://code.visualstudio.com/Download) |
| **运行环境**   | Node.js 18.x (推荐18.16.1)  | [中文镜像](https://npmmirror.com/mirrors/node/v18.16.1/) |
> ⚠️ 注意：Node.js 20.6.0版本存在兼容性问题，请勿使用


- **快速开始**

```bash
# 克隆代码
git clone https://gitee.com/youlaiorg/vue3-element-admin.git

# 切换目录
cd vue3-element-admin

# 安装 pnpm
npm install pnpm -g

# 设置镜像源(可忽略)
pnpm config set registry https://registry.npmmirror.com

# 安装依赖
pnpm install

# 启动运行
pnpm run dev
```


## 项目部署

执行 `pnpm run build` 命令后，项目将被打包并生成 `dist` 目录。接下来，将 `dist` 目录下的文件上传到服务器 `/usr/share/nginx/html` 目录下，并配置 Nginx 进行反向代理。

```bash
pnpm run build
```

以下是 Nginx 的配置示例：

```nginx
server {
    listen      80;
    server_name localhost;

    location / {
        root   /usr/share/nginx/html;
        index  index.html index.htm;
    }

    # 反向代理配置
    location /prod-api/ {
        # 请将 api.youlai.tech 替换为您的后端 API 地址，并注意保留后面的斜杠 /
        proxy_pass http://api.youlai.tech/;
    }
}
```

