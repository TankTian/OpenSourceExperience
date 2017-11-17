## DOCKER
### 下面docker编译环境以及构建好，可以直接使用。（-v 挂在目录；-w命令执行目录 -ti就是docker将给你一个伪终端进行交互命令，后面可以直接输入命令）  https://paas-training.obs.cn-north-1.myhwclouds.com/huaweiair.test.tar.gz


docker run --rm -it --name zqmvn -v /root/tmp/java-chassis-0.1.0:/usr/src/project -w /usr/src/project qizha/cse-java-chassis-build mvn clean install

## GIT
### 撤销上次add  
git reset HEAD .  
### 版本回退，保留原始修改  
git reset --soft tag  
### 版本回退，不保留原始修改  
git reset --hard tag  

    CseHttpEntity<Person> httpEntity = new CseHttpEntity<>(person);
    httpEntity.addContext("contextKey", "contextValue");
    ResponseEntity<String> responseEntity =
        RestTemplateBuilder.create().exchange("cse://springmvc/springmvchello/sayhello", HttpMethod.POST, httpEntity, String.class);
    System.out.println("tank test :  "+responseEntity.getBody());

### package

		<plugins>
			<!-- 项目依赖插件 -->
			<plugin>
				<groupId>org.apache.maven.plugins</groupId>
				<artifactId>maven-dependency-plugin</artifactId>
				<configuration>
					<outputDirectory>${project.build.directory}/lib_accesspoint</outputDirectory>
					<excludeTransitive>false</excludeTransitive> <!-- 表示是否不包含间接依赖的包 -->
					<stripVersion>false</stripVersion> <!-- 去除版本信息 -->
				</configuration>

				<executions>
					<execution>
						<id>copy-dependencies</id>
						<phase>package</phase>
						<goals>
							<goal>copy-dependencies</goal>
						</goals>
						<configuration>
							<!-- 拷贝项目依赖包到lib/目录下 -->
							<outputDirectory>${project.build.directory}/build/lib_accesspoint</outputDirectory>
							<excludeTransitive>false</excludeTransitive>
							<stripVersion>false</stripVersion>
						</configuration>
					</execution>
				</executions>
			</plugin>

			<!-- 打包插件 -->
			<plugin>
				<groupId>org.apache.maven.plugins</groupId>
				<artifactId>maven-jar-plugin</artifactId>
				<version>2.6</version>
				<configuration>
					<outputDirectory>${project.build.directory}/build</outputDirectory>
					<archive>
						<!-- 生成MANIFEST.MF的设置 -->
						<manifest>
							<!-- 为依赖包添加路径, 这些路径会写在MANIFEST文件的Class-Path下 -->
							<addClasspath>true</addClasspath>
							<classpathPrefix>lib_accesspoint</classpathPrefix>
							<!-- jar启动入口类 -->
							<mainClass>com.huawei.paas.cse.autotest.studentmanager.Main</mainClass>
						</manifest>
					</archive>
				</configuration>
			</plugin>
