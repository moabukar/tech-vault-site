## Linux Questions

<details>
<summary>What is Linux and difference between UNIX and Linux?</summary>

Linux is an open-source operating system based on the UNIX architecture. It was created by Linus Torvalds in 1991. UNIX, on the other hand, is a family of operating systems that was developed in the late 1960s at Bell Labs. The main differences between UNIX and Linux are:

- **License:** UNIX is proprietary, while Linux is open-source and free to use.
- **Development:** UNIX is developed by a few organizations (like IBM, Sun Microsystems, and HP), while Linux has a widespread community-driven development process.
- **Portability:** Linux is more portable and can be used on a wide range of hardware, whereas UNIX is limited to specific hardware platforms.
- **User base:** Linux has a broader user base, including personal computers, servers, and embedded systems, while UNIX is primarily used in enterprise environments.
</details>

<details>
<summary>What is the Linux kernel?</summary>

The Linux kernel is the core component of the Linux operating system. It is responsible for managing the system's resources, providing an interface between hardware and software, and facilitating essential tasks such as memory management, process scheduling, and input/output (I/O) operations.

</details>

<details>
<summary>What are inodes in Linux?</summary>

Inodes in Linux are data structures that store important information about files on a file system. Each file or directory in a Linux file system has an associated inode that contains metadata such as the file's size, permissions, ownership, timestamps, and the location of the file's data blocks on the disk.

When you create a file or directory, the file system assigns a unique inode number to it. The inode number serves as an identifier for the file, allowing the file system to access the inode's information and manage the file accordingly.

Here's a summary of what inodes store:

- File type (regular file, directory, symbolic link, etc.)
- File permissions (read, write, execute)
- Ownership (user and group)
- Timestamps (creation, modification, and access times)
- File size
- Number of hard links to the file
- Location of the file's data blocks on the disk

It's important to note that inodes don't store the file's name or the actual file data. The file name is stored in the directory that contains the file, which associates the name with the inode number. The actual file data is stored in separate data blocks on the disk, and the inode points to these blocks.

Inodes play a crucial role in managing files and directories within a Linux file system, providing an efficient way to access and manipulate file metadata.

</details>


<details>
<summary>Explain the Linux boot process</summary>

The Linux boot process consists of several stages that initialize the system and load the operating system. Here's a brief overview of the key steps:

BIOS/UEFI: When the computer is powered on, the BIOS (Basic Input/Output System) or UEFI (Unified Extensible Firmware Interface) performs initial hardware checks and locates the boot device.

Bootloader: The bootloader (e.g., GRUB) loads from the boot device and presents the available operating systems to the user. It then loads the Linux kernel and initial RAM disk (initrd) into memory.

Kernel initialization: The Linux kernel initializes hardware, sets up memory management, starts essential processes, and mounts the initial RAM disk, which contains essential drivers and tools needed during the boot process.

Root file system: The kernel switches the root file system from the initial RAM disk to the actual root partition on the disk, typically identified by its UUID or device name (e.g., /dev/sda1).

Init process: The first user-space process, called init (e.g., Systemd, SysVinit, or Upstart), starts and manages system services and processes during the boot process and the system's runtime.

Runlevel/target: Init process initializes the predefined runlevel (SysVinit) or target (Systemd), which determines the services and processes to run at startup.

Login prompt: Once all services and processes specified in the runlevel/target have started, the system displays a login prompt, indicating that the boot process is complete and the system is ready for use.

</details>

<details>
<summary>What is a zombie process?</summary>

A zombie process, also known as a defunct process, is a process that has completed its execution but still remains in the process table. This happens because the parent process has not yet read the child process's exit status, which is required to clean up the child process's resources and remove its entry from the process table.

Zombie processes don't consume any system resources, except for the process table entry, which includes the process ID (PID) and the exit status. The operating system keeps this information so that the parent process can eventually retrieve the exit status and perform the necessary clean-up.

