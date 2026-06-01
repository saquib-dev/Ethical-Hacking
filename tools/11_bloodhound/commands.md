# BloodHound - Cheat Sheet

## Starting the Infrastructure (Kali/Linux)
- **Start Neo4j database:** 
  ```bash
  sudo neo4j start
  ```
  *(Default UI is usually at `http://localhost:7474`, default credentials: `neo4j` / `neo4j`)*
- **Start BloodHound GUI:**
  ```bash
  bloodhound
  ```

## Data Collection (Ingestors)

### SharpHound (Windows)
SharpHound is run from a domain-joined Windows machine or via runas/Pass-the-Hash.
- **Basic Collection (All data):**
  ```cmd
  SharpHound.exe -c All
  ```
- **Collect specific data (e.g., Sessions and ObjectProps):**
  ```cmd
  SharpHound.exe -c Session,ObjectProps
  ```
- **Stealthier collection (limits LDAP queries):**
  ```cmd
  SharpHound.exe -c Stealth
  ```
- **Specify a target domain:**
  ```cmd
  SharpHound.exe -d target.local
  ```

### BloodHound-Python (Linux)
Useful when attacking from a non-domain-joined Linux machine, provided you have valid AD credentials.
- **Basic Collection:**
  ```bash
  bloodhound-python -u 'username' -p 'password' -ns [DC_IP] -d domain.local -c All
  ```
- **Using Pass-the-Hash:**
  ```bash
  bloodhound-python -u 'username' -p 'LM:NT' -ns [DC_IP] -d domain.local -c All
  ```

## Useful Cypher Queries (Advanced Search)
- **Find all Domain Admins:**
  ```cypher
  MATCH (n:Group) WHERE n.name =~ '(?i).*DOMAIN ADMINS.*' RETURN n
  ```
- **Find computers where Domain Users are Local Admins:**
  ```cypher
  MATCH p=(m:Group)-[r:AdminTo]->(n:Computer) WHERE m.name =~ '(?i).*DOMAIN USERS.*' RETURN p
  ```
