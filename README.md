# 技术储备

## Node.js
1. NodeJS程序是以单进程形式运行, 可以创建多个子进程用于运行多个实例，负载均衡，提高效率
2. 微服务提高部署效率，不用牵一发动全身。甚至可以使用不同语言开发，独立部署，独立维护，解耦业务
3. Node.js 入门：https://github.com/ElemeFE/node-interview/tree/master/sections/zh-cn
4. Node.js 中文文档：http://nodejs.cn/api/
5. Node.js 中文论坛：https://cnodejs.org/
6. Promise 迷你书 http://liubin.org/promises-book/
7. 深入Promise https://zhuanlan.zhihu.com/p/25178630
8. 获取参数方法：
    1. post       req.body.name
    2. get         req.query.name
    3. url          req.params.name
9. 使用淘宝的源：npm install -g cnpm --registry=https://registry.npm.taobao.org

## Express
1. Express 中文文档：http://expressjs.com/zh-cn/
2. 安装express项目生成器   npm install express-generator -g
3. 安装进程管理器   npm install supervisor -g
4. 创建项目    express --view=ejs myapp
5. 初始化项目   npm install
6. 启动服务   npm start     可以跟端口:  PORT=8888  npm start bin/www
7. 后台进程启动    supervisor bin/www  
8. Express在生产环境下的最佳实践 - 性能和可靠性 https://segmentfault.com/a/1190000004026112
9. 使用Express + MongoDB 搭建多人博客 https://github.com/nswbmw/N-blog
10. 微博实例  https://cnodejs.org/topic/53f23e198f44dfa35129c43b
11. pug 模板教程：https://github.com/pugjs/pug-zh-cn/blob/master/Readme_zh-cn.md

## Express-session
1. 官网：https://github.com/expressjs/session/blob/master/README.md
2. 安装：npm install express-session
3. session的store：https://github.com/tj/connect-redis


## Passport
1. 官网    http://passportjs.org/docs
2. 安装   npm install passport
3. 配置    http://passportjs.org/docs/configure
    - strategy
    - middleware
    - serializeUser
    - deserializeUser
    - passport.authenticate
    - req.isAuthenticated()
    - req.logout()
    - req.user


## Mocha
1. 官网：http://mochajs.org/#installation


## JWT


## Koa


## mongodb
1.  官网  https://www.mongodb.com/
2.  mac安装：
    1.  更新 brew update
    2.  brew install mongodb
3.  centos 7 安装：参考：https://www.hugeserver.com/kb/install-mongodb-centos-6-7/，http://blog.topspeedsnail.com/archives/6005
    1.  cd /etc/yum.repos.d/
    2.  vi mongodb-org-3.4.repo
    3. 填入官方的源
        1.  [mongodb-org-3.4]
        2.  name=MongoDB Repository
        3.  baseurl=https://repo.mongodb.org/yum/redhat/$releasever/mongodb-org/3.4/x86_64/
        4.  gpgcheck=1
        5.  enabled=1
        6.  gpgkey=https://www.mongodb.org/static/pgp/server-3.4.asc
    4.  yum repolist
    5.  yum install mongodb-org -y
    6.  创建数据目录： mkdir -p /data/db，可能会提示权限不足，执行：sudo chown -R $USER /data/db
    7.  默认配置文件在 /etc/mongod.conf
4.  启动：mongod 即可
5.  启动后台用户认证： mongod  --auth
6.  数据库用户权限：admin表是管理所有用户的表，
    1.  创建 root 用户，角色为root，用于创建其他用户：
        1.  mongo
        2.  use admin
        3.  db.createUser({user: 'root', pwd: 'codoonhealth', roles:[{role: 'root', db: 'admin'}]})
    2.  创建普通用户，用户是绑定在对应的数据库下的：
        1.  mongo
        2.  use admin
        3.  db.auth('root', 'codoonhealth')
        4.  use account
        5.  db.createUser({user: 'codoonhealth', pwd: 'ch20170801', roles:[{role: 'readWrite', db: 'account'}]})
        6.  db.grantRolesToUser('codoonhealth', [{role: "readWrite", "db": "h5"}])  添加权限
        7.  db.revokeRolesFromUser('codoonhealth', [{role: "readWrite", "db": "h5"}])  删除权限
    3.  登录:
        1.  mongo
        2.  use account
        3.  db.auth('codoonhealth', 'ch20170801')


