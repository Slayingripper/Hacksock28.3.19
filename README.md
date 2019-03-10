# Hacksock28.3.19

## Prerequisites 
any linux distro (ubuntu shell on windows is fine) 
Raspberry pi
Pifm (LIBARY)
Putty
Arduino IDE 


## Transmiting FM signals from a raspberry pi 
Firstly lets do a git clone of the PiFm libary
```
git clone https://github.com/rm-hull/pifm.git
```

```
cd pifm
```

It uses the hardware on the raspberry pi that is actually meant to generate spread-spectrum clock signals on the GPIO pins to output FM Radio energy. This means that all you need to do to turn the Raspberry-Pi into a (ridiculously powerful) FM Transmitter is to plug in a wire as the antenna (as little as 20cm will do) into GPIO pin 4 and run the code posted below.

The python library calls a C program. The C program maps the Peripheral Bus (0x20000000) in physical memory into virtual address space using /dev/mem and mmap. To do this it needs root access, hence the sudo. Next it sets the clock generator module to enabled and sets it to output on GPIO4 (no other accessible pins can be used).

Modulation is done by adjusting the frequency using the fractional divider between 103.325Mhz and 103.275Mhz, which makes the audio signal.


## Steganography

Steganography is the art of hiding something in somehting else . Its very usefull when you need to hide stuff (like your porn folder ^^) doing this is easy and can be expanded very easily (but can be easily detected if you are not carefull. For starters pic some files you want to hide a put them in a zip folder you will also need a JPG image (preferebly a high quility one).

Now it is clear that we want to hide  youfiles.zip inside apicture.jpg image. We will use the Linux cat command  which has different functions like displaying files, creating new ones and combining copies of them. The cat command will read the images file first, secret_files.zip and we will concatenate them   together.   After you have opened the terminal change directory to the  directory  where you have your files, mine are inside  Desktop, so i type cd Desktop/articles in my terminal and press Enter.

Make sure all the files are inside the directory by using the ls command  which stands for listing all files and subdirectories inside a directory and copy your filenames inside a text document because you will need them in the next command.  Time to hide my zip archive inside my image.

```
cat myimage.jpg yourfiles.zip > newimage.jpg
```

### Exaplnation

    cat reads the image file
    cat reads the zip file
    cat  concatenates the image and the zip file togeather  in a new file, bugatti.jpg ( You can put any name you like)


Press Enter and a new  file will be created. The new file is newimage.jpg which  looks like a regular image file but if we try to operate with unzip command on it ,  the unzip command will extract  the zip archive that is inside the image.

TYpe 
```
ls
```
and your file will should be there

The file that is important to us is youfile.jpg  because  our secret files are inside this image so feel completely free to delete other files when you  use this method. It looks like a normal jpeg file and it
will open as an image

If notice the file is larger than before that is because we have hidden files in the image its self (and is a dead give away if its too much to an experienced user).

To pull out the files just use

```
unzip yourfile.jpg

```

This can become really handy when you want to sent an email and hide something if someone where to hijack the receipient or inject a payload in a system by just sending an image . 

## Bash scripting essentials 

Bash scripts are very handfull in doing time consuming tasks in very little time the unix "bash" terminal 


first lets write a sample bash script all bash scripts start with #!/bin/bash so we can point the system to the right place 

Here is our first bash shell script example:

```
#!/bin/bash
# declare STRING variable
STRING="Hello World"
#print variable on a screen
echo $STRING
```

Navigate to a directory where your hello_world.sh is located and make the file executable:
```
chmod +x hello_world.sh 
```

Now you are ready to execute your first bash script:

```


./hello_world.sh 

```
Lets make a long but simple update script that diplays system info and update the system packages but also removes the old packages (saving space).

```
#!/bin/bash

RED="\033[1;31m"
GREEN="\033[1;32m"
NOCOLOR="\033[0m"

echo

echo -e "step 0: ${RED}Show Splash${NOCOLOR}"

screenfetch

echo

echo -e "step 1: ${GREEN}pre-configuring packages${NOCOLOR}"
sudo dpkg --configure -a

echo

echo -e "step 2: ${GREEN}fix and attempt to correct a system with broken dependencies${NOCOLOR}"
sudo apt-get install -f

echo

echo -e "step 3: ${GREEN}update apt cache${NOCOLOR}"
sudo apt-get update

echo

echo -e "step 4: ${GREEN}upgrade packages${NOCOLOR}"
sudo apt-get upgrade

echo

echo -e "step 5: ${GREEN}distribution upgrade${NOCOLOR}"
sudo apt-get dist-upgrade

echo

echo -e "step 6: ${GREEN}remove unused packages${NOCOLOR}"
sudo apt-get --purge autoremove

echo

echo -e "step 7: ${GREEN}clean up${NOCOLOR}"
sudo apt-get autoclean

echo

```

### Explanation 

Echo command will display the progress on screen 
${Green} changes the colour of the command so it becomes more clear on the screen 
Screenfetch displays an acii graphic of the distributions LOGO on the screen (just for fun)

## Common linux crash fix

If you ever had something crash on linux there is always a pop up that shows up(on start up) which is quite annoying 
(IF YOU KNOW WHAT THE PROBLEM IS USE THIS )

```
sudo rm /var/crash/*

```
just add this to a .sh file and the crash will be gone on next start up . This just clear the crash logs of the system















