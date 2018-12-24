# rabbitmqwithgo

在A和B两台服务器上操作

step1
在A台服务器上
  docker run -d --hostname my-rabbit -p 8080:15672 -p 5672:5672 rabbitmq:3-management

step2
在B台服务器上
  docker run -it -p 8099:8099 -p 8081:8080 -p 5670:5672 mengmanzbh/go

step3
  git clone https://github.com/rabbitmq/rabbitmq-tutorials
  go get github.com/streadway/amqp
  cd rabbitmq-tutorials/go/

链接改成这样
  amqp://guest:guest@18.234.102.148:5672/
  go run send.go


