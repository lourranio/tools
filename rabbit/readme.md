# Rabbit MQ

1. https://github.com/jlavallee/JMeter-Rabbit-AMQP
<div>
  <span align="center">
  <img alt="logo-ls" title="logo-ls" src="https://github.com/lourranio/tools/blob/c3bd3bc84159dbec5324c705b35071ccc1872809/img/JMeter-Rabbit-AMQP.png">
    </span>
</div><br>

2. https://rabbitmq.github.io/rabbitmq-perf-test/stable/htmlsingle/
<div>
  <span align="center">
  <img alt="logo-ls" title="logo-ls" src="..">
    </span>
</div><br>

```

Comandos

############ 1 - simple test ############
./runjava com.rabbitmq.perf.PerfTest \
--time 20 \
--producers 1 \
--consumers 2 \
--queue "q.test-1" \
--size 1000 \
--autoack \
--id "test 1" -h amqp://guest:guest@localhost:5672


############ 2 - Frame size test ############
./runjava com.rabbitmq.perf.PerfTest \
--time 20 \
--producers 1 \
--consumers 1 \
--queue "q.test-1" \
--size 1000000 \
--autoack \
--framemax 5000 \
--id "test 2" -h amqp://guest:guest@localhost:5672

./runjava com.rabbitmq.perf.PerfTest \
--time 20 \
--producers 1 \
--consumers 1 \
--queue "q.test-1" \
--size 1000000 \
--autoack \
--framemax 1000000 \
--id "test 2" -h amqp://guest:guest@localhost:5672


############ 3 - Queue extra parameters ############

./runjava com.rabbitmq.perf.PerfTest \
--time 20 \
--producers 1 \
--consumers 2 \
--queue "q.test-2" \
--size 1000 \
--autoack \
--queue-args x-max-length=10,x-max-priority=5,x-dead-letter-exchange=ex.dlx-exchange-name \
--auto-delete false \
--id "test 3" -h amqp://guest:guest@localhost:5672

############ 4 - Lazy Queue ############

./runjava com.rabbitmq.perf.PerfTest \
--time 20 \
--producers 50 \
--consumers 0 \
--queue "q.lazy-queue" \
--size 1000 \
--autoack \
--flag persistent \
--queue-args x-queue-mode=lazy \
--auto-delete false \
--id "test 4" -h amqp://guest:guest@localhost:5672


./runjava com.rabbitmq.perf.PerfTest \
--time 20 \
--producers 50 \
--consumers 0 \
--queue "q.not-lazy-queue" \
--size 1000 \
--autoack \
--flag persistent \
--auto-delete false \
--id "test 4" -h amqp://guest:guest@localhost:5672


############ 5 - RampUp ############

./runjava com.rabbitmq.perf.PerfTest --help | grep start-delay

for i in {1..10}; do ./runjava com.rabbitmq.perf.PerfTest \
--time 240 \
--producers 1 \
--consumers 1 \
--queue "q.test-2" \
--size 1000 \
--autoack \
--rate 1000 \
--id "test 5" -h amqp://guest:guest@localhost:5672 & sleep 10; done


########### 6 baseline many queues
./runjava com.rabbitmq.perf.PerfTest \
--time 20 \
--queue "q.test-6" \
--random-routing-key \
--producers 1 \
--consumers 0 \
--size 100 \
--queue-args x-queue-mode=lazy \
--flag persistent \
-h amqp://guest:guest@localhost:5672

./runjava com.rabbitmq.perf.PerfTest \
--time 20 \
--queue "q.test-6" \
--producers 1 \
--consumers 0 \
--size 100 \
--queue-args x-queue-mode=lazy \
--flag persistent \
-h amqp://guest:guest@localhost:5672

./runjava com.rabbitmq.perf.PerfTest \
--time 20 \
--queue-pattern 'q.perf-test-%d' --queue-pattern-from 1 --queue-pattern-to 10 \
--producers 10 \
--consumers 0 \
--size 100 \
--queue-args x-queue-mode=lazy \
--flag persistent \
-h amqp://guest:guest@localhost:5672

./runjava com.rabbitmq.perf.PerfTest \
--time 20 \
--queue-pattern 'q.perf-test-%d' --queue-pattern-from 1 --queue-pattern-to 10 \
--producers 1 \
--producer-channel-count 10 \
--consumers 0 \
--size 100 \
--queue-args x-queue-mode=lazy \
--flag persistent \
-h amqp://guest:guest@localhost:5672

./runjava com.rabbitmq.perf.PerfTest \
--time 20 \
--queue-pattern 'q.perf-test-%d' --queue-pattern-from 1 --queue-pattern-to 10 \
--producers 5 \
--producer-channel-count 2 \
--consumers 0 \
--size 100 \
--queue-args x-queue-mode=lazy \
--flag persistent \
-h amqp://guest:guest@localhost:5672

############# IoT ################

./runjava com.rabbitmq.perf.PerfTest \
--time 120 \
--queue-pattern 'perf-test-%05d' --queue-pattern-from 1 --queue-pattern-to 2000 \
--producers 2000 --consumers 0 \
--nio-threads 10 \
--producer-scheduler-threads 10 \
--consumers-thread-pools 10 \
--publishing-interval 1 \
--size 512 \
--heartbeat-sender-threads 10 \
--flag persistent \
--producer-random-start-delay 60 \
-h amqp://guest:guest@localhost:5672

```


