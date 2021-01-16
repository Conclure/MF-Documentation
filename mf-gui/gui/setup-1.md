---
description: This is how you add MF-GUI to your project.
---

# Setup

### Version

Make sure to replace `{version}` with the latest version of **MF-GUI**.  
Latest version: `2.0.2`

### Gradle

You need to add the dependency to your `build.gradle`.

```groovy
repositories {
    mavenCentral()
}

dependencies {
    implementation "me.mattstudios.utils:matt-framework-gui:{version}" // Replace version here 
}
```

 In order to include the lib in your project, you need to add `shadowJar` plugin `build.gradle`.  
 Replace `[YOUR PACKAGE]`with your plugin's package, for example `me.myplugin.plugin`.

```groovy
apply plugin: 'com.github.johnrengelman.shadow'

shadowJar {
   relocate 'me.mattstudios.mfgui', '[YOUR PACKAGE].mfgui'
}
```

### Maven

You need to add the dependency to your `pom.xml`.

```markup
<dependency>
  <groupId>me.mattstudios.utils</groupId>
  <artifactId>matt-framework-gui</artifactId>
  <version>{version}</version> <!-- replace version here -->
</dependency>
```

 In order to include the framework in your project, you need to add the following to your `pom.xml`, in the plugins section.  
 Replace `[YOUR PACKAGE]`with your plugin's package, for example `me.myplugin.plugin`.

```markup
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-shade-plugin</artifactId>
    <version>3.1.1</version>
    <configuration>
        <relocations>
            <relocation>
                <pattern>me.mattstudios.mfgui</pattern>
                <shadedPattern>[YOUR PACKAGE].mfgui</shadedPattern> <!-- Replace package here here -->
            </relocation>
        </relocations>
    </configuration>
    <executions>
        <execution>
            <phase>package</phase>
            <goals>
                <goal>shade</goal>
            </goals>
        </execution>
    </executions>
</plugin>
```

