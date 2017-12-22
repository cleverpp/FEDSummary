## 基础前提
1. Promise  （http://es6.ruanyifeng.com/#docs/promise）
2. Fetch API  （https://developer.mozilla.org/zh-CN/docs/Web/API/Fetch_API/Using_Fetch）
3. Service Worker （https://developer.mozilla.org/zh-CN/docs/Web/API/Service_Worker_API）
4. Cache Storage API （）
5. Push API （https://developer.mozilla.org/zh-CN/docs/Web/API/Push_API）
6. Notification API （https://developer.mozilla.org/zh-CN/docs/Web/API/notification）


## 哇哈哈抽奖
1. 要求https环境，如果是http则只能是 localhost  | 127.0.0.1
2. 启动pwa的http环境：open -a /Applications/Google\ Chrome.app --args --user-data-dir  --unsafety-treat-insecure-origin-as-secure   【该命令本机验证无效】
3. 演示离线缓存
4. 演示add to home screen
5. 演示离线页面
6. 演示推送通知
7. 消息订阅
    1. 需要进行订阅ServiceWorkerRegistration.pushManager.subscribe 、 
    2. service worker 需要监听push事件
    3. 需要一个订阅应用服务器（https://web-push-codelab.glitch.me/） 【npm install -g web-push】


## [第一个PWA](https://developers.google.com/web/fundamentals/codelabs/your-first-pwapp/?hl=zh-cn)
1. 构建App Shell（可以理解为不需要调用后台的UI组件，以便能超快启动）
2. 服务工作线程（service worker）
    1. 注册register
    2. install事件（安装时缓存必要的资源）
    3. activate事件（激活时管理缓存，例如删除旧缓存、更新缓存等）
    4. fetch事件（拦截请求）
3. 缺点：
    1. 务必在每次发生内容更改时更改缓存键
    2. 每次发生更改时重新下载所有内容
    3. 浏览器缓存可能阻止服务工作线程缓存更新（即服务工作线程被缓存了！）
    4. 缓存优先策略产生的副作用：部署的网站极难更新！
    5. 解决方案：第三方库sw-precache【未研究】
4. Add to Home Screen
    1. manifest.json
    2. <link rel="manifest" href="/manifest.json">
    3. 准备好icons
    4. 对于有些设备需要打开‘添加到屏幕’的权限，例如华为
5. 需要部署到支持https的服务器上

## [调试服务工作线程](https://developers.google.com/web/fundamentals/codelabs/debugging-service-workers/?hl=zh-cn)
1. sevice worker 的浏览器支持情况：https://jakearchibald.github.io/isserviceworkerready/
2. 开发时可用localhost（或127.0.0.1)， 部署到测试环境、生产环境必须要使用https
3. 部署HTTPS的托管主机：firebase、github pages
4. chrome://inspect/#service-workers
5. Service worker的作用域：服务工作线程注册的默认作用域是与脚本网址相对的 ./。 这意味着如果您在 //example.com/foo/bar.js 注册一个服务工作线程，则它的默认作用域为 //example.com/foo/。
6. 更新service worker：如果你的 service worker 已经被安装，但是刷新页面时有一个新版本的可用，新版的 service worker 会在后台安装，但是还没激活。当不再有任何已加载的页面在使用旧版的 service worker 的时候，新版本才会激活。一旦再也没有更多的这样已加载的页面，新的 service worker 就会被激活。
7. 调试：debugger、断点

## [向网络应用添加推送通知](https://developers.google.com/web/fundamentals/codelabs/push-notifications/?hl=zh-cn)
1. 注册服务工作线程
2. 获取应用服务器密钥，并订阅用户：
3. service worker 处理push事件
4. service worker 处理notificationclick事件
5. 发送推送消息：一般情况下，这个过程就是从网页向后端发送订阅，然后后端通过对订阅中的端点实施 API 调用，进而触发推送消息
6. 取消订阅