More info on zombie processes below:

Typically, a well-behaved parent process will use the wait() or waitpid() system call to collect the exit status of its child processes. However, if the parent process doesn't do this, either due to a programming error or because the parent is still running and hasn't reached the point where it collects the exit status, the child process becomes a zombie.

Zombie processes are usually harmless, but if a system accumulates a large number of them, it could exhaust the available PIDs and prevent new processes from being created. To resolve this issue, the parent process should be fixed to correctly handle its child processes' exit status, or if the parent process is unresponsive or terminated, a system reboot might be necessary.

</details>

<details>
<summary>Difference between soft links and hardlinks?</summary>

Soft links and hard links are two types of file links in a Unix-like file system, such as Linux. They serve different purposes and have distinct characteristics:

**Soft Link (Symbolic Link):**

- A soft link is a separate file that points to the target file or directory by storing its path.
- If the target file is deleted, the soft link becomes a "dangling" link, pointing to a nonexistent file.
- Soft links can span across different file systems and partitions.
- Soft links can link to directories as well as files.
- When a soft link is created, the link count of the target file doesn't change.
- Soft links have different inode numbers than their target files.

**Hard Link:**

- A hard link is a direct reference to the data on the disk, sharing the same inode as the target file.
- If the target file is deleted, the hard link still points to the data, and the data remains accessible until all hard links to it are removed.
- Hard links can only be created within the same file system or partition.
- Hard links cannot link to directories, only to files.
- When a hard link is created, the link count of the target file increases by one.
- Hard links have the same inode numbers as their target files.

In summary, a soft link is a more flexible but less reliable type of link that can point to files or directories across file systems, while a hard link is a more robust link that directly references the file's data, but is limited to the same file system and cannot link to directories.

</details>

<details>
<summary>What are namespaces and c-groups?</summary>

Namespaces and cgroups (control groups) are two Linux kernel features that play a crucial role in implementing process isolation and resource management, especially in containerization technologies like Docker.

**Namespaces:**

Namespaces are a feature that provides process isolation by creating separate instances of certain system resources, which can only be accessed by processes within the same namespace. This isolation helps ensure that processes running in one namespace don't interfere with processes in another namespace

There are several types of namespaces, including:

- PID namespace: Isolates process IDs, allowing each namespace to have its own set of PIDs.
- Mount namespace: Isolates the file system mount points, so that each namespace has its own mount tree.
- Network namespace: Isolates network resources, providing each namespace with its own network stack, including interfaces, routes, and firewall rules.
- IPC namespace: Isolates inter-process communication resources, preventing processes in one namespace from communicating with processes in another namespace.
- UTS namespace: Isolates system identifiers like hostname, allowing each namespace to have its own unique hostname.
- User namespace: Isolates user and group ID mappings, enabling each namespace to have its own set of user and group IDs.

**Cgroups (Control Groups):**

Cgroups are a kernel feature that enables the management and limitation of system resources, such as CPU, memory, and I/O, for a group of processes. Cgroups help ensure fair distribution of resources, prevent resource starvation, and enforce limits on resource usage. Some of the key features of cgroups include:

- Resource limiting: Allows setting limits on resource usage for a group of processes, such as maximum CPU usage, memory consumption, and disk I/O bandwidth.
- Prioritization: Enables setting priorities for resource allocation among different cgroups, helping to ensure that critical processes receive sufficient resources.
- Accounting: Collects resource usage statistics for processes in a cgroup, which can be useful for monitoring, profiling, and billing purposes.
- Control: Provides a mechanism to start, stop, or freeze processes in a cgroup, allowing for better management of process groups.

In combination, namespaces and cgroups provide the necessary isolation and resource management capabilities required to build and run containers, enabling multiple containers to coexist on the same host without interfering with each other or consuming excessive resources.

</details>

<details>
<summary>What are symbolic links?</summary>

