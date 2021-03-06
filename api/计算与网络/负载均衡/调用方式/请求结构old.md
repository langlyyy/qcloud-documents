## 服务地址
腾讯云负载均衡（CLB）使用的域名访问地址为：lb.api.qcloud.com。

## 通信协议
腾讯云 API 的所有接口均通过 HTTPS 进行通信，提供高安全性的通信通道。

## 请求方法
同时支持 POST 和 GET 请求，需要注意不能混合使用。即如果使用 GET 方式，则参数均从 Querystring 取得；如果使用 POST 方式，则参数均从 Request Body 中取得，Querystring 中的参数将忽略。两种方式参数格式规则相同，一般使用 GET，当参数字符串过长时使用 POST，请见各接口详细描述。

## 字符编码
均使用 UTF-8 编码。


## API 请求结构
<table class="t">
<tbody><tr>
<th> <b>名称</b>
</th><th> <b>描述</b>
</th><th> <b>备注</b>
</th></tr>
<tr>
<td> API 入口
</td><td> API 调用的 WebService 入口
</td><td> https://lb.api.qcloud.com/v2/index.php<br> 
</td></tr>
<tr>
<td> 公共参数
</td><td> 每个接口都包含的通用参数
</td><td> 详见 <a href="/doc/api/244/公共参数" title="公共参数">公共参数</a> 页面
</td></tr>
<tr>
<td> 指令名称
</td><td> API 要执行的指令的名称，这里使用 Action 指定，<br>
<p>例如 Action=CreateLoadBalancer
</p>
</td><td> 完整的指令请参见 <a href="/doc/api/244/API概览" title="API概览">API概览</a>
</td></tr>
<tr>
<td> 指令参数
</td><td> 每个特定的指令需要的参数
</td><td> 详见每个指令的接口文档
</td></tr></tbody></table>
