在 https://github.com/sleighzy/ansible-kafka/ 基础上修改，用于安装 kafka 集群。

一些基础的配置在 ansible-kafka/defaults/main.yaml，必须要修改的配置有：

- kafka_download_base_url：下载 kafka 的地址，原版是直接下载官方的文件，由于国内访问国外速度感人，所以我给改了，但是需要提供一个 http 链接，整个文件的链接为 ：{{ kafka_download_base_url }}/kafka_{{ kafka_scala_version }}-{{ kafka_version }}.tgz；
- kafka_scala_version：scala 版本号，既是下载链接的一部分，也是 kafka 解压后文件名的一部分；
- kafka_version：kafka 版本号，既是下载链接的一部分，也是 kafka 解压后文件名的一部分；
- kafka_data_log_dirs：kafka 的数据目录；
- kafka_log_retention_hours：消息存储的最大时间。

修改完毕之后，修改 `hosts` 文件，指定 broker 的地址和两个变量，以及 zk 的连接地址。

需要注意的是，如果 `kafka_listeners` 的值是主机名而非 IP，安装之前需要保证可以解析。

安装：

```
ansible-playbook -i hosts --private-key /PATH/TO/PRIVATE_KEY site.yml
```