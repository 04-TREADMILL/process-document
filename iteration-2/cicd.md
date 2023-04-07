# 概述

1. 后端代码部署流水线触发，将打包的 jar 上传到阿里云 OSS (https://senti-strength.oss-cn-nanjing.aliyuncs.com/myEASIEST-1.0-SNAPSHOT.jar)
2. 前端使用 Python Streamlit 框架，使用 Docker 部署，其构建脚本中会设置对应的 word lists 和 jar 包，可以动态获取到最新的 jar 包

# TODO

1. 流水线搭建