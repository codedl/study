```    <build>
        <plugins>
<!--            指定jdk版本-->
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <version>3.7.0</version>
                <configuration>
                    <source>8</source>
                    <target>8</target>
                </configuration>
            </plugin>
<!--            禁用原生jar-->
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-jar-plugin</artifactId>
                <version>3.2.2</version>
                <executions>
                    <execution>
                        <id>default-jar</id>
                        <phase>none</phase>
                    </execution>
                </executions>
            </plugin>
<!--            打入依赖jar，包含本地jar-->
           <plugin>
               <groupId>org.apache.maven.plugins</groupId>
               <artifactId>maven-assembly-plugin</artifactId>
               <version>3.1.1</version>
               <executions>
                   <execution>
                       <phase>package</phase>
                       <goals>
                           <goal>single</goal>
                       </goals>
                       <configuration>
                           <finalName>yyzl-open-sdk-1.0</finalName>
                           <appendAssemblyId>false</appendAssemblyId>
                           <archive>
                               <manifest>
                                   <addClasspath>true</addClasspath>
                                   <mainClass>com.ocopen.test.Demo</mainClass>
                               </manifest>
                           </archive>
                           <descriptorRefs>
                               <descriptorRef>jar-with-dependencies</descriptorRef>
                           </descriptorRefs>
                       </configuration>
                   </execution>
               </executions>
           </plugin>
        </plugins>
    </build>
```