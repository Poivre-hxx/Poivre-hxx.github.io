---
title: git commit时的verified认证配置说明
tags: 
  - git
categories: 
  - [Others]
date: 2024-09-30 20:20:00


---

🤗🤗基于win环境，使用 Github Desktop 软件的配置🤗🤗

<!-- more -->

## 事先准备

[Gpg4win]: https://gpg4win.org/get-gpg4win.html	"gpg4win"

选择$0即可免费下载，安装完毕后可以得到一个这样的软件。 <img src="https://pic-poivre.oss-cn-hangzhou.aliyuncs.com/pics/image-20240929215613611.png" alt="image-20240929215613611" style="width:9%;" />

## 创建密钥对

1. 选择 “新建密钥对”，然后根据提示创建密钥（如果没有特殊需求的话，建议有效期选择长一些或者直接设置为永久，一劳永逸）

2. 将公钥放到自己的github账号上

   - 右击选择新建的密钥对，选择 “细节”

     <img src="https://pic-poivre.oss-cn-hangzhou.aliyuncs.com/pics/image-20240929220242807.png" alt="image-20240929220242807" style="width:40%;" />

   - 然后在“证书明细”界面选择“导出...”

     <img src="https://pic-poivre.oss-cn-hangzhou.aliyuncs.com/pics/image-20240929220414635.png" style="width:50%;" />

   - 打开您的github主页，选择 "setting" -> "SSH and GPG keys"，将复制到的公钥部分放入 ”GPG keys“ 中

## 启用 Git 提交签名

1. 终端定位至 Github Desktop 安装文件中的 git 文件夹

   路径为 `app -> resources -> app -> git`

2. 将 Github Desktop 调用的路径改为 GPG 客户端路径（可以在`gitbash`中通过 “where gpg” 查询得到）

   ```shell
   git config --global gpg.program "gpg客户端路径"
   ```

   

3. 配置 Github Desktop 默认签名的 GPG Key ID（也就是配置的“密钥 ID”）

   ```shell
   git config --global user.signingkey "Key ID"
   ```

   

4. 配置邮箱

   ```shell
   git config --global user.email "您的邮箱"
   ```

   

5. 开启 commit 的 GPG 签名功能

   ```shell
   git config --global commit.gpgsign true
   ```

   