# Python + Playwright 配置指南

> 完整的 Python 后端 + E2E 测试配置

## 项目结构

```
your-project/
├── .claude/
│   ├── settings.json
│   ├── agents/
│   │   ├── backend.md
│   │   └── tester.md
│   └── CLAUDE.md
├── src/                    # 源代码
├── tests/
│   ├── unit/              # pytest 单元测试
│   └── e2e/               # Playwright E2E 测试
│       └── screenshots/   # 失败截图
├── requirements.txt
└── playwright.config.toml
```

## 配置文件

### settings.json

```jsonc
{
  "$schema": "https://json.schemastore.org/claude-code-settings.json",
  "subagentModel": "claude-sonnet-4-6",
  "env": {
    "PATH": "/Users/your_name/.virtualenvs/mundo/bin:${PATH}",
    "VIRTUAL_ENV": "/Users/your_name/.virtualenvs/mundo",
    "PYTHONPATH": "${VIRTUAL_ENV}/lib/python3.11/site-packages",
    "PLAYWRIGHT_BROWSERS_PATH": "/Users/your_name/.cache/ms-playwright"
  },
  "permissions": {
    "allow": [
      "Read(**)",
      "Edit(**)",
      "Bash(git *)",
      "Bash(python *)",
      "Bash(pytest *)",
      "Bash(playwright *)",
      "Bash(pip *)"
    ]
  }
}
```

### backend.md

```markdown
---
name: backend
description: Python 后端 API 实现，使用 FastAPI/Flask
tools: Read, Write, Edit, Bash, Glob
model: claude-sonnet-4-6
---

你是后端工程师，使用 Python。

## 技术栈
- 读取项目确认框架（FastAPI/Flask）
- Python 3.11+

## 实现规范
- 所有接口必须有参数校验
- 所有接口必须有错误处理
- 敏感操作必须有权限校验

## 完成标准
- 运行 `python -m pytest tests/unit/ -x`
- 通过后执行 `git commit`
```

### tester.md

```markdown
---
name: tester
description: pytest 单元测试 + Playwright E2E 测试
tools: Read, Write, Edit, Bash, Glob, Grep
model: claude-haiku-4-5
---

你是测试工程师，使用 Python + Playwright。

## pytest 单元测试

### 覆盖内容
- 正常路径
- 边界条件
- 异常情况

### 测试位置
- 单元测试：`tests/unit/`
- 与新增 API 同名

### 运行命令
```bash
python -m pytest tests/unit/ --cov --cov-report=term
```

### 完成标准

- 覆盖率 ≥ 80%
- 不修改业务代码

## Playwright E2E 测试

### 测试位置

- E2E 测试：`tests/e2e/`
- 失败截图：`tests/e2e/screenshots/`

### 运行命令

```bash
playwright test --reporter=list
```

### 测试模板

```python
from playwright.sync_api import Page, expect

def test_login(page: Page):
    # 导航到登录页
    page.goto("http://localhost:3000/login")

    # 填写表单
    page.fill('[name="email"]', "test@example.com")
    page.fill('[name="password"]', "password123")

    # 提交表单
    page.click('[type="submit"]')

    # 验证结果
    expect(page.locator("h1")).to_contain_text("Dashboard")
```

### 完成标准

- E2E 场景全部覆盖
- 失败有截图
- 执行 `git commit`

```

## requirements.txt

```txt
# Web 框架
fastapi==0.104.1
uvicorn[standard]==0.24.0

# 数据库
sqlalchemy==2.0.23
alembic==1.12.1

# 测试
pytest==7.4.3
pytest-cov==4.1.0
pytest-asyncio==0.21.1

# E2E 测试
playwright==1.40.0

# 工具
pydantic==2.5.0
python-dotenv==1.0.0
```

## playwright.config.toml

```toml
[tool.playwright]
test_dir = "tests/e2e"
browser_channel = "chromium"
headed = false
screenshot = "only-on-failure"
video = "retain-on-failure"

[tool.playwright.config]
reporter = "list"
timeout = 30000

[tool.playwright.config.webserver]
command = "uvicorn src.main:app --port 3000"
port = 3000
```

