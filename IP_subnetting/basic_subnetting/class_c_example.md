# Demo 1: Basic Subnetting (Class C Example)

**Network:** `192.168.10.0/24`  
**Requirement:** Create 4 subnets.  

---

### Step 1: Determine new prefix
- Original prefix: /24 → 255.255.255.0  
- To create 4 subnets, we need 2 extra bits (2² = 4).  
- New prefix: /26 → 255.255.255.192  

---

### Step 2: Calculate subnet increment
- Block size = 2^(8-6) = 64  
- Subnets: `0, 64, 128, 192`

---

### Step 3: List subnet details
1. `192.168.10.0/26` → Hosts 192.168.10.1 – 192.168.10.62, Broadcast 192.168.10.63  
2. `192.168.10.64/26` → Hosts 192.168.10.65 – 192.168.10.126, Broadcast 192.168.10.127  
3. `192.168.10.128/26` → Hosts 192.168.10.129 – 192.168.10.190, Broadcast 192.168.10.191  
4. `192.168.10.192/26` → Hosts 192.168.10.193 – 192.168.10.254, Broadcast 192.168.10.255  

---

✅ **Result:** 4 usable subnets, each with 62 usable host IPs.
