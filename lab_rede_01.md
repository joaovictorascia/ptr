Disciplina: **ENE0011 – Laboratório de Redes**  
Curso: **Engenharia de Redes de Comunicação**  
Instituição: **Universidade de Brasília (UnB)**  
Departamento: **Engenharia Elétrica** 

Professor Responsável: **Prof. Dr. Laerte Peotta de Melo**

# Relatório do Experimento 01

## Identificação
- Nome: João Victor Machado Santos
- Matrícula: 232013318
- Turma: 01

## Objetivo

Conhecer os dispositivos básicos de rede e realizar operações básicas em um roteador Cisco.

## Ambiente experimental
- Router 1841

## Procedimentos
O Router 1841 foi configurado via CLI.
Logs:
```
         --- System Configuration Dialog ---

Would you like to enter the initial configuration dialog? [yes/no]: yes

At any point you may enter a question mark '?' for help.
Use ctrl-c to abort configuration dialog at any prompt.
Default settings are in square brackets '[]'.


Basic management setup configures only enough connectivity
for management of the system, extended setup will ask you
to configure each interface on the system

Would you like to enter basic management setup? [yes/no]: yes
Configuring global parameters:

  Enter host name [Router]: lab_1

  The enable secret is a password used to protect access to
  privileged EXEC and configuration modes. This password, after
  entered, becomes encrypted in the configuration.
  Enter enable secret: apr

  The enable password is used when you do not specify an
  enable secret password, with some older software versions, and
  some boot images.
  Enter enable password: apr1

  The virtual terminal password is used to protect
  access to the router over a network interface.
  Enter virtual terminal password: apr
Configure SNMP Network Management? [no]:no

Current interface summary

Interface              IP-Address      OK? Method Status                Protocol

FastEthernet0/0        unassigned      YES manual administratively down down

FastEthernet0/1        unassigned      YES manual administratively down down

Vlan1                  unassigned      YES manual administratively down down

Enter interface name used to connect to the
management network from the above interface summary: FastEthernet0/0

Configuring interface FastEthernet0/0:
  Configure IP on this interface? [yes]: yes
    IP address for this interface: 192.168.0.10
    Subnet mask for this interface [255.255.255.0] : 255.255.255.0

The following configuration command script was created:

!
hostname lab_1
enable secret 5 $1$mERr$V7cjNHFi7FcITLCiKNEah.
enable password apr1
line vty 0 4
password apr
!
interface Vlan1
 shutdown
 no ip address
!
interface FastEthernet0/0
 no shutdown
 ip address 192.168.0.10 255.255.255.0
!
interface FastEthernet0/1
 shutdown
 no ip address
!
end

[0] Go to the IOS command prompt without saving this config.
[1] Return back to the setup without saving this config.
[2] Save this configuration to nvram and exit.

Enter your selection [2]: 2
Building configuration...
[OK]
```

`show version`:
```
[...]
Cisco 1841 (revision 5.0) with 114688K/16384K bytes of memory.
Processor board ID FTX0947Z18E
M860 processor: part number 0, mask 49
2 FastEthernet/IEEE 802.3 interface(s)
191K bytes of NVRAM.
63488K bytes of ATA CompactFlash (Read/Write)

Configuration register is 0x2102
```

`show interfaces`:

