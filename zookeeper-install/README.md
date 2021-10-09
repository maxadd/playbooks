修改自 https://github.com/kpx-dev/ansible-zookeeper。

默认配置在 ansible-zookeeper/defaults/main.yml，配置很少，看着改就行。

zk 的下载链接为 `{{ zookeeper_download_base_url }}/zookeeper-{{ version }}.tar.gz`，因此需要提供对应的 http 链接。解压之后的文件名必须是 `zookeeper-{{ version }}`，不然会报错，不行就修改 playbook 文件。

hosts 文件里面就是需要安装的机器，配置好就行。

安装：

```
ansible-playbook -i hosts --private-key /PATH/TO/PRIVATE-KEY site.yml
```