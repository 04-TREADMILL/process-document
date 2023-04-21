[![pipeline status](http://172.29.4.49/0021/process-document/badges/master/pipeline.svg)](http://172.29.4.49/0021/process-document/-/commits/master)

[![Latest Release](http://172.29.4.49/0021/process-document/-/badges/release.svg)](http://172.29.4.49/0021/process-document/-/releases)

为了使用 Git hooks，在 clone 本仓库后请键入如下命令

```
npm install
npm run prepare
```

# 项目结构

- `iteration-1`：第一轮迭代的代码和文档所在的文件夹
  - `division.md`：第一轮迭代中小组成员分工情况的文档
  - `matrix.csv`：第一轮迭代中用到的矩阵数据文件
  - `meeting.md`：第一轮迭代中会议记录的文档
  - `ProjectInitiationDocument.md`：项目启动文档，可能包含项目的背景信息、目标和计划等
- `iteration-2`：第二轮迭代的代码和文档所在的文件夹
  - `cicd.md`：第二轮迭代中关于 CI/CD 持续集成与持续部署的文档
  - `design.md`：第二轮迭代中关于设计的文档，可能包含需求规格说明、系统设计文档等
  - `division.md`：第二轮迭代中小组成员分工情况的文档
  - `meeting.md`：第二轮迭代中会议记录的文档
  - `NoteOfSentiSE.md`：第二轮迭代中阅读 SentiStrength-SE 相关论文的笔记文档
  - `助教数据分析`：第二轮迭代中用到的助教提供的数据集所在的文件夹
    - `report.md`：第二轮迭代中对助教数据集进行分析的文档
    - `社交文本-bbc1000.csv`：BBC 新闻网站的社交文本数据文件
    - `社交文本-myspace1041.csv`：MySpace 社交网络上的文本数据文件
    - `软工文本-appreview.csv`：App Review 网站上的软件评论数据文件
    - `软工文本-sof4423.csv`：Stack Overflow 上的软件工程问题数据文件
  - `拓展数据分析`：第二轮迭代中针对其他数据集的拓展数据分析所在的文件夹
    - `emotional.xlsx`：用于情感分析的数据集
    - `SE-Text.xlsx`：用于软件工程文本分析的数据集
  - `项目代码分析`：第二轮迭代中对项目代码进行分析所在的文件夹
    - `分析报告`：分析报告所在的文件夹
      - `checkstyle 工具检测与分析`：分析 checkstyle 工具检测和分析的文件夹
        - `checkstyle 分析报告.md`：checkstyle 工具检测和分析的报告文档
        - `commit1`：第一次提交的代码版本所在的文件夹
          - `BoosterWordsList.xml` 等多个 xml 文件：checkstyle 工具所产生的报告具体内容
        - `commit2`：第二次提交的代码版本所在的文件夹，包含相同的 xml 文件内容
        - `commit3`:第三次提交的代码版本所在的文件夹，包含相同的 xml 文件内容
      - `sonarlint 工具检测与分析`：分析 sonarlint 工具检测和分析的文件夹
        - `commit1.pdf`：第一次提交的代码版本对应的 sonarqube 报告
        - `commit2.pdf`：第一次提交的代码版本对应的 sonarqube 报告
        - `commit3.pdf`：第一次提交的代码版本对应的 sonarqube 报告
    - `checkstyle.xml`：checkstyle规则文档
- `README.md`：说明本项目文件结构的文档。

# 贡献指南

欢迎对该项目进行贡献，您可以通过以下方式参与到项目中：

- 提交 bug 或 feature request
- 提交代码修复或新功能实现
- 改进文档和说明
- 参与讨论和社区建设

请注意：

- 在提交代码之前，请先 fork 该仓库，然后基于自己的分支进行开发
- 在提交代码之前请编写完整的 commit message，包含修改内容、原因和影响