Symbolic links, also known as soft links or symlinks, are a type of file link in Unix-like file systems, such as Linux. A symbolic link is a special file that points to another file or directory by storing its path. Symbolic links serve as a reference to the target file or directory, allowing users and applications to access the target through the link.

Symbolic links are useful in various scenarios, such as creating shortcuts, linking to files or directories in different locations, or maintaining multiple versions of a file or directory. Some key characteristics of symbolic links are:

Symbolic links can point to files or directories, and they can span across different file systems and partitions.
If the target file or directory is moved or deleted, the symbolic link becomes a "dangling" link, pointing to a nonexistent location.
Symbolic links have different inode numbers than their target files or directories.
When listing files with the ls command, symbolic links are usually indicated by an "l" at the beginning of the file permissions and an arrow (->) pointing to the target file or directory.

To create a symbolic link in Linux, you can use the ln command with the -s option, followed by the target file or directory and the desired symlink name:

```bash
ln -s target_file symlink_name

Example:

ln -s /path/to/original/file.txt link_to_file.txt

This command creates a symbolic link named link_to_file.txt that points to the file located at /path/to/original/file.txt.
```

</details>

<details>
<summary>What are the different types of permissions in Linux?</summary>

In Linux, there are three main types of permissions for files and directories, which determine how users can interact with them. These permissions are classified into categories based on the user's relationship to the file or directory: owner, group, and others (sometimes referred to as "world" or "public"). The three types of permissions are:

Read (r): Read permission allows a user to view the contents of a file or list the contents of a directory. For files, this means the user can open and read the file. For directories, the user can view the names of files and subdirectories within that directory.

Write (w): Write permission allows a user to modify the contents of a file or make changes within a directory. For files, this means the user can edit, append, or delete the file's content. For directories, the user can create, rename, or delete files and subdirectories within that directory. Note that deleting or renaming files within a directory requires write permission on the directory itself, not the individual files.

Execute (x): Execute permission allows a user to run a file as a program or script, or enter and access a directory. For files, this means the user can execute the file if it is a binary executable or script with a proper interpreter (e.g., a shell script or Python script). For directories, the user can change their current working directory to that directory, and access files and subdirectories within it.

These permissions are usually represented using a combination of letters (r, w, x) and dashes (-) for each of the three categories: owner, group, and others. For example, the permission string -rwxr-xr-- indicates:

- The first character - indicates it's a regular file (a d would indicate a directory).
- The owner has read (r), write (w), and execute (x) permissions: rwx.
- The group has read (r) and execute (x) permissions, but not write permission: r-x.
- Others have only read (r) permission: r--.

Alternatively, permissions can also be represented using octal notation (base-8), where read, write, and execute permissions are assigned values of 4, 2, and 1, respectively. The permissions are then represented by a three-digit number, with each digit corresponding to the owner, group, and others. For example, the permission string -rwxr-xr-- can be represented as 754 in octal notation.

</details>

<details>
<summary>What is swap space?</summary>

Swap space is a dedicated area on a storage device (such as a hard drive or SSD) that functions as an extension of a computer's physical memory (RAM). It is used by the operating system to temporarily store data that does not fit into RAM or when the system experiences memory pressure due to high RAM utilization.

When the operating system needs more memory than is physically available, it can move the least recently used or less important data (called pages) from RAM to the swap space. This process is called "paging" or "swapping out." By doing so, it frees up space in RAM for more critical or frequently accessed data. If the swapped-out data is required again, the operating system will move it back into RAM, possibly swapping out other data in the process. This is called "swapping in."

Swap space can be implemented as a dedicated swap partition or a swap file. In Linux, you can manage swap space using commands such as swapon, swapoff, and mkswap. To check the current swap space usage on a Linux system, you can use the free or swapon -s commands.

</details>


<details>
<summary>What is chmod, chown and chgrp in Linux?</summary>

