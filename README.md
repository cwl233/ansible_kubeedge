# 使用方法:


1.安装ansible
```
apt-get install software-properties-common sshpass
apt-get update
apt-get install ansible
```
2.拉取ansible_kubeedge仓库
```
cd /root/
git clone https://github.com/cwl233/ansible_kubeedge.git
cd ansible_kubeedge
```
3.拉取kubeedge binary(如果是自己编译的binary那么只要放到对应的位置就可以)
```
wget https://github.com/kubeedge/kubeedge/releases/download/v1.4.0/kubeedge-v1.4.0-linux-amd64.tar.gz
tar -xf kubeedge-v1.4.0-linux-amd64.tar.gz
mv kubeedge-v1.4.0-linux-amd64 /root/ansible_kubeedge/kubeedge/
```

4.在ansible_kubeedge/hosts中填写cloud和edge的ip和passwd
```
cp hosts /etc/ansible/hosts
```

5.使用playbook安装依赖，这里建议先在部署机上ssh一下所有机器，（为了把ssh指纹写进known_hosts）,建议把cloud_server作为运行这些命令的机器
```
ansible-playbook requirements.yaml
```

6.使用playbook部署kubeedge
```
ansible-playbook kubeedge.yaml
```