# SLAs and SLOs #

## Check Your Knowledge ##

1. On VM, if you install Wireshark, you should be able to sniff packets from:

__Only my VM.__

_Correct. Due to the isolation provided by VM's cloud provider, Wireshark will work only in your VM.._

2. The process of mapping instances from the virtual cloud to the physical infrastructure is called cloud cartography. 
Assuming that you're an IaaS provider, which of the following will protect an attacker from mapping your service?

__Dynamically allocating both public and private IPs__

_Correct. As long as the IP addresses are allocated in an unpredictable fashion, your service is difficult to map._

3. You host an email server on the cloud only to find that the emails that your service sends are categorized as spam by anti-spammers like Spamhaus. 
However, the content of your mails is not spam-like. What could be a possible reason for this filtering?

__Both Spamhaus and cloud providers need to adapt to this new type of problem.__

_Correct! This is an evolving problem due to the complex and ever-changing patterns of spam._

4. Some service providers offer dedicated VM instances as an added security measure. 
Such instances are guaranteed to run on dedicated hardware that will not be shared with other users of the cloud service. 
Which of the following threats will you be protected against on a dedicated VM?

__Malicious code from a competitor hosted on a neighboring VM.__

_Correct. With dedicated infrastructure, we can eliminate the threat of a competitor running malicious code from a neighboring VM._

5. A cloud firewall resides within the hypervisor layer, between the physical network interface and the instance's virtual interface. 
All packets must pass through this layer; thus an instance's neighbors have no more access to that instance than any other host on the 
internet and can be treated as if they are on separate physical hosts. These can be configured as security groups. What is one disadvantage of this method?

__The security groups don't let you log traffic that's being blocked, so you have reduced visibility about security events.__

6. Homomorphic encryption is a special form of encryption where computation can be carded out on encrypted data. For instance, 
if Bing used homomorphic encryption, it would receive an encrypted version of your search term, find the matches without looking at it, 
and return an encrypted version of the results. Your data would never be exposed. Recent research from Craig Gentry at Stanford demonstrated 
a practical way to create an encryption scheme that allows addition and multiplication. Why is this not widely used?

__The scheme is currently computationally very expensive, and takes too long.__

7. If you're an educator building a service that runs and grades student code to add two numbers, which of the following should you not do?
__Run the script as the root user.__
