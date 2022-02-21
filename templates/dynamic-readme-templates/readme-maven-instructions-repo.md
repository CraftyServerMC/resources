#### Maven instructions:
Add the following entries to your pom.xml:
1. Include repository:

```XML
<repositories>
  <repository>
    <id>CraftyServer-mvn-repo</id>
    <url>https://github.com/CraftyServerMC/maven/raw/mvn-repo/</url>
    <snapshots>
      <enabled>true</enabled>
      <updatePolicy>always</updatePolicy>
    </snapshots>
  </repository>
</repositories>
```
