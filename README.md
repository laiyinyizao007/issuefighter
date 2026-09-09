# IssueFighter

通过 GitHub Issue 与 Claude AI 协作的自动化平台。

## 使用方法

在任意 Issue 评论中提及 `@claude`，即可触发 Claude 自动响应。

| 触发方式 | 说明 |
|----------|------|
| Issue 评论含 `@claude` | 最常用，在已有 Issue 下评论 |
| 新 Issue 标题或正文含 `@claude` | 创建时直接触发 |

## 示例

```
@claude 请帮我分析这段代码的时间复杂度，并给出优化建议：

def find_pairs(lst, target):
    result = []
    for i in range(len(lst)):
        for j in range(i + 1, len(lst)):
            if lst[i] + lst[j] == target:
                result.append((lst[i], lst[j]))
    return result
```

## 工作流

| 文件 | 用途 |
|------|------|
| `claude.yml` | 核心：监听 `@claude` 触发，调用 Claude Code Action |
| `auto-add-to-project.yml` | 自动将 Issue 加入项目看板（可选） |

## 必要配置

在 GitHub 仓库 `Settings → Secrets and variables → Actions` 中配置：

| Secret | 说明 |
|--------|------|
| `ANTHROPIC_API_KEY` | API 鉴权 Key |
| `ANTHROPIC_BASE_URL` | API 代理端点（如使用代理） |
| `PROJECT_TOKEN` | GitHub PAT（`repo + project` scope），用于项目看板，可选 |

Variable（可选）：`PROJECT_NUMBER` — 项目看板编号

## Claude 行为指令

见 [`CLAUDE.md`](./CLAUDE.md)
