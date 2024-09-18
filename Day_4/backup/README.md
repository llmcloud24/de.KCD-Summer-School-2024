## Day 4: Backup

### Hands-on: Pre-requisites

We will first make some space outside of our running VM to store our backups.

With OpenStack, we have 2 main options. One is to create **Volumes**, that acts like an additional hard drive. You can create new volumes and attach them to your running VM, but each volume can only be attached to one VM at a time.

The other option is to create **Shares**, which are basically networked storage that can be shared and accessed by multiple VMs. Similar to **Volumes**, you can also easily create them and define which VMs should get access to it.

Let's focus on **Shares** for now, and revisit the **Volumes** later if we have time.

### Hands-on: Creating New NFS Share

Create a new **Share** with the correct settings as shown in the figures.
 - Left sidebar > Share > Shares > Create Share button (next to the search bar)
 - At the "Create Share" page please make sure:
 	- Name: `<jdoe>-nfs-backup` (if your name is John DOE)
 	- Description: `NFS share for JDOE's backup`
 	- Share Protocol: `NFS`
 	- Size: `10` GiB
 	- Share Type: `isilon-denbi`
 	- Rest can be left empty
 	
### Hands-on: Adding your VM to your Share

After creating your Share, we need to make sure your VM is allowed to access it.
 - Find your newly-created Share's name from the list of shares, and click the arrow beside the "Edit Share" button, and then click ok "Manage Rules"
 - Click the "Add rule" button and use the following settings:
 	- Access Type: `ip`
 	- Access Level: `read-write`
 	- Access To: `<VM's IP, e.g., 10.0.X.X>`
 	- Click "Add" button

### Hands-on: Accessing your Share from your VM

Now that you've successfully created a Share and configured it to allow access from your VM, you can finally access it from your VM.

Click your newly-created Share's name, and you will see a "Share Overview" page.
 - Pay attention to these:
 	- Share Type: `isilon-denbi`
 	- Access Rules: VM's IP, Access Level, etc are listed correctly
 	- Export locations path: We will need to copy the one that starts with `manila-prod.isi...`

Now, SSH into your VM and run these commands:
 - `sudo apt install -y nfs-common rsync`
 - `sudo mkdir /nfs`
 - `sudo chown ubuntu:ubuntu /nfs`
 - `sudo mount <manila-prod.isi...> /nfs`
 - `df -h`

>[!NOTE]
>Do you see your NFS share in the output of `df -h`?
>Does it match what you created via the dashboard?
 
And now you should be able to browse into the `/nfs` directory and create some files there:
 - `cd /nfs`
 - `touch hi.txt`

If you want the share to be automatically mounted when your VM starts, you can add it into your `/etc/fstab` file:
 - `sudo nano /etc/fstab`
 - add this to the very end of the file as a new line:
 - `<manila-prod.isi....> /nfs nfs defaults,rw,nofail 0 0`
 - Press `Ctrl`+`O` and then `Enter` to write the changes to the file
 - Then press `Ctrl`+`X` to exit `nano`
 
Now, you can reboot your VM by doing `sudo reboot now`, and then SSH into it again after a few seconds.

If everything goes right, you should be able to see that `/nfs` is already available right away:
 - `df -h`
 - `ls /nfs`


### Hands-on: Making some copies of toy data

First, let's get some toy data to practice our backup skills.
 - `cd ~`
 - `git clone https://github.com/fwten/llmcloud24_toy_data.git`
 - `cd llmcloud24_toy_data`
 - `ls -lah`

Now, you can explore these files and data first to get a better idea of what they are, how they look like, what to expect and so on.

Once you're ready, you can try to make backups of this folder and its files to your mounted Share at `/nfs`:
 - `tar -cvf /nfs/llmcloud24_toy_data.tar ~/llmcloud24_toy_data`
 - `rsync -aP ~/llmcloud24_toy_data /nfs`
 - `tar -cvf ~/llmcloud24_toy_data.tar ~/llmcloud24_toy_data`

>[!TIP]
>The `tar` command will create a `.tar` archive file containing all the files, just like a zip file.
>The `rsync` command is a fancier way to copy or `cp` files, and you get to see the progress while this is being done.

Now you've created some copies of your data. Let's try to find out a little bit more about them:
```
# check the original size of our folder
$ du -sh ~/llmcloud24_toy_data/
10M	/home/ubuntu/llmcloud24_toy_data/

# check the size of the copied folder in /nfs
$ du -sh /nfs/llmcloud24_toy_data/
16M	/nfs/llmcloud24_toy_data/

# check the size of the tar file in our home folder
$ du -sh ~/llmcloud24_toy_data.tar 
9.8M	/home/ubuntu/llmcloud24_toy_data.tar

# check the size of the tar file in /nfs
$ du -sh /nfs/llmcloud24_toy_data.tar
12M	/nfs/llmcloud24_toy_data.tar
```
>[!NOTE]
>Interestingly, they seem to differ in size, even though they're supposed to be copies!
>Do you know why? Is there something wrong?

```
$ md5sum ~/llmcloud24_toy_data.tar 
87443e0c6129f374d846a532e01bf9ec  /home/ubuntu/llmcloud24_toy_data.tar
$ md5sum /nfs/llmcloud24_toy_data.tar 
87443e0c6129f374d846a532e01bf9ec  /nfs/llmcloud24_toy_data.tar
```
