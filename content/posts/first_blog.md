+++
date = '2026-07-17T18:27:11+08:00'
draft = false
title = 'First_blog'
+++
#这是我的第一篇博客
# 开源软件开发实践1：基于Hugo+GitHub Actions搭建个人Blog

## 一、本地环境准备：安装依赖工具
1. **安装Hugo扩展版**
    - 解压Hugo安装包，将程序文件夹添加至系统环境变量；
    - 打开命令行执行`hugo version`，输出版本号即安装成功。
2. **安装Git**
    - 运行Git安装程序，全程默认Next完成安装；
    - 可选安装FastGitHub，加速GitHub网络访问。
3. **安装GitHub Desktop（可视化工具，可选）**
    - 安装后登录个人GitHub账号，完成账号授权。

## 二、本地搭建Hugo博客站点
1. **新建博客站点目录**
    命令行进入工作目录，执行`hugo new site 博客文件夹名`，生成完整博客项目结构。
2. **配置博客主题**
    - 下载Hugo主题包，解压后放入项目`themes`文件夹；
    - 修改根目录`config.toml`配置文件，添加`theme = "主题文件夹名"`。
3. **创建第一篇博客文章**
    - 执行`hugo new posts/第一篇文章名.md`，自动生成Markdown文稿；
    - 打开文章文件，将`draft: true`改为`draft: false`（取消草稿，否则网页不展示），写入博客正文内容。
4. **本地预览调试**
    执行`hugo server -D`，浏览器访问`http://localhost:1313`查看本地博客效果，确认文章、页面显示正常。
5. **生成静态网页文件**
    命令行执行`hugo`，项目内自动生成`public`文件夹，存放可直接部署的静态网页资源。

## 三、创建GitHub公开仓库
1. 登录GitHub网页端，新建公开仓库，仓库名必须为`你的GitHub用户名.github.io`，私有仓库无法开启GitHub Pages。
2. 本地`public`文件夹初始化Git仓库：
    ```bash
    git init
    git add .
    git commit -m "初次提交博客静态文件"
    ```
3. 两种方式推送代码到云端仓库：
    - 命令行：关联远程仓库地址，执行`git push`推送；
    - GitHub Desktop：添加本地`public`仓库，点击`Publish repository`推送，取消私有勾选。

## 四、配置GitHub Pages基础发布（基础部署）
1. 打开云端仓库页面，进入`Settings`→`Pages`；
2. 在Build and deployment的Source选项选择`Deploy from a branch`；
3. 分支选择`main/master`，目录选择`/(root)`，点击Save保存；
4. 等待页面部署完成，即可通过`用户名.github.io`访问博客。

## 五、配置GitHub Actions实现自动发布
1. 在博客根目录创建`.github/workflows`文件夹，新建Actions配置yaml文件；
2. 编写工作流脚本：实现代码提交后自动拉取Hugo、构建静态页面、自动部署至GitHub Pages；
3. 将完整博客源文件（非仅public静态文件）推送至GitHub远程仓库；
4. 提交代码后，仓库自动触发Actions任务，在仓库`Actions`标签页查看运行日志；
5. 确认至少有1条绿色成功运行记录，复制该记录页面链接用于报告填写。

