# pgit

pgit 是 Proxy Git 的缩写，使用镜像加速 github 下载,支持 repo,release

## 仓库

- [github](https://github.com/gcslaoli/pgit)
- [gitee](https://gitee.com/gcslaoli/pgit)

[![李栋/pgit](https://gitee.com/gcslaoli/pgit/widgets/widget_card.svg?colors=ffffff,1e252b,323d47,455059,d7deea,99a0ae)](https://gitee.com/gcslaoli/pgit)

## 安装

从`github`下载

```bash
curl -o pgit https://raw.githubusercontent.com/gcslaoli/pgit/main/shell/pgit && chmod +x pgit && mv pgit /usr/local/bin
```

从`gitee`下载

```bash
curl -o pgit https://gitee.com/gcslaoli/pgit/raw/main/shell/pgit && chmod +x pgit && mv pgit /usr/local/bin
```

## 使用

对于`git clone`加速,使用`pgit`替代`git`.

`pgit`会自动判断是否需要加速,如果需要加速,则会自动使用镜像地址.传入的参数与`git`完全一致,事实上内部使用的也是`git`.

```bash
pgit clone https://github.com/cool-team-official/cool-admin-vue.git
```

当需要通过`wget`或者`curl`下载 relase branch raw 等资源时,可以使用`pgit`加速.在原`wget`或者`curl`命令前加上`pgit`即可.

例如`cool-tools`的 wget 安装脚本为:

```bash
wget -O cool-tools https://github.com/cool-team-official/cool-admin-go/releases/latest/download/cool-tools_$(go env GOOS)_$(go env GOARCH) && chmod +x cool-tools && ./cool-tools install  && rm ./cool-tools
```

可以使用`pgit`加速:

```bash
pgit wget -O cool-tools https://github.com/cool-team-official/cool-admin-go/releases/latest/download/cool-tools_$(go env GOOS)_$(go env GOARCH) && chmod +x cool-tools && ./cool-tools install  && rm ./cool-tools
```

## 配置

`pgit`默认使用的镜像地址为`https://ghproxy.com/`,如果需要使用其他镜像地址,可以设置环境变量`PGIT_PREFIX`来指定.

例如使用`https://gh.hjmcloud.cn/`:

```bash
export PGIT_PREFIX=https://gh.hjmcloud.cn/
```

## 自建镜像

如果需要自建镜像,可以使用开源项目[gh-proxy](https://github.com/hunshcn/gh-proxy)来搭建.
