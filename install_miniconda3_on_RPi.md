This procedure works perfectly on `Raspberry Pi 3 Model B+ (Rev. 1.2)` with un-touched installations of:
+ `Raspberry Pi OS` (any version) 
+ `Ubuntu` (any version) 
+ `Kali Linux` (any version)
 
{USER}: pi 
> **Note:** You may have different username, so change the fields accordingly.
 
Install Miniconda 3: 
 
```
cd /home/pi/Downloads \
> wget http://repo.continuum.io/miniconda/Miniconda3-latest-Linux-armv7l.sh \
> sudo /bin/bash Miniconda3-latest-Linux-armv7l.sh 
```
 
Press the **spacebar** to *instantly* move to the end of the license agreement (else keep on pressing the **enter key** to go line-by-line).
Accept the license agreement with `yes`.
 
When asked to specify the installation directory, change default directory to:
```
/home/pi/miniconda3
```
 
For all other prompts, enter `yes`.
 
After the **successful** completion of Installation, do: 
```
sudo nano /home/pi/.bashrc
```
Move to the End of the file and add:
```
export PATH="/home/pi/miniconda3/bin:$PATH"
```
 
Now, there are two ways to activate the installation through bash and then test the installation.
1. Run the following command:
```
source /home/pi/.bashrc
```
OR

2. reboot your machine.

```
sudo reboot -h now
```
 
To test the installation, run:
```
conda
```
The above command will display a whole lot of options and arguments that can be used with `conda`.
 
Now do:
```
conda update --all
```
If Conda update gives a write permission error for the directory, do:
```bash
sudo chown -R pi miniconda3
```
