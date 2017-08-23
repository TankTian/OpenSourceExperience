#下面docker编译环境以及构建好，可以直接使用。（-v 挂在目录；-w命令执行目录 -ti就是docker将给你一个伪终端进行交互命令，后面可以直接输入命令）
docker run --rm -it --name zqmvn -v /root/tmp/java-chassis-0.1.0:/usr/src/project -w /usr/src/project qizha/cse-java-chassis-build mvn clean install

#撤销上次add
git reset HEAD .
#版本回退，保留原始修改
git reset --soft tag
#版本回退，不保留原始修改
git reset --hard tag
