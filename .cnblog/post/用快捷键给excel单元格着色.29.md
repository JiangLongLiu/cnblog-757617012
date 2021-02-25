<p><br></p><p>为了避免频繁的鼠标和键盘之间的切换，所以参考了网上的<a href="https://jingyan.baidu.com/article/215817f72feb615eda1423ac.html" target="_blank">方法</a>。</p><p>遇见问题 1 <a href="https://zhidao.baidu.com/question/137331184366987605.html">https://zhidao.baidu.com/question/137331184366987605.html</a></p><p>遇建问题2 <a href="https://jingyan.baidu.com/article/ca41422f121c771eaf99ed10.html">https://jingyan.baidu.com/article/ca41422f121c771eaf99ed10.html</a></p><p><br></p><p>录制宏之后，文件类型也应当发生改变，&nbsp; 改成了 .xlsm</p><div class="cnblogs_code" style="padding: 5px; border: 1px solid rgb(204, 204, 204); border-image: none; background-color: rgb(245, 245, 245);"><pre><span style="color: rgb(0, 0, 255);">Sub</span><span style="color: rgb(0, 0, 0);"> 单元格着色()
</span><span style="color: rgb(0, 128, 0);">'
'</span><span style="color: rgb(0, 128, 0);"> 单元格着色 宏</span><span style="color: rgb(0, 128, 0);">
'
'</span><span style="color: rgb(0, 128, 0);"> 快捷键: Ctrl+q</span><span style="color: rgb(0, 128, 0);">
'
</span>    <span style="color: rgb(0, 0, 255);">With</span><span style="color: rgb(0, 0, 0);"> Selection.Interior
        .Pattern </span>=<span style="color: rgb(0, 0, 0);"> xlSolid
        .PatternColorIndex </span>=<span style="color: rgb(0, 0, 0);"> xlAutomatic
        .ThemeColor </span>=<span style="color: rgb(0, 0, 0);"> xlThemeColorDark1
        .TintAndShade </span>= -<span style="color: rgb(128, 0, 128);">4.99893185216834E-02</span><span style="color: rgb(0, 0, 0);">
        .PatternTintAndShade </span>= <span style="color: rgb(128, 0, 128);">0</span>
    <span style="color: rgb(0, 0, 255);">End</span> <span style="color: rgb(0, 0, 255);">With</span>
<span style="color: rgb(0, 0, 255);">End Sub</span></pre><pre><span style="color: rgb(0, 0, 255);"><br></span></pre><pre><span style="color: rgb(0, 0, 255);"><br></span></pre><pre><span style="color: rgb(0, 0, 255);"><br></span></pre></div>