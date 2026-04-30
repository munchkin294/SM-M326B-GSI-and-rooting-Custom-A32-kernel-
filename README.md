# SM-M326B-GSI-and-rooting-Custom-A32-kernel-
Samsung Galaxy M326B "CrDroid super.img", "A32 custom kernel Magisk boot.img" and a "Null vbmeta.img"


okeyy gng we gon install the CrDroid GSI with magisk and a custom A32 kernel on yo phone


**IMPORTANT**

* Check your phone's model this is Samsung Galaxy M32 5G,SM-M326B, Stock firmware: M326BXXSCCYD2 

* Make sure you install your phone's stock firmware from bifrost in case of corrupted flashing or any problems.

* Here the bifrost folder I have (I kinda forgot the link i got it from so I uploaded it on my drive hope that's fine)

  Here: https://drive.google.com/drive/folders/1MBiyVR5VGIsewaWLctGdqieeLVXKf9A9?usp=drive_link

* This process will wipe away your whole phone so either keep backup or stay prepared for the loss i guess

* you need a linux machine (duck windows)

* I'm not responsible for any retarded bootloops, I'm js sayin what I did here
  

**FLASHABLE IMAGES**

  Here are the super.tar (crDroid), boot.tar (A32 kernel and magisk),vbmeta.tar (normal one that works)

**Vbmeta.tar**

 Here: https://drive.google.com/file/d/1zjIhYqbuTXcQZ1vcdBZcrml6Xuv7XOW3/view?usp=drive_link

**Boot.tar**
  
  I got it patched from Magisk: https://topjohnwu.github.io/Magisk/
  
  And I got the custom A32 kernel from: https://xdaforums.com/t/custom-kernel-for-a32-5g-gsi.4773514/

we are using the custom kernal of A32 5G because well I couldn't find the M32 5G one online and A32 and M32 both have dimensity 720 processor, workes so fine

Here: https://drive.google.com/file/d/1ZR63xW8fw7XQyzGXTjLsMNxjhLSC_-Wg/view?usp=drive_link

**super.tar**

I got the crDroid GSI for Android 14 from: https://github.com/naz664/crDroid_gsi/releases/tag/v2025.03.08

And these are the exact byte sizes of the partitions of this model if u ever wanna check

    --device super: 7864320000
    --group main: 7860125696
    --partition system: 4977426432
    --partition vendor: 906416128
    --partition product: 1397661696
    --partition odm: 4349952    

*I think they are trustworthy because I wrote em in my dad's diary*

Here: https://drive.google.com/file/d/17CxkACRa0tAqAVAkamG1h5CWKyTDy5C1/view?usp=drive_link 

**UNLOCKING THE BOOTLOADER (This might voild warrenty and the knox bit will be fused riskyy)** 

So guys let's start working first u gtta go "settings> about phone> software information> build number" and tap it six or seven times to unlock dev options.

In dev options look for "OEM unlocking" and toggle it on

get a USB C to A cable (i use my charging cable) and plug it into your Linux machine (for me the Dell vostro from 2014 which runs Linux on nomodeset)

then the fun part, power off your phone press volume up and volume down together and plug the USB into your phone

you will see a teal blue screen as "Download Mode" you have to do nothing, Just press the volume up for a while and your bootloader is unlocked 

(Fun fact: I was one dumb click close to bricking my phone because I had a failed flash and I thought locking the bootloader while the OS is practically broken will help, no, download mode is the only place that will save you if you soft-brick)

(Another fun fact: your data i all wiped off after that unlocking bootlader thingy)

**INSTALLING ODIN4**

Now I used Odin4, you guys can get it from the link: https://github.com/Adrilaw/OdinV4

Now make sure the permisssions for the user are set to "read and write" while you check the properties, right click the folder in which your executable is and click "open in terminal" there make it executable by running "sudo chmod +x odin4" and try running it by using "./odin4" 

also, while flashing with this make sure to use "sudo" because usually it just ignores you without that and flashes nothing in nanoseconds

and MAKE SURE you don't flash any different firmware it's just gonna waste time 

**SETTING UP PC CONNECTION (kinda won't help but is useful if u wanna check for any logs or if your fastboot isn't as retarded as mine)**

now you need to install adb walkie talkie in yo pc by running 

"sudo apt update" "sudo apt install android-tools-adb android-tools-fastboot"

and you need to toggle the "USB Debugging" ON 


while your PC is connected it a notification will pop up you have to hit ALLOW 


now type "adb devices" in your terminal and it show come as an authorized device

**FLASHING (NO TWRP or FastbootD just you and Odin4**

now all that is done, you need to keep the images (tar boxes) i just gave you in one folder with odin in there

now you see you have a super, boot and vbmeta that goes in the AP 

so we will flash them one by one (really it's just subjective)

**vbmeta**

now u have to go to download mode and connect your phone to your PC with the USB cable

and then on yo PC fisrt open the folder wherever you have the images saved in a terminal (right cick and select "open in terminal") 

in the terminal run "sudo ./odin4 -a vbmeta.tar"

and it will flash, now let the OS boot and in the terminal type " adb shell getprop | grep -i "state\|verified\|bootloader" "

there, if you see [ro.boot.verifiedbootstate]: [orange]

youre good to go to step two 

**boot**

we are doing this before because i want to

run "sudo ./odin4 -a boot.tar"

get to the OS and see if Magisk is working, now you have a custom kernel so you can easily install the GSI with no bootloops

**super**

now go back to download mode 
and run "sudo ./odin4 -a super.tar"


this one will take a while (or it's just cuz of my ancient artifact machine), tbh i had to pack it myself by extracting firmwares and injecting system because apparenty it's not 2016 anymore but worth the effort

and gng right after is says success, jump to android recovey (volume up and power when the phone restarts) and select "format data" and then boot to the OS, it's necessary

now you would log in to crDroid yaey! :D


Thanks for reading, i will post tut of "how to edit the super,boot and vbmeta yourself" later

bye bye 












  
  

  

   
