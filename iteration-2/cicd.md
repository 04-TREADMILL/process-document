# 流程综述

1. 后端代码部署流水线触发，将打包的 jar 上传到阿里云 OSS (https://senti-strength.oss-cn-nanjing.aliyuncs.com/myEASIEST-1.0-SNAPSHOT.jar)
2. 前端使用 Python Streamlit 框架，使用 Docker 部署，其构建脚本中会设置对应的 word lists 和 jar 包

# TODO

1. 前端动态配置 jar 包，设置相应的缓存时间