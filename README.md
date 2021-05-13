#   新建站点

    hugo new site meBlog

#   进入站点目录

    cd LearnStack

#   安装皮肤

    git clone git@gitee.com:clin003/LoveIt.git themes/LoveIt


#   新建页面

    hugo new about.md

#   新建文章

    hugo new posts/xxx.md

#   本地测试命令

    hugo server

#   发布方法1:

    hugo --baseUrl="https://3ae.cn/"

#   发布方法2:

    hugo