## mongoose
1. 官方文档：http://mongoosejs.com/docs/guide.html
2. schema —> model —> entry
3. schema可以自定义一些方法
4. 可以设置虚拟属性virtual，类似于python的@property
5. minimize属性，默认删除掉空对象，节省空间
6. timestamps属性，设置数据添加时间，和最后修改时间
7. new model 之后，需要save保存到数据库，表名默认会加s，
8. validation ，验证器，schema阶段设置
9. population 使用：https://segmentfault.com/a/1190000002727265


## VUE
1. 官网：https://cn.vuejs.org/v2/guide/
2. computed属性多用于缓存数据，虽然可以用method代替，但是method会每次都要计算一遍
3. 为元素添加key属性可以防止vue重复引用这个元素
4. model的修饰符：
    1. lazy：将input更新转到change时触发
    2. number：将用户输入转换成数字
    3. trim：去掉首尾空格
5. 组件推荐命名：小写，中间带一个短杠，my-component
6. 父子组件通信原则：props down，events up
7. vue与express结合：http://southerncross.github.io/2016/02/28/setup-express-vue-boilerplate/
8. vue-cli 使用：http://www.runoob.com/w3cnote/vue2-start-coding.html
9. vue技术栈归纳与精粹 https://uinika.github.io/2017/12/03/web/vue/?hmsr=toutiao.io&utm_medium=toutiao.io&utm_source=toutiao.io


## VUEX
1. 官网：https://vuex.vuejs.org/zh-cn/intro.html
2.  mutations 同步执行，store.commit('increment') 提交
3.  actions 异步执行，store.dispatch('incrementAsync') 提交，最终还是要提交mutations


## Vue-Router
1. 官网：https://router.vuejs.org/zh-cn/


## Vue-Element
1. 官网：http://element.eleme.io/#/zh-CN/component/installation


## Vue-iView
1. 官网：https://www.iviewui.com/docs/guide/install


## WEEX


## Reactjs
1. 官方文档：https://facebook.github.io/react/docs/installation.html
2. 事件绑定   this.handleClick = this.handleClick.bind(this);
3.  民间文档：http://www.zcfy.cc/article/all-the-fundamental-react-js-concepts-jammed-into-this-single-medium-article-4030.html?hmsr=toutiao.io&utm_medium=toutiao.io&utm_source=toutiao.io


## Redux
1. 官方中文文档：http://cn.redux.js.org/index.html
2. 阮一峰系列文档：
    1. http://www.ruanyifeng.com/blog/2016/09/redux_tutorial_part_one_basic_usages.html
    2. http://www.ruanyifeng.com/blog/2016/09/redux_tutorial_part_two_async_operations.html
    3. http://www.ruanyifeng.com/blog/2016/09/redux_tutorial_part_three_react-redux.html
3. 基本概念：
    1. store 用于存放数据，由 createStore 生成
    2. state 包含所有数据，一个state对应一个view
    3. action 是传递消息，view无法直接修改state，store.dispatch(action)是view发出action的唯一方法
    4. reducer 用于处理消息业务，接受两个参数：state，action
    5. combineReducers 方法用于拆分 reducer


## React-Router
1. 中文文档：https://react-guide.github.io/react-router-cn/
2. 阮一峰文档：http://www.ruanyifeng.com/blog/2016/05/react_router.html


## ReactNative


## RxJS
1. http://cn.rx.js.org/

## Sass


## Webpack
1. webpack 入门：http://www.jianshu.com/p/42e11515c10f
2. 官网：https://doc.webpack-china.org/
3. webpack多页架构：https://segmentfault.com/a/1190000006843916
4. webpack 3 https://yangkean.com/blog/2017/8/webpack.html?hmsr=toutiao.io&utm_medium=toutiao.io&utm_source=toutiao.io
5. 深入浅出：http://webpack.wuhaolin.cn/


## gulp


