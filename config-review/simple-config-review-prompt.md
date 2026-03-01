
***

# **Simple Config Review Prompts (3 Variants)**

Each is short, powerful, and requires no complex framework.

***

# ✅ **Prompt 1 — Basic Config Review (General Use)**

### **Prompt**

    You are a Network Configuration Review Assistant.
    I will paste a device configuration.

    Please provide:
    1. Top issues or misconfigurations
    2. Security risks
    3. Unused or redundant commands
    4. Best-practice improvements

    Keep it short and practical.
    Ask me if vendor/platform is unclear.

### **Example (Cisco NX-OS)**

    Review this NX-OS config:

    feature ospf
    feature interface-vlan
    ip route 0.0.0.0/0 10.10.10.1
    no password strength-check
    ssh key rsa 1024

    vlan 10
      name USERS
      ip igmp snooping disable

    interface Vlan10
      ip address 10.1.10.1/24

### **Example (Arista EOS)**

    Review this Arista config:

    daemon TerminAttr
       exec command "bash -c 'echo test'"

    management api http-commands
       no shutdown

    enable secret 5 $1$abc123

    spanning-tree mode mstp
    spanning-tree vlan 1-4094 priority 0

***

# ✅ **Prompt 2 — Security-Focused Config Review**

### **Prompt**

    I will paste a switch/router configuration.
    Please focus on SECURITY ONLY.

    Provide:
    1. Weak or dangerous settings
    2. Open services or insecure protocols
    3. Missing recommended security features
    4. Quick fixes I should apply

    Keep output short. Do NOT add vendor-specific commands unless present.

### **Example (Cisco NX-OS)**

    Check this NX-OS config for security issues:

    username admin password 5 $1$abcd$test
    no ip ssh source-interface
    feature telnet
    logging level default 0
    feature http-server

### **Example (Arista EOS)**

    Check this Arista config for security risks:

    management api http-commands
       no shutdown

    aaa authentication login default local
    ip tacacs source-interface Management1

    ntp source vrf default

***

# ✅ **Prompt 3 — Cleanup & Best-Practice Review**

### **Prompt**

    I will paste a device configuration.

    Your tasks:
    1. Identify redundant, unused, or deprecated commands
    2. Suggest cleanup recommendations
    3. Suggest best-practice improvements
    4. Do NOT rewrite the config unless I ask

    Keep it simple and vendor-neutral.

### **Example (Cisco NX-OS)**

    Review this config for cleanup:

    feature ospf
    feature ospf   (duplicated)
    ip domain-lookup
    ip domain-lookup  (duplicated)

    interface Eth1/1
      mtu 9216
    interface Eth1/1
      switchport mode trunk

    vlan 20
    vlan 20   (duplicate vlan)

### **Example (Arista EOS)**

    Review this Arista config for cleanup:

    spanning-tree vlan 10 priority 4096
    spanning-tree vlan 10 priority 4096

    interface Ethernet3
      no switchport
    interface Ethernet3
      no switchport

    alias TEST "show version"
    alias TEST "show clock"

    vlan 100
      name USERS
    vlan 100

***

Which one should we create next?
