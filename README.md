# java sandbox example run

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
