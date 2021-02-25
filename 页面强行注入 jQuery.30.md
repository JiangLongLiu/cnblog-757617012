<div class="cnblogs_code" style="padding: 5px; border: 1px solid rgb(204, 204, 204); border-image: none; background-color: rgb(245, 245, 245);"><pre>(<span style="color: rgb(0, 0, 255);">function</span><span style="color: rgb(0, 0, 0);">() {
  </span><span style="color: rgb(0, 0, 255);">var</span> hm = document.createElement("script"<span style="color: rgb(0, 0, 0);">);
  hm.src </span>= "http://libs.baidu.com/jquery/2.0.0/jquery.min.js"<span style="color: rgb(0, 0, 0);">;
  </span><span style="color: rgb(0, 0, 255);">var</span> s = document.getElementsByTagName("title")[0<span style="color: rgb(0, 0, 0);">]; 
  s.parentNode.insertBefore(hm, s);
})();</span></pre></div>