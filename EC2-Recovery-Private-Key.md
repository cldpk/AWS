=========================================================
Q) How To Access / Recover EC2 Instance in AWS, if .pem file is lost?
==========================================================

1. Stop the ec2_instance (name it as db_server)

2. Detach ebs root volume from db_server

3. Create new ec2_instance (name it as helper_ec2) ( choose new key pair and save .pem file )

4. Attach db_server ebs root volume to helper_ec2 instance

5. Connect to helper_ec2_instance using mobaxterm with newly created .pem file

6. Execute below commands

# lsblk
# ls /mnt
# sudo mount -o nouuid /dev/xvdf1 /mnt
# cp /home/ec2-user/.ssh/authorized_keys /mnt/home/ec2-user/.ssh/authorized_keys
# sudo umount /mnt

7) Stop the helper_ec2 instance and detach the db_server volume and attach it back to db_server.

Note: Please use device name as /dev/xvda.

8) Start the db_server and connect to it using newly created .pem file





