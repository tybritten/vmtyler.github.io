---
layout: post
status: publish
published: true
comments: true
title: "Cloud Encryption is Fool's Gold"
categories:
- cloud

---
I constantly see a number of encryption vendors selling their wares by promising to 'protect your VMs in the cloud' or 'help you meet PCI compliance in the cloud' through encryption. What these vendors are selling is a technology called Data at Rest Encryption (DARE). It's a style of encryption that leverages either existing OS-level encryption or deploys its own encryption agent but generally lives right above the storage drivers in the operating system. In this use case, it runs inside the VM and encrypts data as it is written and decrypts it as it is read. Some even leverage underlying hardware acceleration if it's available.

### DARE? How Does it Work

Data at Rest Encryption is an important technology that's been around for some time. How it works is pretty straightforward. A software module, either provided by the OS or the software vendor, is loaded into the I/O stack and intercepts all traffic between the rest of the server and e underlying disk. It encrypts disk blocks as they are written and decrypts them as they are read. To the rest of the server, applications, and users this process is seamless and goes unnoticed. It's called 'at rest' encryption because the only place where the data is encrypted is the data 'resting' on the disk.

### What About Keys?
The one thing I haven't mentioned yet is encryption keys. That software module that's doing the encryption work needs a key to encrypt and decrypt the data. Depending on the implementation, it gets those keys in a different way. A common way is to encrypt the key using a password. This is a common way FileVault on OS X works. When my laptop boots, the UEFI boot loader asks for my password which it uses to decrypt my encryption key and pass it to FileVault which uses that key to mount my encrypted hard drive and boot my system.  My key is stored in memory by FileVault, but when my laptop is powered off, the memory is cleared.


While that's fine for one machine, it generally doesn't scale. So many vendors offer some sort of centralized key manager that a server needs to check in with to get its key. This central server can also perform other management tasks like changing keys, pushing agent upgrades, etc. Just like my FileVault example, when the machine is powered off or rebooted it needs to check in with the key manager to get a key otherwise it can't decrypt the data.

### What's the Problem?
Sounds great, right? Honestly, it was and still is great for physical use cases. For example, disposing of failed disks is easier because you don't have to worry about sensitive data on it. Everyone with even the slightest bit of sensitive data (tax returns?) on your laptop should have a password and encryption turned on. If you lose your powered off laptop or it's stolen, your data is safe (unless you have your password on a sticky note on your laptop).


Notice how I said 'powered off.' As long as your laptop is running, the process doing to encryption work is running and has the key in memory. How do you get to the key as an attacker? It's really hard- you need to access the memory chips and siphon the keys out. I'm sure the NSA & CIA has equipment to do this, but not your average thief. There's an old security maxim that if someone has physical access, you have to assume they'll eventually be able to gain full access. In this case, it's still a pretty rare combination.

### One Click Access
Still don't see a problem yet, right? Well here it is: *virtualization and cloud technology makes it much, much easier to access both the storage and the memory of a running machine.* What used to take a CIA-level capability, can now be done by almost any server admin. If you're running a VM somewhere, whoever administers the underlying hypervisor has access to your data, encrypted or not.
How? Well Since the hypervisor stands between your VM and the hardware, it adds some great new capabilities (live migrating servers, moving storage, resizing VMs while they're running, etc). It also includes the ability to dump the memory of a running VM to a file without the VM knowing. I can also copy the storage your VM is using without you knowing.  
If you're leveraging something like BitLocker in a VMware vSphere-backed environment to do the encryption, defeating it as an admin is stupidly easy:

* From the GUI, take a VM snapshot, and check the box to include the memory as well
* download one of the many BitLocker decrypter programs
* point it at the dumped memory as the key location and the vmdk as the encrypted data
* mount the unencrypted data to the windows machine of your choosing and you now have all the data.

It's that easy and the owner of the VM is none the wiser.

### Turtles All the Way Down
This is the part where vendors that do things differently generally jump up and go "ah ha! we've thought of that and we've overcome that problem!" This usually applies to solutions that do centralized key management.  Their main defense is some sort of nested key arrangement- the key server doesn't give out the key to the data, it gives out the key to unlock the key for the data. This approach has some advantages- it allows re-keying a machine without having to decrypt and re-encrypt all the data to change keys. The problem is, even if they decrypted the data key on each actual use every millisecond (which would kill performance), the outer key (the one decrypting the data key) is still stored in the clear in memory. Why don't they encrypt *that* key? You can keep going down the line, but sooner or later the outermost key has to be stored in the clear in memory for any of this to work. So when I take a snapshot of a VM disk and its ram, there's a key in there that can get me to the data in the memory, period.


One other defense mechanism that is trotted out is they assume the person trying to steal the data is going to power the cloned/snapshotted VM on. Their agent will contact the key server, and the key server will either not supply a key, or in the case of nested keys, tell the agent to destroy the encrypted data key. While this is generally a good feature to have, it still doesn't fix any variation of scenario we talked about above.
Not to mention if your VM is compromised while it's running, it's totally unnoticeable to the attacker just like any other person or app accessing the data on the server.

### Meeting Compliance
Many security and encryption folks will usually drop back to "yeah, well, that all may be true, but we're required to encrypt to meet some compliance requirement and this checks the box." From my experience, this is usually incorrect and due to a misreading or misinterpretation of the relevant policies or governing documentation.   A perfect example is people encrypting VMs on Amazon Web Services to "meet PCI compliance." A quick google search will uncover that the entire AWS platform has received PCI DSS Level 1 certification.  Now that doesn't absolve those handling payment data from any other responsibilities in regards to PCI DSS, but there's no need to encrypt VMs there to "meet PCI compliance." I've seen this throughout my career both as a customer and as a consultant, each company interprets regulations and policies differently. It's not surprising because most of the regulations are purposely vague and focus on outcomes not techniques. There are obvious exceptions that are very prescriptive, but that's not the norm.

### Conclusion
Clearly DARE is a good technology for protecting physical computers with minimal impact on the user experience. We should all embrace any technology which is that straightforward. The problem is trying to apply this technology to virtual and cloud environments.
So if doing DARE in the cloud doesn't protect your data from a cloud administrator or from someone who has compromised your VM, what is it good for? Filling vendor bank accounts.
