# session2-practice-ci-cd

数据工程 session-2 练习二：用 GitHub Actions 实现 CI/CD + 自动 Release。

## 流程

1. 向 `main` 分支 push（且 `training_data.csv` 有变化时）触发 workflow
2. 安装依赖 → 用 `train_model.py` 训练线性回归模型 → 生成 `linear_model.txt`
3. 把 `linear_model.txt` 推到 `release` 分支（orphan 分支，只放模型文件）
4. 自动创建 GitHub Release（tag 为 `v<run_number>`），并把 `linear_model.txt` 作为 release 资产上传

## 文件

| 文件 | 作用 |
| --- | --- |
| `.github/workflows/ci-cd.yml` | CI/CD 流水线定义 |
| `training_data.csv` | 训练数据（YearsExperience → Salary） |
| `train_model.py` | 训练脚本 |
| `requirements.txt` | Python 依赖 |

## 验证

- `Actions` 标签页能看到成功的 workflow run
- `Releases` 标签页能看到自动生成的 release 和 `linear_model.txt` 附件
- `release` 分支上只有 `linear_model.txt`
