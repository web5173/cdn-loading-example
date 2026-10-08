# 从 CDN 加载前端依赖示例

一个极简示例：**入口页只有一个 div，不打包、不构建**，所有 JS / CSS 依赖都在浏览器运行时从 unpkg CDN 动态加载。

> ⚠️ 仅用于学习参考，未在实际项目中使用。

## 功能

- 单文件入口，零构建、零本地依赖
- 通过 `loadCSS` / `loadScript` 按 `base` 地址从 CDN 加载资源
- 预加载 Vue、Element Plus（中文 + 暗色）、PocketBase、idb-keyval、exifr、wasm-vips
- 以 `@web5173/woc` 应用包作为实际渲染的 Demo 页面
- Deno 服务返回同一入口页，并附带 COOP/COEP 响应头，使 `wasm-vips` 可用 SharedArrayBuffer 做图像处理

## 加载的资源

| 类型 | 资源 |
| --- | --- |
| CSS | normalize.css、animate.css、Element Plus 及其暗色变量 |
| 脚本 | Vue 3、Element Plus、PocketBase、idb-keyval、exifr、wasm-vips |
| 应用 | `@web5173/woc`（模块方式加载） |

## 目录结构

```
index.html      静态入口页，可直接用浏览器打开或部署到任意静态托管
woc/main.ts     Deno 服务，返回同样的入口页并附加 COOP/COEP 头
woc/deno.json   Deno 任务与部署配置
```

## 运行

直接打开 `index.html` 即可。

或通过 Deno 启动（带 COOP/COEP 头）：

```bash
cd woc
deno task dev
```

## 说明

本仓库**仅用于学习参考，并未在实际项目中使用**。

`@web5173/woc` 只是一个被加载的示例应用，重点在于 CDN 动态加载的写法本身。