**chmod**
chmod (change mode) is a command used to change the permissions of a file or directory. You can set read, write, and execute permissions for the owner, group, and others. Permissions can be represented in octal notation (numeric) or using symbolic notation (letters).

Example: For example, to give the owner read, write, and execute permissions, the group read and execute permissions, and others only read permission, you would use:
- Using octal notation: `chmod 754 file.txt`
- Using symbolic notation: `chmod u=rwx,g=rx,o=r file.txt`

**chown**

chown (change owner) is a command used to change the ownership of a file or directory. You can specify a new owner and an optional new group for the file or directory.

Example: For example, to change the owner of file.txt to the user john and the group to developers, you would use:

`chown john:developers file.txt`

**chgrp**

chgrp (change group) is a command used to change the group assignment of a file or directory. You can specify a new group for the file or directory.

Example: For example, to change the group of file.txt to the group developers, you would use:

`chgrp developers file.txt`


</details>

<details>
<summary>What are cronjobs?</summary>

Cronjobs, also known as cron jobs or simply cron, are scheduled tasks that run automatically at specified intervals on Unix-like operating systems, such as Linux. The term "cron" comes from the Greek word "chronos," which means "time." Cronjobs are commonly used for automating repetitive tasks, performing system maintenance, running periodic backups, and other similar activities.

Cronjobs are managed by a daemon called "cron," which runs in the background and executes the scheduled tasks. The configuration for cron jobs is stored in a series of files called "crontabs" (short for "cron tables"). Each user on the system can have their own crontab, and there is also a system-wide crontab.

For example, a cron job that runs every day at 3:30 AM would have the following entry in the crontab:

`30 3 * * * /path/to/command arg1 arg2`

To manage cron jobs, you can use the crontab command with various options:

- crontab -l: List the current user's cron jobs.
- crontab -e: Edit the current user's cron jobs using the default text editor.
- crontab -r: Remove the current user's cron jobs.
- crontab -u USER: Perform an operation (list, edit, or remove) on the specified user's cron jobs (requires root privileges).

</details>

**Commands (basic & advanced):**

<details>
<summary>What does chmod +x FILENAME do?</summary>

The command chmod +x FILENAME is used to add execute permissions to a file in a Linux or Unix-like system. By adding execute permissions, you allow the file to be run as an executable or script, provided it has the appropriate format and interpreter (e.g., a shell script, Python script, or compiled binary). The +x option specifically grants execute permission to the owner, group, and others (all users).

For example, if you have a script named myscript.sh and you want to make it executable, you would run:

`chmod +x myscript.sh`

</details>

<details>
<summary>Which command will show you free/used memory?</summary>

the free command is used to display information about free and used memory. The command provides details on total, used, free, shared, and available memory, as well as swap space usage.

To use the free command, simply type free in the terminal, followed by any desired options. Some common options include:

- -b: Display memory usage in bytes.
- -k: Display memory usage in kilobytes (default).
- -m: Display memory usage in megabytes.
- -g: Display memory usage in gigabytes.
- -h: Display memory usage in a human-readable format, automatically choosing the appropriate unit (e.g., B, K, M, or G).
- -t: Display a line containing the total amount of physical memory and swap space.
- -s N: Continuously display memory usage information, updating every N seconds.

For example, to display memory usage in a human-readable format, you would run:

`free -h`

</details>

<details>
<summary>Which command will show me the current directory I am in?</summary>

`pwd`

</details>

<details>
<summary>How can I terminate an on going process?</summary>

`kill -9 PID`

</details>


<details>
<summary>Write the command that will display all .yaml files including permissions of each file? ()</summary>

