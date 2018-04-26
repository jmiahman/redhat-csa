---


---

<h2 id="intro---archives-are-not-just-tar">Intro - Archives are not just tar</h2>
<p>Along with tar there are other types of archives on a RHEL system. Most administrators and users may not realize that a RPM file is actually a Archive as well.</p>
<p>An RPM package is simply a header structure on top of a CPIO archive. The package itself is comprised of four sections: a header with a leading identifier (magic number) that identifies the file as an RPM package, a signature to verify the integrity of the package, the header or ‘tagged’ data containing package information, version numbers, and copyright messaging, and the archive containing the actual program files.</p>
<h2 id="exercise-description">Exercise Description</h2>
<p>In this exercise we will be examining a RPM with the usage of the rpm2cpio. The program rpm2cpio provided by the rpm package, extracts the cpio archive from the rpm package itself and allows us to view and even modify it’s contents.</p>
<h2 id="practicum">Practicum</h2>
<p>To download our package we are going to use yum and it’s “–downloadonly” and “–downloaddir=directory” options. From the man page for yum:</p>
<pre><code>--downloadonly
Don't update, just download. This is done in the background, so the yum lock is released for other operations. This can also be chosen by
typing 'd'ownloadonly at the transaction confirmation prompt.

--downloaddir=directory
Specifies an alternate directory to store packages.
</code></pre>
<p>For this exercise we are going to use the curl package as it has a minimal amount of files, but still gives a fairly decent example of what’s in an RPM package. We are now going to download this package running these commands (notice I am in my home folder):</p>
<pre><code>[student@desktop ~]$ sudo yum install --downloadonly --downloaddir=$(pwd) curl
</code></pre>
<p>Here’s the command explanation. By now hopefully you know what “sudo yum install” does. If not it is rather self explanatory. We are elevating our privileges to run the yum command using sudo and then calling install because we want it to install a package, but do we? No. We don’t want the package to install, we want to just download the package. So we tell yum that, after we say install, by using the “–downloadonly” option. Why then do we need to use the option “–downloaddir=$(pwd)” you ask? Great question! By default yum will download packages to a cache directory located in:</p>
<pre><code>"/var/cache/yum/"
</code></pre>
<p>that then gets organize in folders by cpu architecture, the version of RHEL,the repository name and then the packages folder. An example for epel packages for RHEL 7 would be:</p>
<pre><code>"/var/cache/yum/x86_64/7/epel/packages/"
</code></pre>
<p>So instead of us having to navigate to the above folder and maybe do some searching if we can’t remember the exact location, we tell yum to just place the RPM package in our present working directory. That is why we use $(pwd) that tells the --downloaddir= option to use the output of the pwd to place our RPM package in the present working directory, in this case the users home directory.</p>
<p>Great! If you have ran the command successfully you should now have the curl RPM package in your users home directory. Do a:</p>

