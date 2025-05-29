# java sandbox example run

If you would like to test specific version of aerospike client library make sure to set specific version, test version you would like to use in both java-sandbox pom.xml and aeropike client lib. In the aerospike client lib repo you can run `./set_version.sh <version>`. You should reference the same `<version>` java-sandbox pom.xml file. The version should resemble semantic versioning `major.minor.hotfix`. After you set the version make sure to build both projects with `mvn clean install`. You will have to run the `mvn clean install` command from both the aerospike client repo and current java-sandbox folder.

```xml
  <dependencies>
    <dependency>
        <groupId>com.aerospike</groupId>
        <artifactId>aerospike-client-jdk21</artifactId>
        <version>version</version>
    </dependency>
    .
    .
    .
```

```java
java -jar target/java-sandbox-1.0-SNAPSHOT-jar-with-dependencies.jar
```

Make sure to set the main class in the pom file:

```xml
  <build>
    <plugins>
          <plugin>
              <artifactId>maven-assembly-plugin</artifactId>
              <configuration>
                  <archive>
                      <manifest>
                          <addClasspath>true</addClasspath>
                          <mainClass>com.aerospike.App</mainClass> <!-- change this line -->
                      </manifest>
                  </archive>
                  <descriptorRefs>
                      <descriptorRef>jar-with-dependencies</descriptorRef>
                  </descriptorRefs>
              </configuration>
              <executions>
                  <execution>
                      <id>make-my-jar-with-dependencies</id>
                      <phase>package</phase>
                      <goals>
                          <goal>single</goal>
                      </goals>
                  </execution>
              </executions>
          </plugin>
          <plugin>

```