`find . -type f -name "*.yaml" -exec ls -l {} \`;

</details>


<details>
<summary>How can I found the status of a process?</summary>

`ps -p <PID>` >> for 1 process

`ps aux` >> display a detailed list of all running processes on the system

</details>

<details>
<summary>What is the command to show all open ports?</summary>

`netstat -tuln`

</details>


<details>
<summary>How do you find the process ID of a running process in Linux?</summary>

- `ps -ef | grep <process_name>`
- `ps -ef | grep chrome`


</details>

<details>
<summary>How do you find the dependencies of a package in Linux?</summary>

Debian based (Ubuntu):
- `apt depends <packagename>`
- `apt-cache depends <packagename>`

Red Hat based (Fedora, CentOS)
- `dnf repoquery --requires <packagename>`


</details>

**Advanced:**

<details>
<summary>Does free memory exist on Linux?</summary>

On Linux systems, the concept of "free memory" may be a bit nuanced due to how Linux manages memory. While the term "free memory" is commonly used, Linux uses a sophisticated memory management system that maximizes the utilization of available memory for optimal performance.

In Linux, free memory refers to the memory that is not currently being used by any active processes or cached by the system. However, this does not mean that the memory is entirely unused or wasted. Linux takes advantage of available memory by utilizing it for disk caching, buffering, and other optimizations to improve system performance.

When you check the memory usage using tools like free or top, you will see several memory-related metrics, including "free," "used," "buffers," and "cache." These metrics represent different aspects of memory usage:

</details>

<details>
<summary>How can I check if a server is down?</summary>

1) The ping command is a simple and widely used tool to check the connectivity between your Linux system and a remote server

`ping <server_address>`

2) The telnet command allows you to establish a connection to a specific port on a server. By attempting to connect to a server's port, you can determine if it's up and accepting connections

`telnet <server_address> <port>`

3) If the telnet command is not available on your system, you can use nc (netcat), which provides similar functionality. 

`nc -zv <server_address> <port>`

</details>

<details>
<summary>What is inside /proc?</summary>

The `/proc` directory is a virtual filesystem that provides an interface to access process-related information dynamically. It contains various files and folders that provide information about running processes and system configuration.

- It holds details about each running process in separate folders identified by their process IDs (PIDs).
- It also provides system-wide information such as CPU details, memory usage statistics, network-related data, and kernel parameters.
- The content of /proc changes dynamically based on the current state of the system and running processes.

</details>

<details>
<summary>A process on the system can no longer log files, what can I do?</summary>

- **Check file permissions**: Ensure that the process has the necessary permissions to write to the log files or directories. Verify the ownership and permissions of the log files, and make sure they are writable by the user or group associated with the process
  
- **Verify available disk space**:  Insufficient disk space can prevent the process from writing to log files
- **Restart the process**
- **Check log file size limit**: Some processes have limits on the maximum size of log files they can generate
- **Check file system or disk errors**: Perform a file system check (fsck) on the relevant file system or check for disk errors using appropriate tools. File system errors or disk issues can sometimes interfere with file writing.
- **Verify logging configuration**: Ensure that the log file path and other settings are correctly specified
- **Check for system-level logging issue**: If multiple processes are unable to log files, there might be a system-wide issue with the logging infrastructure. Check system logs (e.g., /var/log/syslog or /var/log/messages) for any relevant error messages or indications of logging problems.

</details>

<details>
<summary>What is LILO?</summary>

- LILO, short for "LInux LOader," is a boot loader program used in older versions of Linux distributions.
- LILO's main function is to load the Linux kernel into memory and initiate the boot process.It presents a menu to the user, allowing the selection of the desired kernel or operating system to boot (if multiple operating systems are installed).
- LILO writes itself to the Master Boot Record (MBR) of the disk, overwriting the existing boot loader.
- Its configuration file (/etc/lilo.conf) specifies the location of the Linux kernel image and boot parameters.
- LILO has been largely replaced by other boot loaders, particularly GRUB (Grand Unified Bootloader), which offers more advanced features and flexibility.
- GRUB has become the default boot loader for many Linux distributions.

</details>

<details>
<summary>What are syscalls in Linux and how do they work?</summary>

- Syscalls are the interface between user-space applications and the kernel in Linux.
- They allow user programs to request services and access operating system resources.
- User programs invoke syscalls using special instructions, triggering a switch from user mode to kernel mode.

</details>

<details>
<summary>What is no route to host?</summary>

- "No route to host" is an error message that can occur in Linux when attempting to establish a network connection to a remote host

</details>

<details>
<summary>What is the difference between a hard link and a symbolic link in Linux? (WITH hands-on example)</summary>

**Hard Link**

- Direct reference to an existing file or directory.
- Creates a new name or entry pointing to the same data.
- Both the original file and hard link refer to the same underlying data.
- Deleting one does not affect the other.
- Essentially multiple names for the same file.

**Symbolic Link (Symlink)**

- Special file that acts as a pointer or shortcut.
- Contains the path or location of the target file or directory.
- Resolves the path to the target when accessed.
- Can point to files or directories on different file systems or even non-existent or moved targets.
- Deleting the original file or directory doesn't automatically delete the symlink.
- Symlink becomes "broken" if the target is deleted or moved.

**Example**

Assume we have a file named "original.txt" with the content "Hello, world!" in the directory /home/user/.

Hard Link:
  - Create a hard link named "hardlink.txt" to "original.txt" using the ln command: `ln /home/user/original.txt /home/user/hardlink.txt`
  - Both "original.txt" and "hardlink.txt" now refer to the same file and share the same data.
  - If you modify the content of "original.txt", the changes will be visible when accessing "hardlink.txt" and vice versa.
  - Deleting either "original.txt" or "hardlink.txt" will not affect the other file.

Symbolic (soft) link:
  - Create a symbolic link named "symlink.txt" to "original.txt" using the ln command with the -s option: `ln -s /home/user/original.txt /home/user/symlink.txt`
  - "symlink.txt" is a separate file that acts as a pointer to "original.txt".
  - If you modify the content of "original.txt", the changes will be reflected in "symlink.txt".
  - Deleting "original.txt" will not automatically delete "symlink.txt", but accessing "symlink.txt" will result in a broken link if the target is not available.

In summary, with a hard link, you have multiple names for the same file sharing the same data, while with a symbolic link, you have a separate file acting as a pointer to another file or directory.

</details>

**Linux Internals & Advanced (Scenario based questions):**

<details>
<summary>Explain the linux boot process (detailed) </summary>

- BIOS/UEFI: When you power on the computer, the Basic Input/Output System (BIOS) or Unified Extensible Firmware Interface (UEFI) firmware is invoked. It performs hardware initialization, self-tests, and determines the boot device.

- Bootloader: GRUB (the most common Linux bootloader) loads the operating system into memory.

- Kernel Initialization: Once the bootloader hands off control, the Linux kernel is loaded into memory. It starts executing from its entry point. The kernel is responsible for managing system resources, such as memory, processes, devices, and file systems.

- Init Process: The first user-space process, known as the init process, is started by the kernel. The init process has a process ID (PID) of 1 and is responsible for initializing the system further. In modern Linux distributions that use systemd as the init system, the init process is replaced by the systemd process.

- Init System/Services: System services and daemons are launched.

- Login Manager: A login screen or prompt appears for user authentication.

- User Session: After login, the user's session starts with the desktop environment.

In summary, the boot process involves firmware initialization, bootloader loading the OS, kernel taking control, system initialization, login prompt, and user session start.

</details>

<details>
<summary>A process on the system can no longer log files, how would you debug?</summary>

- **Check File Permissions**: Verify that the process has proper permissions to write to the log files or directories. Ensure that the file permissions and ownership are correctly set to allow the process to write logs.
- **Review Log File Configuration**: Check the configuration file (e.g., /etc/rsyslog.conf or /etc/syslog-ng/syslog-ng.conf) to ensure that the log files and their destinations are correctly defined.
- **Check Disk Space**: Insufficient disk space can prevent file logging. Use the df command to check the available disk space. Ensure that the filesystem containing the log files has enough free space to accommodate new logs.
- **Check System Logs**: Review the system logs (/var/log/syslog, /var/log/messages, etc.) for any relevant error messages or indications of issues related to the logging process. Look for log entries related to the process and check if any error messages are reported.
- **Restart the Logging Service**: Restart the logging service associated with the process (if you use rsyslog for logging) >> `sudo systemctl restart rsyslog`

</details>

<details>
<summary>How can I check if a Linux system is healthy?</summary>

- **System Resource Usage**: 
  - Monitor CPU usage: Use tools like `top` or `htop` to check CPU usage and identify any processes consuming excessive CPU resources.
  - Check memory usage: Use commands like `free` or `top` to examine memory usage and ensure sufficient free memory is available.
  - Monitor disk usage: Use `df` or `du` commands to check disk space utilization and identify any partitions nearing capacity limits.

- **System Services and Processes:**: 
  - Check running processes: Use `ps` or `top` to view running processes and ensure critical services are active.
  - Verify system services: Use service management tools like `systemctl` (systemd) or `service` (init) to check the status of essential services.

- **System Logs**: 
  - Review system logs: Examine log files in `/var/log/` (e.g., `/var/log/syslog`, `/var/log/messages`) for any error or warning messages related to system components, applications, or hardware.
  - Monitor log files in real-time: Use the `tail` command with the -f option to track log files as new entries are added.

- **Network Connectivity**: 
  - Check network interfaces: Use `ifconfig` or `ip` command to verify the status and configuration of network interfaces.
  - Test network connectivity: Use `ping` or `traceroute` to test connectivity to remote hosts or check for network latency or packet loss.

- Hardware monitoring?
- Security and updates?
- Backup and recover?

</details>

<details>
<summary>What happens when you type "ls" or "cd" into a terminal? (go deep and talk about what happens behind the scenes - kernel level)</summary>

- The terminal program receives the command you typed and identifies the command and any arguments.

- The shell then searches for the location of the command binary within the directories specified in the `PATH` environment variable. It looks for an executable file with a matching name.

- Once the command binary is located, the shell initiates a system call, specifically the `execve()` system call, to load the command into memory and execute it.

- The kernel allocates memory for the command and sets up file descriptors for input, output, and error handling.

- The kernel performs a context switch, transitioning from the shell to the command.

- The command binary is loaded into memory, and its execution begins.

- As the command executes, it may make additional system calls to interact with the kernel. For example, the "ls" command might make system calls to read directory contents or retrieve file metadata.

- The command may manipulate the terminal's display using control codes.

- Once the command completes, the kernel returns control to the shell.

</details>

<details>
<summary>How can I check if a server is down?</summary>

- The ping command is a simple and widely used tool to check the connectivity between your Linux system and a remote server >> `ping <server_address>`
- The telnet command allows you to establish a connection to a specific port on a server. By attempting to connect to a server's port, you can determine if it's up and accepting connections >> `telnet <server_address> <port>`
-  If the telnet command is not available on your system, you can use nc (netcat), which provides similar functionality >> `nc -zv <server_address> <port>`

</details>

<details>
<summary>How are Linux processes killed on a lower level?</summary>

- In Linux, processes can be terminated or killed at a lower level using signals. Signals are software interrupts sent to a process to convey various notifications or requests. They can be used to terminate a process gracefully, forcefully, or perform other actions

  - SIGTERM (Signal 15): This is the default termination signal sent to a process when you use the kill command without specifying a signal. It politely requests the process to terminate and allows it to perform cleanup operations before exiting.

  - SIGKILL (Signal 9): This signal forcefully terminates a process. It does not allow the process to perform any cleanup or graceful shutdown procedures. The process is immediately terminated.

  - SIGINT (Signal 2): This signal is generated when you press Ctrl+C on the keyboard. It is typically used to interrupt or terminate a process that is running in the foreground.

  - SIGQUIT (Signal 3): Similar to SIGINT, this signal is generated when you press Ctrl+\ on the keyboard. It usually requests a process to terminate and provides a core dump for debugging purposes.

</details>

<details>
<summary>I have accidentally entered `cd/bin` and done `chmod 644 chmod` - how can I fix this?</summary>

**Method 1 - Copy the file from another system**:
- If you have compatible systems, you can always just grab a copy of chmod from another server using scp or rsync.

```sh
cd /bin
mv chmod chmod.orig
scp twin:/bin/chmod .
diff chmod chmod.orig
```

**Method 2 - Restoring from Backup**:

- If you have a recent backup of the affected system, you can restore the correct permissions of the `chmod` command by replacing it with the version from the backup. Copy the `chmod` binary from the backup location to the `/bin` directory, ensuring that the correct permissions are retained.

Method 3

</details>

<details>
<summary>How would you troubleshoot a network connectivity issue in Linux?</summary>

- **Check Network Configuration**: Verify that the network configuration is correct. Use commands like `ifconfig` or `ip` to check the status of network interfaces, IP addresses, subnet masks, and gateway settings.
- **Ping**: Use the ping command to test basic connectivity to a remote host or IP address. For example, `ping 8.8.8.8` pings Google's public DNS server. If the ping is successful, it indicates that network connectivity is established.
- **Check DNS Resolution**: If you are having trouble accessing websites by domain name, check if DNS resolution is functioning correctly. Use the `nslookup` or `dig` command to query DNS servers and verify if they are returning the correct IP addresses for the given domain
- **Check Routing**: Use the `traceroute` or `tracepath` command to trace the route packets take to reach a destination. It helps identify any network hops or routing issues along the path.
- **Firewall Configuration**: Review the firewall configuration to ensure it is not blocking the required network traffic. Check the rules in tools like `iptables`, `ufw`, or other firewall management tools.
- **Check Network Services**: Ensure that required network services, such as DHCP (Dynamic Host Configuration Protocol) or DNS, are running and functioning properly. Use commands like `systemctl` or `service` to check the status of specific services.
- **Inspect Network Logs**: Check system logs in `/var/log/` (e.g., `/var/log/syslog`, `/var/log/messages`) for any relevant error messages related to network interfaces, services, or connectivity issues.
- **Test Connectivity with Different Tools**: Use network troubleshooting tools like `netcat` (nc), `curl`, or `wget` to test connectivity to specific ports or services on remote hosts.


</details>

<details>
<summary>How do you troubleshoot a connectivity issue with a remote server in Linux?</summary>

- Check Network Connectivity >> `ping <server_ip_or_hostname>`
- Verify DNS Resolution >> `nslookup <server_hostname>` or `dig`
- Check Firewall Settings: Verify that your local firewall or any intermediate firewalls are not blocking the necessary network traffic. Temporarily disable the firewall or configure it to allow the specific ports or protocols required to communicate with the remote server.
- Verify Port Connectivity >> `telnet <server_ip_or_hostname> <port_number>`
- Trace Route: Use the traceroute or tracepath command to trace the network path to the remote server >> `traceroute <server_ip_or_hostname>`
- Review Server Logs: Examine the server's logs for any error messages or indications of connectivity issues. Check logs related to the specific services running on the server, such as Apache logs for web server issues.
- Check Server Services: Ensure that the necessary services on the remote server are running and properly configured

</details>

<details>
<summary>How do you view and edit the system logs in Linux?</summary>

- View logs >> `cat /var/log/syslog` - use SUDO
- Edit logs >> `vim /var/log/syslog` - use SUDO

</details>


<details>
<summary>Which command do you use to copy one file from one server to another?</summary>

- scp

</details>

<details>
<summary>Which command do you use to copy directories from one server to another?</summary>

- scp -r

</details>
