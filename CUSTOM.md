# v0.3.13-libo.1

基于 [haowang02/cpa-plugin-codex-candy-eval v0.3.13](https://github.com/haowang02/cpa-plugin-codex-candy-eval/tree/v0.3.13)（`876d1ab480ca297b82367f09392dbbcb785e86c8`），保留原作者、MIT 许可与测试逻辑。

插件共享 `api()` 从页面 `/v0/resource/plugins/` 之前的路径提取 CPA 部署前缀，使 `/v0/management`、`/v8/management` 和 `/v1/models` 在 `/cpa`、多段路径或根目录下均使用正确地址。

回归检查：

```sh
node scripts/test-ui.cjs
go vet ./...
go test -race ./...
```

插件版本及 GitHub 元数据指向本 fork。README 中保留的原版安装命令仍安装上游版本；本修复可从本 fork 对应版本的 release 资产或源码构建获取。

Linux ARM64 构建需在 ARM64 环境中以 `CGO_ENABLED=1`、`-tags cshared -buildmode=c-shared` 构建，并检查实际 CPA 容器的 glibc 兼容性；现有 `scripts/deploy.sh` 是 Linux AMD64 部署脚本，不能直接用于 ARM64 服务器。
