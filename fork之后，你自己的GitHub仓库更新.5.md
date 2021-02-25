<p>相信吾爱很多小伙伴用过BILIBILI-HELPER，<br>有没有用了几天后，项目连续报错？<br>原因： 项目代码旧了，需要更新<br>更新方法：<br>1.fork仓库后，将你的仓库拉到本地，如果没有源头仓库，则添加源头仓库<br>&nbsp;&nbsp;&nbsp; git remote add upstream https://github.com/JunzhouLiu/BILIBILI-HELPER.git<br>2.更新上游仓库main分支的代码（pull操作实际上是 fetch+merge）<br>&nbsp;&nbsp;&nbsp;&nbsp; git pull upstream main<br>3. 将从源头仓库更新后的代码推送到你自己的github仓库<br>&nbsp;&nbsp;&nbsp;&nbsp; git push origin main<br>这样你就能快速的从我的仓库拉取最新的代码，并更新到你自己的仓库里了。自定义配置的同学，要注意config.json 不要被我的文件覆盖了。<br>如果你提交代码太慢，可以考虑git挂代{过}{滤}理，git 加代{过}{滤}理的方法是<br>git config --global https.proxy https://代{过}{滤}理服务IP:端口<p>取消，则是<p>git config --global --<strong><font style="background-color: rgb(255, 255, 0);">unset</font></strong> https.proxy</p><p><br></p><p><br></p><p><hr></p><h1>以上介绍的是<a href="https://github.com/JiangLongLiu/BILIBILI-HELPER#%E6%89%8B%E5%8A%A8%E6%8B%89%E5%8F%96%E6%9C%80%E6%96%B0%E4%BB%A3%E7%A0%81" target="_blank">手动方式</a>，当然会有自动方式(两种)：</h1><h4>更新和帮助</h4><h2>1.使用 Github Actions 自动同步源仓库代码</h2><p>参阅<a href="https://github.com/JunzhouLiu/BILIBILI-HELPER/issues/8">Issue8 使用GitHub Actions任务自动同步源仓库代码</a><div class="cnblogs_code" style="padding: 5px; border: 1px solid rgb(204, 204, 204); border-image: none; background-color: rgb(245, 245, 245);"><pre>该方案来自 @happy888888 #<span style="color: rgb(128, 0, 128);">6</span><span style="color: rgb(0, 0, 0);"> ，由于本操作会覆盖用户自己的config.json配置文件，所以暂时没有合并到main分支，所以请使用自定义功能的朋友请慎用。

在.</span>/github/<span style="color: rgb(0, 0, 0);">workflows目录下创建auto_merge.yml文件，内容如下

name: auto_merge

on:
  workflow_dispatch:
  schedule:
    </span>- cron: <span style="color: rgb(128, 0, 128);">0</span> <span style="color: rgb(128, 0, 128);">8</span> * *<span style="color: rgb(0, 0, 0);"> fri
    # cron表达式,每周五16点执行一次，actions任务时区为UTC时区。 


jobs:
  merge:
    runs</span>-on: ubuntu-<span style="color: rgb(0, 0, 0);">latest
    steps:
    </span>-<span style="color: rgb(0, 0, 0);"> name: Checkout
      uses: actions</span>/<span style="color: rgb(0, 0, 0);">checkout@v2
      with:
        ref: main
        fetch</span>-depth: <span style="color: rgb(128, 0, 128);">0</span><span style="color: rgb(0, 0, 0);">
        lfs: </span><span style="color: rgb(0, 0, 255);">true</span>

    -<span style="color: rgb(0, 0, 0);"> name: Set git identity
      run : </span>|<span style="color: rgb(0, 0, 0);">
        git config </span>--global user.email <span style="color: rgb(128, 0, 0);">"</span><span style="color: rgb(128, 0, 0);">41898282+github-actions[bot]@users.noreply.github.com</span><span style="color: rgb(128, 0, 0);">"</span><span style="color: rgb(0, 0, 0);">
        git config </span>--global user.name <span style="color: rgb(128, 0, 0);">"</span><span style="color: rgb(128, 0, 0);">github-actions[bot]</span><span style="color: rgb(128, 0, 0);">"</span>
    -<span style="color: rgb(0, 0, 0);"> name: Load upstream commits
      run: </span>|<span style="color: rgb(0, 0, 0);">
        git update</span>-index --assume-unchanged ./src/main/resources/<span style="color: rgb(0, 0, 0);">config.json
        git pull https:</span><span style="color: rgb(0, 128, 0);">//</span><span style="color: rgb(0, 128, 0);">github.com/JunzhouLiu/BILIBILI-HELPER.git --log --no-commit</span>
    -<span style="color: rgb(0, 0, 0);"> name: Apply commit changes
      run: </span>|

        <span style="color: rgb(0, 0, 255);">if</span> [ -f ./.git/MERGE_MSG ]; <span style="color: rgb(0, 0, 255);">then</span>
        <span style="color: rgb(0, 0, 255);">mkdir</span> ./tmp &amp;&amp; <span style="color: rgb(0, 0, 255);">cp</span> ./.git/MERGE_MSG ./tmp/<span style="color: rgb(0, 0, 0);">message
        </span><span style="color: rgb(0, 0, 255);">sed</span> -i <span style="color: rgb(128, 0, 0);">"</span><span style="color: rgb(128, 0, 0);">1c [bot] AutoMerging: merge all upstream's changes:</span><span style="color: rgb(128, 0, 0);">"</span> ./tmp/<span style="color: rgb(0, 0, 0);">message
        </span><span style="color: rgb(0, 0, 255);">sed</span> -i <span style="color: rgb(128, 0, 0);">'</span><span style="color: rgb(128, 0, 0);">/^\#.*/d</span><span style="color: rgb(128, 0, 0);">'</span> ./tmp/<span style="color: rgb(0, 0, 0);">message
        git commit </span>--<span style="color: rgb(0, 0, 255);">file</span>=<span style="color: rgb(128, 0, 0);">"</span><span style="color: rgb(128, 0, 0);">./tmp/message</span><span style="color: rgb(128, 0, 0);">"</span>
        <span style="color: rgb(0, 0, 255);">else</span>
        <span style="color: rgb(0, 0, 255);">echo</span> <span style="color: rgb(128, 0, 0);">"</span><span style="color: rgb(128, 0, 0);">There is no merge commits.</span><span style="color: rgb(128, 0, 0);">"</span>
        <span style="color: rgb(0, 0, 255);">fi</span>
    -<span style="color: rgb(0, 0, 0);"> name: Push Commits
      </span><span style="color: rgb(0, 0, 255);">env</span><span style="color: rgb(0, 0, 0);">:
        DOWNSTREAM_BRANCH: main
        TZ: Asia</span>/<span style="color: rgb(0, 0, 0);">Shanghai
      run: git push origin $DOWNSTREAM_BRANCH</span></pre></div><h2>2. 使用Pull APP［推荐］</h2><p>参阅 <a href="https://github.com/apps/pull">Pull APP</a>&nbsp; <blockquote><p>a GitHub App that keeps your forks up-to-date with upstream via automated pull requests.</p></blockquote>