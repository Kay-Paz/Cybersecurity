# Proof of Concept

## [`pkexec` privilege escalation hack](https://www.linkedin.com/posts/katie-paz_vulnerability-pkexec-kali-activity-6893066548563849216-Xui8)

My version of exploiting the privilege escalation vulnerability with `pkexec`. 

In this case, I used Kali to work around some roadblocks I had with my "user" account in an Ubuntu server. 
That user account had no external access to the internet, nor sudo or bash privileges. 

Instead, I downloaded the [PwnKit](https://github.com/ly4k/PwnKit) binary into my Kali machine and then secure copied it directly into the Ubuntu server. Once I ran it, I immediately got `root` access.
 
This also gave me a chance to practice configuring firewalls and networking- especially as the two virtual machines were running in separate VLANs and needed a way to communicate despite that.

A Nessus scan of the server was unable to find this vulnerability as it didn't have the user account credentials. Surprisingly though, running the 
[LinPEAS](https://github.com/carlospolop/PEASS-ng/tree/master/linPEAS) script from within the user account DID list `/usr/bin/pkexec` as "something to check out" under its SUID section, 
but did NOT recognize it as being a highly-rated PE vector. 
(From the LinPEAS report: `-rwsr-xr-x 1 root root 31K May 26 2021 /usr/bin/pkexec ---> Linux4.10_to_5.1.17(CVE-2019-13272)/rhel_6(CVE-2011-1485)`)  


***

https://github.com/Kay-Paz/Cybersecurity/assets/91631432/a68f26ed-88c5-4e3e-a4fd-e384640cbc32

