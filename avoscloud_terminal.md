  Usage: avoscloud [选项] <命令> 

  有效的命令列表包括: 
    add <app>                   添加一个应用
    app [list]                  显示当前应用，deploy、status 等命令运行在当前应用上，如果加上 list ，则显示所有的应用信息。
    checkout <app>              切换到一个应用，deploy、status 等命令将运行在该应用上。
    clear                       清除本地状态，在输入 app id 或者 master key 错误的情况下使用。
    cql                         进入 CQL 查询交互
    deploy                      部署云代码到云引擎平台开发环境
    lint                        静态检查代码错误
    logs                        查看云代码日志
    new                         创建云代码项目
    publish                     发布开发环境代码到生产环境
    redis                       LeanCache Redis 命令行
    rm <app>                    移除一个应用
    search <keyword>            根据关键字查询开发文档
    status                      查询当前部署状态
    undeploy                    从云引擎平台清除云代码部署，包括生产环境和开发环境。
    upload <file-or-directory>  导入文件到 LeanCloud 平台，如果是目录，则会将该目录下的文件递归导入。

  Options:

    -d, --debug                 启用 Debug 模式，参见 https://nodejs.org/api/debugger.html。
    -f, --filepath <path>       本地云代码项目根路径，默认是当前目录。
    -g, --git                   使用定义在管理平台的 git 仓库或者 -u 指定的 git 仓库部署云代码，默认使用本地代码部署。
    -h, --help                  显示帮助信息
    -l, --local                 使用本地代码部署云代码，该选项是默认选中。
    -n, --lines <lines>         查看多少行最新的云代码日志，默认 10 行。
    -o, --log <log>             本次部署的提交日志，仅对从本地部署有效。
    -P, --port <port>           指定本地调试的端口，默认 3000。
    -p, --project <app>         命令运行在指定应用上，默认运行在当前应用或者 origin 应用上。
    -r, --revision <revision>   git 的版本号，仅对从 git 仓库部署有效。
    -t, --tailf                 自动刷新云代码日志，结合 logs 命令使用。
    -V, --version               显示版本信息