## PM2
1. 安装  npm install pm2 -g 
2. 启动服务  pm2 start bin/www 
3. 服务列表  pm2 list
4. 关闭服务  pm2 stop 0
5. 删除服务  pm2 delete 0
6. 以cluster方式启动   pm2 start bin/www -i 2 --name website
7. 以配置文件方式启动  http://pm2.keymetrics.io/docs/usage/pm2-doc-single-page/
8. 关闭pm2  pm2 kill
9. 官网   http://pm2.keymetrics.io/docs/usage/quick-start/#how-to-update-pm2
10. 开机自启动：
    1. 首先运行node服务  pm2 start bin/www -i 2
    2.  pm2 save
    3.  pm2 startup centos
11. 远程发布：https://segmentfault.com/a/1190000005171229
12. 日志管理： 
    1.  pm2 install pm2-logrotate        https://github.com/pm2-hive/pm2-logrotate#configure
    2.  pm2 set pm2-logrotate:retain 10  设置只保留10个日志
    3.  pm2 set pm2-logrotate:max_size 100M  设置单个文件大小 

## node.js 部署
1. yum install nodejs
2. 添加环境变量 
3. 克隆项目：git clone https://git.coding.net/codoonhealth/ch_node.git
4. 安装pm2：npm install pm2 -g 
5. 安装日志管理工具：pm2 install pm2-logrotate
    1. 设置只保留10个日志：pm2 set pm2-logrotate:retain 10
    2. 设置单个日志文件大小：pm2 set pm2-logrotate:max_size 100M 
6. 进入各个子项目执行：npm install
7. 运行服务：pm2 start pm2.json   此配置文件在各个子项目的根目录下，如果是生产环境需要执行 pm2 start pm2.json --env production，配置详细：
    1. name: "website"           // 项目名称
    2. script: "bin/www"         // 启动脚本
    3. instances: 2                  // 进程数
    4. exec_mode: "cluster"   // 运行模式
    5. error_file: "/var/log/node/website-err.log"     // 错误日志
    6. out_file: "/var/log/node/website-out.log"       // 输出日志
    7. merge_logs: true           // 合并日志
    8. env: {"NODE_ENV": "dev"}                             // 指定开发环境变量
    9. env_production: {"NODE_ENV": "prod"}        // 指定生产环境变量
8. 设置开机自启动：
    1.  重复第4个步骤，开启所有的项目：h5，website，document
    2.  pm2 list  查看服务列表
    3.  pm2 save
    4.  pm2 startup centos
    5.  pm2 unstartup     --取消自动启动
9. 其他命令：
    1. 重启单个应用：pm2 restart website
    2. 重启所有应用：pm2 restart all
    3. 关闭单个应用：pm2 delete website
    4. 杀掉pm2：pm2 kill
    5. 查看各个项目资源占用情况：pm2 monit


## Nginx
1. 官网   http://nginx.org/en/docs/beginners_guide.html
2. nginx 做静态文件处理，负载均衡，虚拟域名

## ES6
1. ES6入门：http://es6.ruanyifeng.com/


## Selenium + phantomjs
1. 爬虫：https://cuiqingcai.com/2577.html
2. 安装phantomjs:
    1.  cnpm install phantomjs 需要翻墙
    2.  cnpm install phantom


## Chromeless


## 微信小程序
1. 官网 https://mp.weixin.qq.com/debug/wxadoc/dev/index.html?t=2017526


## Golang
1. 官网指南：https://tour.go-zh.org/welcome/1
2. go入门：http://wiki.jikexueyuan.com/project/the-way-to-go/preface.html
3. go详细指南：https://github.com/astaxie/build-web-application-with-golang/blob/master/zh/preface.md
4. 指针，go ，channel，select
5. 项目默认新建在  $GOPATH/src/myproject
6. 大写字母开头的变量是可以导出的，即公有，小写字母开头即为私有
7. defer 关键字：相当于python 中的finally
8. 没有类的概念，可以通过添加接受者receive 变相的实现类，通过匿名字段实现继承
9. interface也是可以嵌入


## Gorm
1. 官网：http://jinzhu.me/gorm/


## Gin