## 安装步骤

### 1. 创建虚拟环境

```bash
python3.11 -m venv .venv
source .venv/bin/activate
```

### 2. 安装依赖

```bash
pip install -r requirements.txt
```

### 3. 安装 Playwright 浏览器

```bash
playwright install --with-deps chromium
```

### 4. 验证安装

```bash
# 验证 Python
python --version

# 验证 pytest
pytest --version

# 验证 Playwright
playwright --version
```

## CLAUDE.md

```markdown
# 项目开发规范

## 技术栈
- 后端：Python 3.11 + FastAPI
- 测试：pytest（单元）+ Playwright（E2E）
- 环境：virtualenv

## 开发流程
1. @agent-backend 实现接口
2. @agent-tester 编写测试
3. 本地验证通过
4. git commit

## 测试要求
- 单元测试覆盖率 ≥ 80%
- E2E 测试覆盖核心用户路径
- 失败测试有详细日志和截图
```

## GitHub Actions 集成

### .github/workflows/test.yml

```yaml
name: Tests

on:
  push:
    branches: [main]
  pull_request:

jobs:
  test:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4

      - name: Set up Python
        uses: actions/setup-python@v5
        with:
          python-version: "3.11"

      - name: Install dependencies
        run: |
          pip install -r requirements.txt
          playwright install --with-deps chromium

      - name: Run unit tests
        run: |
          python -m pytest tests/unit/ --cov --cov-report=xml

      - name: Run E2E tests
        run: |
          playwright test

      - name: Upload coverage
        uses: codecov/codecov-action@v3
```

## 测试最佳实践

### pytest 单元测试

```python
# tests/unit/test_auth.py
import pytest
from src.api.auth import login

def test_login_success():
    """测试正常登录"""
    result = login("user@example.com", "password123")
    assert result["success"] is True
    assert "token" in result

def test_login_wrong_password(mocker):
    """测试密码错误"""
    mocker.patch("src.api.auth.verify_password", return_value=False)
    result = login("user@example.com", "wrong")
    assert result["success"] is False
    assert result["error"] == "Invalid password"

@pytest.mark.parametrize("email", ["", "invalid", "test@test"])
def test_login_invalid_email(email):
    """测试邮箱格式验证"""
    result = login(email, "password")
    assert result["success"] is False
```

### Playwright E2E 测试

```python
# tests/e2e/test_user_flow.py
from playwright.sync_api import Page, expect

def test_complete_user_flow(page: Page):
    """测试完整用户流程：注册 -登录 -操作 -登出"""

    # 1. 注册
    page.goto("http://localhost:3000/register")
    page.fill('[name="email"]', "test@example.com")
    page.fill('[name="password"]', "password123")
    page.click('[type="submit"]')
    expect(page).to_have_url("http://localhost:3000/login")

    # 2. 登录
    page.fill('[name="email"]', "test@example.com")
    page.fill('[name="password"]', "password123")
    page.click('[type="submit"]')
    expect(page.locator("h1")).to_contain_text("Dashboard")

    # 3. 创建项目
    page.click("text=New Project")
    page.fill('[name="name"]', "Test Project")
    page.click("button:has-text('Create')")
    expect(page.locator(".project-name")).to_have_text("Test Project")

    # 4. 登出
    page.click("text=Logout")
    expect(page).to_have_url("http://localhost:3000/login")
```

## 常见问题

**Q: Playwright 浏览器安装失败？**

A: 使用 `playwright install --with-deps chromium` 安装系统依赖

**Q: 测试超时怎么办？**

A: 在 `playwright.config.toml` 中增加 `timeout` 值

**Q: 如何只运行单个测试？**

A:

```bash
# pytest 单个文件
pytest tests/unit/test_auth.py

# pytest 单个测试
pytest tests/unit/test_auth.py::test_login_success

# Playwright 单个文件
playwright test tests/e2e/test_login.py

# Playwright 单个测试
playwright test tests/e2e/test_login.py:14
```

## 相关指南

- [settings.json 配置](./settings-json.md)
- [Git 工作流配置](./git-workflow.md)
- [两阶段工作流](./two-phase-workflow.md)
