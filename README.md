# 作业

《开源创新思维》平时作业 —— 第七周作业

| 项目 | 内容 |
| --- | --- |
| 班级 | f250118 |
| 学号 | f25015243 |
| 姓名 | 姚晔 |
| 指导教师 | 祝欣蓉 |
| 开设学期 | 2026-2027 秋季学期 |
| 提交日期 | 2026 年 10 月 29 日 |

## 作业内容

利用开源软件许可合规检测工具，对一个 Apache 社区开源项目进行技术测试，生成测试报告。

- **被测项目**：Apache Commons Lang 3.17.0（Apache-2.0）
  - 源码来源：<https://github.com/apache/commons-lang>，标签 `rel/commons-lang-3.17.0`
  - 规模：576 个文件 / 63 个目录 / 8.36 MB
- **检测工具**：ScanCode Toolkit 32.5.0（Python，Windows 11 + Python 3.13.12 独立虚拟环境）
- **扫描命令**：

```bash
scancode -clpi -n 4 --timeout 900 \
  --json-pp out/commons-lang3-3.17.0_scan.json \
  --html   out/commons-lang3-3.17.0_scan.html \
  commons-lang-rel-commons-lang-3.17.0
```

## 主要结论

| 指标 | 结果 |
| --- | --- |
| 扫描资源 | 639（576 文件 + 63 目录），8.36 MB |
| 扫描耗时 / 速度 | 102.17 秒 / 5.80 文件每秒，0 个错误 |
| 许可证检出率 | 570 / 576 = **98.96%** |
| 检出许可证 | 全部为 **Apache-2.0**（无 GPL/AGPL 等传染性许可） |
| 误报 | 2 处（README、CONTRIBUTING 中的贡献者协议文本被判为 generic-cla） |
| 漏报 | 6 处（图片、空文件、CGI 脚本、历史发行说明与测试数据） |
| 版权声明检出 | 2 条（召回率 0.35%，ASF 头部不含 Copyright 年份） |

**合规结论**：Apache Commons Lang 3.17.0 为纯净的 Apache-2.0 项目，可安全商用与再分发；义务为保留 LICENSE 与 NOTICE、标注修改。工具输出需经人工复核方可作为合规结论，版权与依赖维度需以 NOTICE、SBOM 交叉验证。

## 目录结构

```
.
├── f25015243-姚晔-Apache Commons Lang-软件许可测试报告.docx   # 测试报告正文
├── README.md
└── 扫描原始报告/
    ├── commons-lang3-3.17.0_scan.html    # ScanCode 输出的 HTML 报告（人工浏览）
    ├── commons-lang3-3.17.0_scan.json    # ScanCode 输出的 JSON 报告（机器可读）
    └── 图1-许可证检测结果.png            # 报告中图 1 的原图
```
