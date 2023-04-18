# 概述

- 后端代码部署流水线触发，将打包的 jar 上传到阿里云 OSS (https://senti-strength.oss-cn-nanjing.aliyuncs.com/myEASIEST-1.0-SNAPSHOT.jar)
- 前端使用 Python Streamlit 框架，使用 Docker 部署，其构建脚本中会设置对应的 word lists 和 jar 包，可以动态获取到最新的 jar 包

# 后端流水线搭建

- 分为四个阶段：构建、测试、上传、发布
- 基础镜像为 gradle
- 使用 cache 机制在不同的 jobs 间传递 jar 包
- 上传阶段利用了 aliyun cli 上传 jar 包到 oss 对象存储服务器，使用变量保护 ak 和 sk 等隐私信息
- 发布阶段利用了 gitlab 自带的 release-cli

> refs:
> 1. https://help.aliyun.com/product/29991.html
> 2. https://help.aliyun.com/document_detail/179388.html
> 3. https://docs.gitlab.com/ee/user/project/releases/release_cicd_examples.html
> 4. https://docs.gitlab.com/ee/ci/variables/index.html#cicd-variable-security

# 前端流水线搭建

- 由于既有的 gitlab runner 无法提供 docker in docker 服务，自构建的 gitlab runner 又无法连接校园网，所以考虑在远程服务器上构建镜像
- 使用变量保存 RSA PRIVATE KEY
- 执行 scp 和 ssh 命令即可
- TODO: docker login and push

> refs:
> 1. https://docs.gitlab.com/ee/ci/variables/index.html#use-file-type-cicd-variables
