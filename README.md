# rabbitmqwithgo

在A和B两台服务器上操作

step1
在A台服务器上
* docker run -d --hostname my-rabbit --name rabbitmq -p 8090:15672 -p 5672:5672 rabbitmq:3
* docker exec -it rabbitmq bash
* rabbitmq-plugins enable rabbitmq_management

# 开启rabbitmq web界面
进入容器运行命令

# 创建用户


* rabbitmqctl add_user {用户名} {密码}



// 设置权限
# rabbitmqctl set_user_tags {用户名} {权限}


例：创建一个超级用户
* rabbitmqctl add_user admin1 cCUnyz3ywWKVcjXw


* rabbitmqctl set_user_tags admin1 administrator


查看用户列表
* rabbitmqctl list_users


为用户赋权
// 使用户user1具有vhost1这个virtual host中所有资源的配置、写、读权限以便管理其中的资源
* rabbitmqctl  set_permissions -p vhost1 user1 '.*' '.*' '.*' 



// 查看权限
* rabbitmqctl list_user_permissions user1



* rabbitmqctl list_permissions -p vhost1



// 清除权限
* rabbitmqctl clear_permissions [-p VHostPath] User


删除用户
* rabbitmqctl delete_user Username


修改用户的密码
* rabbitmqctl change_password Username Newpassword


step2
在B台服务器上
  * docker run -it -p 8099:8099 -p 8081:8080 -p 5670:5672 mengmanzbh/go

step3
  * git clone https://github.com/rabbitmq/rabbitmq-tutorials
  * go get github.com/streadway/amqp
  * cd rabbitmq-tutorials/go/

链接改成这样
 *  amqp://guest:guest@18.234.102.148:5672/
 *  go run send.go


