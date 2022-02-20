# Templates for .gitignore files
This document contains a few templates for your .gitignore that you might need when writing a module.
## Contents
1. [Standard Gitignore for Java](#standard-gitignore)
## Standard Gitignore for Java<a id='standard-gitignore'></a>
Thanks to [MinecraftForge/MinecraftForge](https://github.com/MinecraftForge/MinecraftForge/blob/1.18.x/.gitignore) for providing the "eclipse" section!
```
# Compiled class file
*.class

# Log file
*.log

# Server Config file
*.config

# BlueJ files
*.ctxt

# Mobile Tools for Java (J2ME)
.mtj.tmp/

# Package Files #
*.jar
*.war
*.nar
*.ear
*.zip
*.tar.gz
*.rar

# virtual machine crash logs, see http://www.java.com/en/download/help/error_hotspot.xml
hs_err_pid*
/bin/
/target/

# eclipse, shamelessly stolen from https://github.com/MinecraftForge/MinecraftForge/blob/1.18.x/.gitignore
**/bin
**/.settings
**/.classpath
*.project
```