## Glide
1. go项目的依赖包管理 ：https://github.com/Masterminds/glide
2. 进入项目中，执行 glide create 命令，会初始化项目生成 glide.yaml
3.  glide get github.com/Masterminds/cookoo  使用此命令安装第三方依赖包，会自动更改 glide.yaml
4.  glide install 安装第三方依赖包到项目目录
5.  以后更新只需要执行 glide update 就行
6.  替源：glide mirror set [original] [replacement]  --vcs git
7.  参考资料：
    1. https://ieevee.com/tech/2017/07/10/go-import.html
    2. https://gocn.io/article/393


## Gopm
1.  https://github.com/gpmgo/gopm
2.  go get -u github.com/gpmgo/gopm  拿到可执行文件
3.  将 上面的可执行文件复制到 $GOPATH/bin ，免得每次使用都要带上全路径
4.  gopm list : 列出依赖包
5.  gopm get -g  github.com/gin-gonic/gin  安装第三方包
6.  gopm build  编译
7.  gopm install 安装
8.  详细文档：https://github.com/gpmgo/docs/blob/master/zh-CN/README.md


## ZooKeeper
1. 官网：https://zookeeper.apache.org/
2. 中文介绍：https://www.ibm.com/developerworks/cn/opensource/os-cn-zookeeper/index.html
3. Zookeeper: 分布式过程协同技术详解 http://www.dengshenyu.com/%E5%88%86%E5%B8%83%E5%BC%8F%E7%B3%BB%E7%BB%9F/2017/11/01/zookeeper.html?hmsr=toutiao.io&utm_medium=toutiao.io&utm_source=toutiao.io
 


## Kafka
1. 官网：https://kafka.apache.org/documentation/#introduction
2. producer  —>  broker —>  customers
3. Kafka 用 Partitions 实现了高并发，Kafka 用 Partitions 复制 + Zookeeper 实现了高可用
4. 快速入门：https://kafka.apache.org/quickstart  里面有下载链接
5. Kafka系列文章：
    1. Kafka背景及架构介绍：http://www.jasongj.com/2015/03/10/KafkaColumn1/
    2. Kafka High Availability （上）：http://www.jasongj.com/2015/04/24/KafkaColumn2/
    3. Kafka High Availability （下）：http://www.jasongj.com/2015/06/08/KafkaColumn3/
    4. Kafka Consumer设计解析：http://www.jasongj.com/2015/08/09/KafkaColumn4/
    5. Kafka性能测试方法及Benchmark报告：http://www.jasongj.com/2015/12/31/KafkaColumn5_kafka_benchmark/
    6. Kafka高性能架构之道：http://www.jasongj.com/kafka/high_throughput/
    7. Kafka Stream：http://www.jasongj.com/kafka/kafka_stream/
6. 起zookeeper服务：bin/zookeeper-server-start.sh config/zookeeper.properties
7. 起kafka服务：bin/kafka-server-start.sh config/server.properties
8. kafka-python包：pip install kafka-python    详解：http://kafka-python.readthedocs.io/en/master/usage.html
9. 配置文件server.properties：
    1. log.retention.hours=168，消息保存时间，对于传统的message queue而言，一般会删除已经被消费的消息，而Kafka集群会保留所有的消息，无论其被消费与否。因为Kafka读取特定消息的时间复杂度为O(1)，即与文件大小无关，所以这里删除过期文件与提高Kafka性能无关。
    2. num.partitions=2，分片个数，Partition机制设置合理，所有消息可以均匀分布到不同的Partition里，这样就实现了负载均衡。如果一个Topic对应一个文件，那这个文件所在的机器I/O将会成为这个Topic的性能瓶颈，而有了Partition后，不同的消息可以并行写入不同broker的不同Partition里，极大的提高了吞吐率。