```
lab_1>show interface
FastEthernet0/0 is down, line protocol is down (disabled)
  Hardware is Lance, address is 00e0.f711.ab01 (bia 00e0.f711.ab01)
  Internet address is 192.168.0.10/24
  MTU 1500 bytes, BW 100000 Kbit, DLY 100 usec,
     reliability 255/255, txload 1/255, rxload 1/255
  Encapsulation ARPA, loopback not set
  Full-duplex, 100Mb/s, media type is RJ45
  ARP type: ARPA, ARP Timeout 04:00:00, 
  Last input 00:00:08, output 00:00:05, output hang never
  Last clearing of "show interface" counters never
  Input queue: 0/75/0 (size/max/drops); Total output drops: 0
  Queueing strategy: fifo
  Output queue :0/40 (size/max)
  5 minute input rate 0 bits/sec, 0 packets/sec
  5 minute output rate 0 bits/sec, 0 packets/sec
     0 packets input, 0 bytes, 0 no buffer
     Received 0 broadcasts, 0 runts, 0 giants, 0 throttles
     0 input errors, 0 CRC, 0 frame, 0 overrun, 0 ignored, 0 abort
     0 input packets with dribble condition detected
     0 packets output, 0 bytes, 0 underruns
     0 output errors, 0 collisions, 1 interface resets
     0 babbles, 0 late collision, 0 deferred
     0 lost carrier, 0 no carrier
     0 output buffer failures, 0 output buffers swapped out
FastEthernet0/1 is administratively down, line protocol is down (disabled)
  Hardware is Lance, address is 00e0.f711.ab02 (bia 00e0.f711.ab02)
  MTU 1500 bytes, BW 100000 Kbit, DLY 100 usec,
     reliability 255/255, txload 1/255, rxload 1/255
  Encapsulation ARPA, loopback not set
  Full-duplex, 100Mb/s, media type is RJ45
  ARP type: ARPA, ARP Timeout 04:00:00, 
  Last input 00:00:08, output 00:00:05, output hang never
  Last clearing of "show interface" counters never
  Input queue: 0/75/0 (size/max/drops); Total output drops: 0
  Queueing strategy: fifo
  Output queue :0/40 (size/max)
  5 minute input rate 0 bits/sec, 0 packets/sec
  5 minute output rate 0 bits/sec, 0 packets/sec
     0 packets input, 0 bytes, 0 no buffer
     Received 0 broadcasts, 0 runts, 0 giants, 0 throttles
     0 input errors, 0 CRC, 0 frame, 0 overrun, 0 ignored, 0 abort
     0 input packets with dribble condition detected
     0 packets output, 0 bytes, 0 underruns
     0 output errors, 0 collisions, 2 interface resets
     0 babbles, 0 late collision, 0 deferred
     0 lost carrier, 0 no carrier
     0 output buffer failures, 0 output buffers swapped out
Vlan1 is administratively down, line protocol is down
  Hardware is CPU Interface, address is 0000.0c37.bbe9 (bia 0000.0c37.bbe9)
  MTU 1500 bytes, BW 100000 Kbit, DLY 1000000 usec,
     reliability 255/255, txload 1/255, rxload 1/255
  Encapsulation ARPA, loopback not set
  ARP type: ARPA, ARP Timeout 04:00:00
  Last input 21:40:21, output never, output hang never
  Last clearing of "show interface" counters never
  Input queue: 0/75/0/0 (size/max/drops/flushes); Total output drops: 0
  Queueing strategy: fifo
  Output queue: 0/40 (size/max)
  5 minute input rate 0 bits/sec, 0 packets/sec
  5 minute output rate 0 bits/sec, 0 packets/sec
     1682 packets input, 530955 bytes, 0 no buffer
     Received 0 broadcasts (0 IP multicast)
     0 runts, 0 giants, 0 throttles
     0 input errors, 0 CRC, 0 frame, 0 overrun, 0 ignored
     563859 packets output, 0 bytes, 0 underruns
     0 output errors, 23 interface resets
     0 output buffer failures, 0 output buffers swapped out

lab_1>
```

`show ip interface`:

```
lab_1>show ip interface
FastEthernet0/0 is up, line protocol is down (disabled)
  Internet address is 192.168.0.10/24
  Broadcast address is 255.255.255.255
  Address determined by setup command
  MTU is 1500 bytes
  Helper address is not set
  Directed broadcast forwarding is disabled
  Outgoing access list is not set
  Inbound  access list is not set
  Proxy ARP is enabled
  Security level is default
  Split horizon is enabled
  ICMP redirects are always sent
  ICMP unreachables are always sent
  ICMP mask replies are never sent
  IP fast switching is disabled
  IP fast switching on the same interface is disabled
  IP Flow switching is disabled
  IP Fast switching turbo vector
  IP multicast fast switching is disabled
  IP multicast distributed fast switching is disabled
  Router Discovery is disabled
  IP output packet accounting is disabled
  IP access violation accounting is disabled
  TCP/IP header compression is disabled
  RTP/IP header compression is disabled
  Probe proxy name replies are disabled
  Policy routing is disabled
  Network address translation is disabled
  BGP Policy Mapping is disabled
  Input features: MCI Check
  WCCP Redirect outbound is disabled
  WCCP Redirect inbound is disabled
  WCCP Redirect exclude is disabled
FastEthernet0/1 is administratively down, line protocol is down (disabled)
  Internet protocol processing disabled
Vlan1 is administratively down, line protocol is down
  Internet protocol processing disabled

lab_1>
```

`cdp`:

```
lab_1>show cdp
Global CDP information:
    Sending CDP packets every 60 seconds
    Sending a holdtime value of 180 seconds
    Sending CDPv2 advertisements is enabled
lab_1>show cdp neighbors
Capability Codes: R - Router, T - Trans Bridge, B - Source Route Bridge
                  S - Switch, H - Host, I - IGMP, r - Repeater, P - Phone
Device ID    Local Intrfce   Holdtme    Capability   Platform    Port ID
lab_1>
lab_1>
```

`show protocols`:

```
lab_1>show protocol
Global values:
  Internet Protocol routing is enabled
FastEthernet0/0 is down, line protocol is down
  Internet address is 192.168.0.10/24
FastEthernet0/1 is administratively down, line protocol is down
Vlan1 is administratively down, line protocol is down
```

Salvando:
```
lab_1#
lab_1#copy running-config startup-config
Destination filename [startup-config]? 
Building configuration...
[OK]
```
## Resultados e evidências
(incluir prints e tabelas em \`relatorio/figuras/\`)

## Análise técnica
(interpretação dos resultados)

## Conclusão
