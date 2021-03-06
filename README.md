ThinkPHP Swoole 扩展
===============

## 安装

首先按照Swoole官网说明安装swoole扩展，然后使用
~~~
composer require tinymeng/think-swoole dev-tinymeng -vvv
~~~
安装swoole扩展。

## 使用方法


直接在命令行下启动HTTP服务端。

~~~
php think swoole
~~~

启动完成后，默认会在0.0.0.0:80启动一个HTTP Server，可以直接访问当前的应用。

swoole的相关参数可以在`config/swoole.php`里面配置（具体参考配置文件内容）。

如果需要使用守护进程方式运行，可以配置

~~~
'options'   =>  [
    'daemonize' =>  true
]
~~~

支持的操作包括
~~~
php think swoole [start|stop|reload|restart]
~~~

tinymeng  新增请求

通过http主动发送到socket

修改配置文件,添加 httpRequest 参数

 ```
     'websocket'  => [
        'enable'        => true,
        'handler'       => SocketHandler::class,
        'httpRequest'   => WebsocketMessage::class,//监听onRequest回调
        'parser'        => Parser::class,
        'ping_interval' => 25000,
        'ping_timeout'  => 60000,
        'room'          => [],
        'listen'        => [],
        'subscribe'     => [],
    ],
 ```

