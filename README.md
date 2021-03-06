<p align="center">
  <img src="./logologo.png" center />
</p>

# [Vaultwarden](https://github.com/dani-garcia/vaultwarden)

用 Rust 编写的非官方 Bitwarden 兼容服务器，以前称为 bitwarden_rs。本项目是vaultwarden的云开发应用版

## 使用

配合腾讯云cloudbase可以实现免费搭建bitwarden_rust版本，数据存储在CFS是分离的，docker这边就算消失了数据也不会丢失。并且可以使用CFS快照备份。

如果要提取出sqlite文件的话就有点麻烦。需要创建一个和CFS处于同一子网的CVM（竞价实例好些），然后挂载CFS再取出文件（用Windows服务器就可以了，在CVM中从CFS里面复制到CVM里面然后压缩一下再复制到本地）

![pic1](pic1.png)

点击下方按钮即可使用

## 部署

本项目基于腾讯开源项目 [CloudBase Framework](https://github.com/Tencent/cloudbase-framework) [![star](https://img.shields.io/github/stars/Tencent/cloudbase-framework?style=social)](https://github.com/Tencent/cloudbase-framework) 开发部署，支持一键云端部署

[![](https://main.qcloudimg.com/raw/67f5a389f1ac6f3b4d04c7256438e44f.svg)](https://console.cloud.tencent.com/tcb/env/index?&action=CreateAndDeployCloudBaseProject&appUrl=https://github.com/james-curtis/vaultwarden-cloudbase&branch=master)

### 配置


- SIGNUPS_ALLOWED，默认true 控制新用户是否可以注册
- INVITATIONS_ALLOWED，默认true 允许管理员邀请用户，即使注册被禁用

配置参考：https://github.com/dani-garcia/vaultwarden/blob/main/.env.template

### 依赖


- CFS：共享文件存储服务。需要使用 CFS 持久化配置数据

## 开发

你也可以下载项目后，使用 [CloudBase CLI](https://docs.cloudbase.net/cli-v1/intro.html) 在终端中一键部署。

```
npx @cloudbase/cli framework deploy -e 环境id
```

## 注意事项

1. 部署完毕之后建议关闭注册功能，设置SIGNUPS_ALLOWED为false。修改位置在腾讯云——云开发——云托管——vaultwarden-container——vaultwarden-container-001——配置信息——编辑配置并重新部署——环境变量

## 文档

- [CloudBase Framework 文档](https://docs.cloudbase.net/framework/)
- [Vaultwarden Wiki](https://github.com/dani-garcia/vaultwarden/wiki)
