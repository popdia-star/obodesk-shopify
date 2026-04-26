OboDesk Shopify 日常开发流程

1. 启动本地预览
cd D:\My-AiOS\10_Workspace\WORK\shopify-projects\obodesk-shopify\theme\obodesk-theme
shopify theme dev --store obo-5.myshopify.com

2. 打开浏览器预览
http://127.0.0.1:9292

3. 另开一个 PowerShell 启动 Codex
cd D:\My-AiOS\10_Workspace\WORK\shopify-projects\obodesk-shopify
codex

4. 给 Codex 的安全指令
先不要修改任何文件。请先分析并列出你准备修改哪些文件，等我确认后再执行。

5. Codex 修改后检查主题
cd D:\My-AiOS\10_Workspace\WORK\shopify-projects\obodesk-shopify\theme\obodesk-theme
shopify theme check

6. 浏览器查看效果
http://127.0.0.1:9292

7. Git 查看状态
cd D:\My-AiOS\10_Workspace\WORK\shopify-projects\obodesk-shopify
git status

8. 添加指定文件
git add 文件路径

9. 提交
git commit -m "本次修改说明"

10. 确认干净
git status