10. 一个consumer可以有多个线程进行消费，线程数应不多于topic的partition数。
11. Partition数量为Broker数量整数倍时吞吐量明显比其它情况高。
12. Broker 集群，Partition 多扩展，Replica 高可用，Customer 提高吞吐量。Partition个数决定了可能的最大并行度，最好是partition与customer数量相同。
13. CAP理论是指，分布式系统中，一致性、可用性和分区容忍性最多只能同时满足两个。一般而言，都要求保证分区容忍性。所以在CAP理论下，更多的是需要在可用性和一致性之间做权衡。
14. web管理工具：kafka manager
    1. 去 https://github.com/yahoo/kafka-manager 下载最新的release包
    2. 解压出来
    3. 然后 ./sbt clean dist  编译打包，此过程耗时很长估计两小时左右。
    4. 拿到解压包，解压，配置  conf/application.conf ，设置  zookeeper 的地址
    5. bin/kafka-manager -Dconfig.file=conf/application.conf -Dhttp.port=9192  即可启动服务
    6. 打开浏览器 http://127.0.0.1:9000/
    7. 参考资料：http://kaimingwan.com/post/kafka/kafka-managershi-yong-jiao-cheng
15. kafka图表监控: KafkaOffsetMonitor


## Redis
1. keys 列出所有键
2. select index  切换库


## Docker
1.  中文介绍：https://yeasy.gitbooks.io/docker_practice/content/introduction/
2.  基本概念：镜像image、容器Container、仓库Repository
3.  centos安装：https://yeasy.gitbooks.io/docker_practice/content/install/centos.html
4.  mac安装：https://yeasy.gitbooks.io/docker_practice/content/install/mac.html



## Swagger
1. 官网：https://swagger.io/
2. swagger分两块：编辑器editor 与 展示swagger UI
3. 编辑可以下载到本地起服务，也可以使用在线编辑器 http://editor.swagger.io/#/  导出为json 或者 yaml格式就行
4. 下载 https://github.com/swagger-api/swagger-ui ，然后直接进入 /dist/index.html
5. 格式详解：
    1. swagger，指定swagger spec版本，2.0
    2. info，一些描述信息
    3. host，主机，如果没有提供，则使用文档所在的host
    4. basePath，相对于host的路径
    5. tags，补充的元数据，在swagger ui中，用于作为api的分组标签
    6. schemes，API的传输协议，http，https，ws，wss
    7. paths，API的路径
    8. summary，方法名摘要
    9. description，描述
    10. consumes，form传输类型，application/x-www-form-urlencoded，multipart/form-data
    11. produces，MIME类型，application/json，application/xml
    12. parameters，传入参数
        1. in，参数位置，query表示问号结尾，path表示在url中，body表示post，formData
        2. name，参数名称
        3. description，描述
        4. required，是否必填
        5. type，类型  string，int
    13. responses，返回值，可以直接为字符串，也可以设置返回格式
    14. 复用，定义下面三种类型之后即可   用  $ref: "#/definitions/Pet" 方式引用
        1. definitions
        2. parameters
        3. responses
6. 参考资料：
    1. 从入门到精通 https://www.gitbook.com/book/huangwenchao/swagger/details
    2. swagger各个参数详细介绍：https://zhuanlan.zhihu.com/p/21353795



## python 3.6
1. 安装python3，mac下  brew install python3
2. 创建项目步骤：
    1. mkdir  project
    2. cd project
    3.  python3 -m venv virtualenv
    4. source  virtualenv/bin/activate
    5. pip install django
    6. deactivate
3. 参考资料：https://docs.python.org/3/library/venv.html 
4. pip install 指定源：pip install -i https://pypi.doubanio.com/simple/ Keras


## django 1.11.4
1. 官网：https://www.djangoproject.com/
2. pip  install  django
3. django-admin  startproject  mysite
4. 修改settings数据库设置
5. python  manage.py  migrate  会自动新建表
6. python  manage.py  startapp  polls  创建新app
7. 配置settings 添加  ‘polls.apps.PollsConfig’  到 INSTALLED_APPS
8. python  manage.py  makemigrations  polls  会生成migrate中间文件，方便开发者查看
9. python  manage.py  sqlmigrate  polls  0001  会生成对应操作的sql语句
10. python  manage.py  migrate  即可完成数据库的更新
11. 以后更新数据库操作步骤：
    1. 修改model
    2. python  manage.py  makemigrations 
    3. python  manage.py  migrate
