# 模板格式
规范使用较多的是 Angular 团队的规范，格式如下：

    <type>(<scope>): <subject>
    // 空出一行
    <body>
    // 空出一行
    <footer>
type: （必填）

    feat: 新特性
    fix: 修改问题
    refactor: 代码重构
    docs: 文档修改
    style: 代码格式化的修改如缩进/去空格/增删分号, 注意不是 css 修改
    test: 测试用例修改
    chore: 不修改src或者test的其他修改, 比如构建流程, 依赖管理.
    perf: 提高性能的改动
    ci: 与CI持续集成的服务的有关改动
scope: （选填）

    commit 影响的范围, 比如: route, component, utils, build…
subject: （必填）

    提交简述
body: （选填）

    commit 具体修改内容
    可以分为多行
footer: （选填）

    一些备注（选填）
    通常是 BREAKING CHANGE 或修复的 bug 的链接.

# 设置模板
## 修改全局配置
在git全局配置里进行设置
linx/mac 进入文件.gitconfig
windows 进入C:\Users\Microsoft\.gitconfig
    
    $ vi ~/.gitconfig
    1
    若不存在[commit] template，则设置如下
    
    [commit]
    template = C:\Users\Microsoft\.gitCommitTemplate
## 修改模板
设置模板完毕后，下一步进行模板内容的修改

    $ vi  C:\Users\Microsoft\.gitCommitTemplate
粘入以下内容保存即可。若使用sourcetree等git管理软件，则需要重启软件才能生效。

    <feat>(<>): <提交描述>
    
    <body>
    
    <footer>
    
    # - type: 
    feat(新特性), 
    fix(修改问题), 
    docs(文档修改), 
    style(代码格式修改, 注意不是 css 修改), 
    refactor(代码重构), 
    test(测试), 
    chore(其他修改, 比如构建流程, 依赖管理)
    # - scope: (可以为空)
    影响的的范围
    # - subject
    提交描述
版权声明：本文为CSDN博主「GuoyeZhang」的原创文章，遵循 CC 4.0 BY-SA 版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/aa390481978/article/details/89314113