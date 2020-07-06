**!!CAUTION!!** Do the following steps only if you understand what these commands will do. 
 
**!!CAUTION!!** Do not append `sudo` to any of the `rm` commands as it might delete some additional directories. 
 
 
> Now that _you have been **warned**_, let's remove the Miniconda3 Installation. 
 
You can remove the entire Miniconda3 directory by using:
```
rm -rf ~/miniconda3
```
 
After the **successful** completion of directory removal, do: 
```
sudo nano /home/pi/.bashrc
```
Move to the End of the file and remove:
```
export PATH="/home/pi/miniconda3/bin:$PATH"
```
If not found, you are good to go!
 
 
Remove the following hidden file and folders that may have been created inside the `home` directory:
 
+ `.condarc` file
+ `.conda` directory
+ `.continuum` directory
 
By running:
```
rm -rf ~/.condarc ~/.conda ~/.continuum
```
 
 
Now, there are two ways to reflect the uninstallation through the terminal.
1. Run the following command:
```
source /home/pi/.bashrc
```
OR 

2. reboot your machine.

```
sudo reboot -h now
```
