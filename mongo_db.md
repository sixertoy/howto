### MongoDB Conf + Install as Service - Windows

##### Download

http://www.mongodb.org/downloads

##### Set env path variables

```bash
set PATH=%PATH%;c:\Progam Files\MongoDB\bin
```

##### Create folders

```bash
md c:\mongodb
md c:\mongodb\data
md c:\mongodb\data\db
md c:\mongodb\log
```

##### Configuration

```yaml
# MongodB Config File
# @see http://docs.mongodb.org/manual/reference/configuration-options/
systemLog:
    destination: file
    path: 'c:\mongodb\log\mongodb.log'
    logAppend: true
    traceAllExceptions: true
storage:
    dbPath: 'c:\mongodb\data'
    journal:
        enabled: true
net:
    port: 27017
    bindIp: 127.0.0.1
#processManagement:
    #fork: true
```

##### Install service

```bash
mongod -f "c:\mongodb\mongodb.conf" --install
# or
mongod -f "c:\mongodb\mongodb.conf" --install && net start MongoDB
```

##### Stop, Start, Remove

```bash
net start MongoDB
net stop MongoDB
mongodb --remove
```
