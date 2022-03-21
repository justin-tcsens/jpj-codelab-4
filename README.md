# Vehicle Service
Vehicle service endpoint.

## Tasks
- Open pom.xml file from the project directory.
- Add OpenAPI codegen dependencies into pom.xml, before the closing tag of </dependencies>
    ```
        <!-- OpenAPI Codegen -->
		<dependency>
			<groupId>org.openapitools</groupId>
			<artifactId>jackson-databind-nullable</artifactId>
			<version>0.2.1</version>
		</dependency>
		<dependency>
			<groupId>io.springfox</groupId>
			<artifactId>springfox-swagger2</artifactId>
			<version>2.9.2</version>
		</dependency>
        <dependency>
            <groupId>commons-io</groupId>
            <artifactId>commons-io</artifactId>
            <version>2.11.0</version>
		</dependency>
		<!-- OpenAPI Codegen -->
    ```
- Add OpenAPI plugin execution goals into Spring Boot processes. Repleace the <package_name> with package name specified in your project.
    ```
        <!-- Open API Codegen -->
			<plugin>
				<groupId>org.openapitools</groupId>
				<artifactId>openapi-generator-maven-plugin</artifactId>
				<version>5.1.0</version>
				<executions>
					<execution>
						<id>jpj-vehicle</id>
						<goals>
							<goal>generate</goal>
						</goals>
						<configuration>
							<inputSpec>${project.basedir}/src/main/resources/vehicle-management.yaml</inputSpec>
							<generatorName>spring</generatorName>
							<library>spring-boot</library>
							<apiPackage><package_name>.api</apiPackage>
							<modelPackage><package_name>.model</modelPackage>
							<supportingFilesToGenerate>
								ApiUtil.java
							</supportingFilesToGenerate>
							<configOptions>
								<delegatePattern>true</delegatePattern>
								<interfaceOnly>true</interfaceOnly>
								<dateLibrary>java8</dateLibrary>
							</configOptions>
						</configuration>
					</execution>
				</executions>
			</plugin>
        <!-- Open API Codegen -->
    ```
- Save pom.xml.

### Notes:
- Run '.\mvnw clean install' to install necessary package defined in pom.xml
- Run '.\mvnw spring-boot:run' to start the Spring Boot application.