12. models 的 __str__ 方法最好写上
13. 自动化测试：
    1. 在 polls/tests.py 文件中新建一个继承 TestCase的类。   from  django.test  import  TestCase
    2. 以 test_开头编写测试用例
    3. python  manage.py  test  polls  查看测试结果
    4. django 会自动创建一个临时数据库，测试完成之后也会自动删除，所有可以随便数据库操作测试
    5. from  django.test  import  Client 。此client可以模拟网页访问，用于测试view
    6. 测试类中添加   setUp  方法可以进行初始化操作，tearDown  方法用于结尾操作，这两个方法，每一次test方法都会执行一次
    7. django 的测试数据库 默认不是utf-8编码，会导致中文报错，需要在settings文件的DATABASES中添加 'TEST': {'CHARSET': 'utf8', 'COLLATION': 'utf8_general_ci'}
14. django 1.5 主要新增内容:
    1. User model 可以定制： https://docs.djangoproject.com/en/1.11/topics/auth/customizing/#auth-custom-user
    2. model.save 方法可以新参数：update_fields=[‘name’, ‘age’] 设置此值将只会更新这些字段，https://docs.djangoproject.com/en/1.11/ref/models/instances/#specifying-which-fields-to-save
    3. 新增StreamingHttpResponse
15. django 1.6 主要新增内容
    1. settings文件新增数据库连接复用属性 CONN_MAX_AGE，默认关闭  https://docs.djangoproject.com/en/1.11/ref/databases/#persistent-database-connections
    2. 新增 BinaryField 
    3. 事务 https://docs.djangoproject.com/en/1.11/topics/db/transactions/
    4. 使用 with transaction.atomic()  将代码块包起来，即可实现自动事务
16. django 1.7 主要新增内容
    1. migrate，自动同步数据库的修改，取代syncdb
    2. 自定义对象序列化方法 deconstruct https://docs.djangoproject.com/en/1.11/topics/migrations/#migration-serializing
    3. 自定义query_set ，让model使用起来更加面向对象化  https://docs.djangoproject.com/en/1.11/topics/db/managers/#create-manager-with-queryset-methods
    4. 自定义manager
    5. prefetch_related 方法 https://docs.djangoproject.com/en/1.11/ref/models/querysets/#django.db.models.query.QuerySet.prefetch_related
17. django 1.8 主要新增内容 
    1. 新的模板引擎 jinja2
    2. 新增 UUIDField，DurationField  貌似都是为PostgreSQL准备的
    3. 复杂查询  https://docs.djangoproject.com/en/1.11/ref/models/conditional-expressions/
    4. 新增TestCase.setUpTestData() 方法
18. django 1.9 主要新增内容
    1. 事务回调函数  on_commit(), 在事务中添加 transaction.on_commit(do_somthing) ，事务正确提交以后会执行绑定的do_somthing方法
    2. 密码验证中间件
19. diango 1.11 主要新增功能
    1. subquery  子查询  https://docs.djangoproject.com/en/1.11/ref/models/expressions/#django.db.models.Subquery
20. uwsgi测试
    1.  pip  install  uwsgi
    2.  uwsgi --http :8001 --module mysite.wsgi -p 4
    3.  即可访问  http://127.0.0.1/8001
21. 代码覆盖率测试：
    1.  pip  install  coverage
    2.  coverage  run  --source='.'  manage.py  test
    3.  coverage report -m
22. django 时区问题：http://www.jianshu.com/p/c1dee7d3cbb9
23. pytz使用：http://www.dannysite.com/blog/122/
    1.  datetime.datetime.fromtimestamp(1503480591.0)
    2.  time.mktime(datetime.datetime.now().timetuple())
24.  django-debug-toolbar 插件查看慢查询


## django 部署
1.  gunicorn -b127.0.0.1:8001 -kgevent -w4 mysite.wsgi
2.  uwsgi --ini uwsgi.ini --http :8001 --pidfile /tmp/uwsgi.pid
3.  kill -HUP `cat /tmp/uwsgi.pid`    或者    kill -s QUIT `cat /tmp/uwsgi.pid`
4.  uwsgi --reload /tmp/uwsgi.pid


