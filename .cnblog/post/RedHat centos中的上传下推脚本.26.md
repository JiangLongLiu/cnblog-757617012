<ul><li><h2>上传</h2></li></ul><div class="cnblogs_code" style="padding: 5px; border: 1px solid rgb(204, 204, 204); border-image: none; background-color: rgb(245, 245, 245);"><pre>ftp -v -n <span style="color: rgb(128, 0, 128);">192.168</span>.<span style="color: rgb(128, 0, 128);">1.100</span>&lt;&lt;END   <span style="color: rgb(0, 128, 0);">//</span><span style="color: rgb(0, 128, 0);">上传服务器</span>
<span style="color: rgb(0, 0, 0);">user root  root123    

cd   </span>/home/test/test123    <span style="color: rgb(0, 128, 0);">//</span><span style="color: rgb(0, 128, 0);">上传 目录</span>
lcd  /home/test/test234  <span style="color: rgb(0, 128, 0);">//</span><span style="color: rgb(0, 128, 0);">本地目录</span>
prompt  <span style="color: rgb(0, 128, 0);">//</span><span style="color: rgb(0, 128, 0);">多个文件</span>
mput *  <span style="color: rgb(0, 128, 0);">//</span><span style="color: rgb(0, 128, 0);">所有</span>
<span style="color: rgb(0, 0, 0);">close
END</span></pre></div><ul><li><h2>下推</h2></li></ul><div class="cnblogs_code" style="padding: 5px; border: 1px solid rgb(204, 204, 204); border-image: none; background-color: rgb(245, 245, 245);"><pre>ftp -v -n <span style="color: rgb(128, 0, 128);">192.168</span>.<span style="color: rgb(128, 0, 128);">1.100</span>&lt;&lt;<span style="color: rgb(0, 0, 0);">END
user test  test

cd  </span>/test/<span style="color: rgb(0, 0, 0);">backup_test
lcd </span>/home/<span style="color: rgb(0, 0, 0);">test
prompt
mget </span>*<span style="color: rgb(0, 0, 0);">
close
END</span></pre></div>