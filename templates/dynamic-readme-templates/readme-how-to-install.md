## How to install
This Project uses Maven.  
1. Clone the repository: 
```bash
git clone https://github.com/${{ env.REPOSITORY_FULL_NAME }}/
```
2. Run inside of e.g. Eclipse, using the default "Run as -> Java Application"-option, or build yourself a `.jar`-file, using Maven:
```bash
mvn install
```  

Once we hit a usable state in developement, there will be some form of installer to actually install and use the server.