## Git
1. git rm --cached xxx.xx    排除已经跟踪的文件
2. git stash  此命令会将当前分支修改的文件临时保存起来
3. git stash pop  取回保存起来的修改
4. git reset HEAD 如果后面什么都不跟的话 就是上一次add 里面的全部撤销了, 可以跟单独的文件
5. 免密pull  执行命令： git config --global credential.helper cache   或者   git config --global credential.helper "cache --timeout=3600"
6. git config --unset --global credential.helper 取消密码
7. store 之后会存储在 .git_credential  文件下, 删掉即可， mac下要到 钥匙串访问下面删除
8. github 客户端升级:  https://ehlxr.me/2016/07/30/CentOS-7-安装最新的-Git/
9. github 升级之后，pull 报错 SSL 不正确，centos 6 下   执行 yum update -y nss curl libcurl
10. git branch -d branch-name 删除本地分支
11. git branch -dr origin/branch-name 删除远程分支
12. git push origin :branch-name  推送一个空的分支 删除掉远程分支


## wkhtmltopdf
1. yum install wkhtmltopdf
2. yum install xorg-x11-server-Xvfb
3. echo -e '#!/bin/bash\nxvfb-run -a --server-args="-screen 0, 1024x768x24" /usr/bin/wkhtmltopdf -q $*' > /usr/bin/wkhtmltopdf.sh
4. chmod a+x /usr/bin/wkhtmltopdf.sh
5. ln -s /usr/bin/wkhtmltopdf.sh /usr/local/bin/wkhtmltopdf
6. wkhtmltopdf http://www.baidu.com output.pdf
7. 中文乱码问题：找到windows里的宋体  C:\Windows\Fonts\simsun.tcc，然后上传到服务器 /usr/share/fonts/chinese/TrueType/simsun.ttc
8. 参数：https://wkhtmltopdf.org/usage/wkhtmltopdf.txt


## Mysql
1.  create database db_name DEFAULT CHARACTER SET utf8 COLLATE utf8_general_ci;
2.  CREATE DATABASE <dbname> CHARACTER SET utf8;
3.  ALTER TABLE knowledge_category CONVERT TO CHARACTER SET utf8 COLLATE utf8_general_ci;
4.  ALTER DATABASE knowledge CHARACTER SET utf8;
5.  导出数据： 
    1.  mysqldump -uorange -porange20150611 -horange_db0 account_qfpay > account.sql
    2.  mysqldump -uroot -pCh_2017_666 -h192.168.11.111 --databases ch_w_knowledge --tables knowledge_article > knowledge_article.sql
6.  压缩数据：tar -czf www.tar.gz www.sql
7.  从远程服务器获取文件： scp root@www.3-10.cc:/root/www.tar.gz  /workspace
8.  往远程服务器传送文件     scp knowledge_article.sql root@python0.codoonhealth.com:/root 
9.  解压数据：tar -xzf www.tar.gz
10.  导入数据：source www.sql
11.  安装mysql未设置密码时候，mysql会随机生成一个密码：sudo grep 'temporary password' /var/log/mysqld.log
12.  登陆进去之后执行： ALTER USER USER() IDENTIFIED BY 'Ch_2017_666';
13.  显示最大连接数：show variables like '%max_connections%';  
14.  显示当前连接信息: show status like 'Threads%';
15.  显示当前进程数： show processlist;
16.  杀掉进程：SELECT concat('KILL ', id, ';') FROM information_schema.processlist WHERE db = 'ch_w_evaluation';


## samba
1.  yum install samba samba-client samba-swat
2.  service smb start
3.  vi /etc/samba/smb.conf
4.  [global]
    1.  workgroup = SAMBA
    2.  map to guest = bad user
5.  [public]
    1.  comment = Documents
    2.  path = /var/samba
    3.  public = Yes
    4.  read only = No
6.  testparm 测试有没有问题
7.  service smb restart

