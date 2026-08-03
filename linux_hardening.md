---


---

<h2 id="linux-system-hardening"><a href="https://tryhackme.com/room/linuxsystemhardening">Linux System Hardening</a></h2>
<ul>
<li><strong>Physical Security</strong>
<ul>
<li>If an intruder can access the system physically, it is a non-sophisticated task to use , a popular bootloader, to reset the root password account. Hence we have the adage “boot access = root access”.</li>
<li>In comes <code>grub2-mkpasswd-pbkdf2</code></li>
<li>prompts you to input your password twice and generates a hash for you</li>
<li>The resulting hash should be added to the appropriate configuration file</li>
<li>It will require the user to supply a password to access advanced boot configurations via GRUB, including logging in with root access.</li>
</ul>
</li>
</ul>

