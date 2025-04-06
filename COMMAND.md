# 📘 OSQuery – Command Reference 

This document contains queries and commands used for __Auditing with OSQuery__.

---

## 🧱 Basic Monitoring

### 🔹Processes 
```sql
SELECT pid, name, user_time, system_time
FROM processes
ORDER BY pid DESC;
```

### 🔹Kernel Version
#### Kernel Version
```sql
SELECT version, arguments, device FROM kernel_info;
```
#### Kernel Modules
```sql
SELECT name, size, used_by, address
FROM kernel_modules
ORDER BY address ASC;
```
### 🔹 Packages
#### Packages from Ubuntu
```sql
SELECT name, version, source, status
FROM deb_packages
WHERE source LIKE '%ubuntu%';
```
#### Firewall Packages
```sql
SELECT name, version
FROM deb_packages
WHERE name LIKE '%iptables%' OR name LIKE '%firewalld%';
```
### 🔹SUID Binaries
```sql
SELECT path, username, groupname, permissions
FROM suid_bin;
````

## 🌐 Network & Process Monitoring
### 🔹 Open Ports and Sockets
#### Listening Ports
```sql
SELECT pid, port, protocol, family, address, fd, socket, net_namespace
FROM listening_ports
LIMIT 10;
````
#### Open Sockets
```sql
SELECT pid, socket, protocol, local_address, remote_address, local_port, remote_port
FROM process_open_sockets;
```

#### Interface Traffic (JOIN)
```sql
SELECT ia.interface, ia.address, id.ibytes, id.obytes
FROM interface_addresses AS ia
JOIN interface_details AS id
ON ia.interface = id.interface;
```

#### Gateway Info
```sql
 SELECT DISTINCT gateway, interface
FROM routes
WHERE gateway != '';
```
### 🔹 Processes and Memory Information
#### Processes from /sbin
```sql
SELECT pid, name, cmdline
FROM processes
WHERE cmdline LIKE '/sbin/%' OR cmdline LIKE '/usr/sbin/%';
```

#### Top Memory Usage
```sql
SELECT pid, name, uid, resident_size
FROM processes
ORDER BY resident_size DESC
LIMIT 10;
```

#### UID != EUID
```sql
SELECT pid, name, uid, euid, resident_size
FROM processes
WHERE uid != euid;
```
### Login Information
#### User Logins
```sql
SELECT username, pid, time, host
FROM last;
```

#### Login Counts
```sql
SELECT username, COUNT(*) AS connected
FROM last
GROUP BY username;
```

## 🛡️ Event and Syslog Logging
### File Events
```sql
SELECT * FROM file_events;
```

### Active Query Packs
```sql
SELECT name, platform, version, discovery_executions
FROM osquery_packs
WHERE active = 1;
```
## 🛠️ File Integrity Monitoring (FIM)
### 🔹 file_events Results
```sql
SELECT target_path, action
FROM file_events;
```