## ssh 远程免密登陆 （mac）
1.  首先执行 ssh-keygen -t rsa  会在当前用户默认目录下生成 id_rsa(私钥) id_rsa.pub(公钥) 这两个文件
2.  将公钥放到对应的服务器  scp  ~/.ssh/id_rsa.pub  root@192.168.11.111:/root/.ssh/
3.  登陆远程服务器，将 .ssh 目录下的公钥追加到 authorized_keys 文件中   cat -n ~/.ssh/id_rsa.pub ~/.ssh/authorized_keys
4.  修改一下权限： chmod 644 ~/.ssh/authorized_keys

## 双系统安装
https://segmentfault.com/a/1190000007215679

## supervisor 
1. 参考：https://leehao.me/%E4%BD%BF%E7%94%A8-Supervisor-%E6%9D%A5%E7%AE%A1%E7%90%86-Redis-%E8%BF%9B%E7%A8%8B/?hmsr=toutiao.io&utm_medium=toutiao.io&utm_source=toutiao.io
2.  运行：supervisord -c /etc/supervisor/supervisord.conf
3. 查看状态：supervisorctl -c /etc/supervisor/supervisord.conf
4.  supervisorctl reload : 载入最新的配置文件，停止原有进程并按新的配置启动、管理所有进程
5.  supervisorctl update : 根据最新的配置文件，启动新配置或有改动的进程，配置没有改动的进程不会受影响而重启
6. 配置文件： priority — 子进程启动关闭优先级，优先级低的，最先启动，关闭的时候最后关闭 默认值为999
7. 当有进程杀不死可以写shell处理
    1.  #!/usr/bin/env bash
    2.  set -e
    3.  if [[ -f "/opt/kafka-manager/RUNNING_PID" ]]; then
    4.      rm "/opt/kafka-manager/RUNNING_PID"
    5.  fi
    6.  /opt/kafka-manager/bin/kafka-manager
8. 设置 stopasgroup = true，killasgroup = true 可以杀死子进程


## linux 常用命令
1.  lsof -i:52000  查看端口
2.  bash -c “sleep 15 && python”  这样可以延迟15秒执行命令
3.  du -d1 -h .  查看当前文件夹大小情况 
4.  添加执行权限：顺序为u文件所有者、g同组用户、o其他用户
    1.  chmod u+x 
    2.  chmod g+x
    3.  chmod o+x
    4. 快捷用法：chmod a+x 添加三组用户
5. 挂载U盘：
    1.  fdisk -l      查看u盘信息
    2.  cd /mnt/    进入mnt目录
    3.  mkdir usb-fat32   新建挂载点
    4.  mount -t vfat /dev/sdb4 /mnt/usb-fat32   挂载U盘
    5.  mount -t vfat -o iocharset=cp936 /dev/sdb4 /mnt/usb-fat32   如果有中文可以用此命令
    6.  ls /mnt/usb-fat32   查看u盘内容
    7.  umount /mnt/usb-fat32   卸载u盘


## Fabric
1. 官网：http://www.fabfile.org/installing.html
2. 中文：http://fabric-chs.readthedocs.io/zh_CN/chs/tutorial.html


## Elasticsearch
1.  权威指南 https://www.elastic.co/guide/cn/elasticsearch/guide/current/index.html


## brew
1. 更新brew自己：brew update
2. 更新所有包：brew upgrade
3. 清理老的包：brew cleanup

## TensorFlow
1. 官方中文文档：http://www.tensorfly.cn/

## 手机端适配
http://www.jianshu.com/p/985d26b40199
http://www.cnblogs.com/lyzg/p/4877277.html
https://github.com/amfe/article/issues/17

## 常用贝塞尔曲线
http://www.cnblogs.com/yansi/p/4012038.html

## 代理服务 shadowsocks
http://vultr.aicnm.com/

## 百度统计用法
https://segmentfault.com/a/1190000002581832

## 图片防盗链破解
页面里用<img src="xxxx" />来引用其他网站的一张图片，但是他的网站设置了防盗链的策略，会在后台判断请求的Referrer属性是不是来自于一个非本域名的网站，如果来源不是本域名就返回403 forbidden。
1. 全局：<meta name="referrer" content="never" />
2. 局部：<img src="xxxx.jpg"  referrerPolicy="no-referrer" />

## cssSprite 雪碧图在线生成工具
https://code.ahthw.com/tools/csssprite/
