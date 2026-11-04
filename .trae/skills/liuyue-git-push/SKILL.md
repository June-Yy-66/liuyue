---
name: "liuyue-git-push"
description: "Commits and pushes the d:\June_css project to GitHub remote git@github.com:June-Yy-66/liuyue.git via SSH. Invoke when user asks to commit, push, or sync this project to GitHub."
---

# 提交并推送项目到 GitHub

将 d:\June_css 项目提交 commit 并 push 到远程仓库 https://github.com/June-Yy-66/liuyue.git（SSH 地址：git@github.com:June-Yy-66/liuyue.git）。

## 执行步骤

1. **前置检查**（在 d:\June_css 目录下执行）：
   ```powershell
   git status
   git remote -v
   ```

2. **配置远程仓库**（若 remote 不存在或地址不对）：
   ```powershell
   git remote add origin git@github.com:June-Yy-66/liuyue.git
   ```
   若已存在但地址错误：
   ```powershell
   git remote set-url origin git@github.com:June-Yy-66/liuyue.git
   ```

3. **验证 SSH 连接**（使用已配置的公钥 id_ed25519）：
   ```powershell
   ssh -T git@github.com
   ```
   - 成功标志：返回 `Hi June-Yy-66! You've successfully authenticated...`
   - 若失败：提示用户确认公钥已添加到 GitHub 账户（Settings → SSH and GPG keys）

4. **确认 git 身份**（若未配置则使用用户邮箱）：
   ```powershell
   git config user.name
   git config user.email
   ```
   若为空：
   ```powershell
   git config user.name "June-Yy-66"
   git config user.email "2912027133@qq.com"
   ```

5. **提交所有变更**：
   ```powershell
   git add -A
   git commit -m "update: <根据实际变更内容生成简短中文描述>"
   ```

6. **推送到远程**：
   - 首次推送：
     ```powershell
     git push -u origin master
     ```
   - 后续推送：
     ```powershell
     git push
     ```
   - 若远程分支为 main：使用 `git push -u origin main`（先用 `git branch` 确认分支名）

## 注意事项

- 私钥位于 C:\Users\Administrator\.ssh\id_ed25519，绝不能提交到仓库或外泄
- 若推送被拒绝（rejected），先执行 `git pull --rebase origin master` 再推送
- 若提示 unknown host，首次连接输入 yes 信任 github.com 即可
- 提交信息使用中文简短描述本次变更内容
