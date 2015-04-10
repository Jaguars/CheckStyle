# Checkstyle file for Jaguars.

This is the checkstyle file to be used by Java development within Jaguars.

## Integrating within IntelliJ

1. Start IntelliJ
2. From the "Welcome to IntelliJ IDEA" screen click "Configure"
3. Click "Settings"
4. On the left click "CheckStyle" (if you don't see CheckStyle, you need to first install the CheckStyle plugin for IntelliJ)
5. Add a new configuration file.
    1. Type in a name for the description, e.g. "Sun Checks (Jaguars Version)".
    2. Check "Use a CheckStyle file accessible via HTTP", and enter the URL: `https://raw.githubusercontent.com/Jaguars/CheckStyle/master/sun_checks.xml`
    3. Click "Next"
6. Click "Finish"
7. Make sure you check the new configuration file as "Active"
8. Check "Scan test classes"

After that, all new projects for IntelliJ should use this new coding standard.  For existing projects, you may have to follow this guide after opening the project in order to set the project specific settings.

## Integrating into Maven validate phase

1. Open your projects `pom.xml` file.
2. Add the following plugin XML to your build section:

```
<plugin>
	<groupId>org.apache.maven.plugins</groupId>
	<artifactId>maven-checkstyle-plugin</artifactId>
	<version>2.11</version>
	<executions>
		<execution>
			<id>validate</id>
			<phase>validate</phase>
			<configuration>
				<configLocation>https://raw.githubusercontent.com/Jaguars/CheckStyle/master/sun_checks.xml</configLocation>
				<encoding>UTF-8</encoding>
				<consoleOutput>true</consoleOutput>
				<includeTestSourceDirectory>true</includeTestSourceDirectory>
				<failsOnError>true</failsOnError>
				<failOnViolation>true</failOnViolation>
			</configuration>
			<goals>
				<goal>check</goal>
			</goals>
		</execution>
	</executions>
</plugin>
```
