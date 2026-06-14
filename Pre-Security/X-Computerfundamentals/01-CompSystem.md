### Motherboard
The motherboard is like our body's skeleton and nervous system. It holds all the different components in place and connects them. On a typical desktop motherboard, you'll see different connectors that house all your components - CPU socket, RAM slots, expansion slots, and various ports. Every other component plugs into or connects through the motherboard. The image below shows a typical desktop motherboard.
<img width="593" height="392" alt="image" src="https://github.com/user-attachments/assets/e840672f-d2af-44bb-a289-bdf253bfa4ee" />

### CPU

The CPU (Central Processing Unit), often called the processor, is comparable to a part of our brain. Just like our brain continuously executes instructions (add numbers, pour milk in a bowl, and so on), a CPU does the same for a computer. Modern CPUs have multiple cores that handle instructions in parallel. The CPU connects to the motherboard via the CPU socket. The image below shows a typical CPU for a desktop.
<img width="545" height="360" alt="image" src="https://github.com/user-attachments/assets/ea8518eb-24d0-4eeb-ac69-00e26ae4fae0" />

### RAM

RAM (Random Access Memory) is comparable to our brain's short-term or working memory. When working on a task, we keep relevant information in mind temporarily. RAM does the same - it holds data that the CPU needs quick access to. RAM is volatile: when power is lost, all contents are gone. Modern RAM modules use technologies like DDR5 or DDR6 for increased speed and performance. The image below shows a RAM module for a desktop.
<img width="839" height="559" alt="image" src="https://github.com/user-attachments/assets/e25be3be-5bb7-48c1-a43a-73a16cf367b2" />

### Storage (SSD/HDD)

SSDs and HDDs are storage devices, comparable to our long-term memory. Just like fond memories are remembered permanently, data is saved long-term on storage devices. HDDs use older technology with moving parts, limiting performance. SSDs have no moving parts and use memory chips, allowing much faster speeds. HDDs remain popular for their large capacity at low cost. Storage connects via SATA cables or PCI Express slots. The image below shows an HDD on the left-hand side and an SSD on the right-hand side.
<img width="937" height="559" alt="image" src="https://github.com/user-attachments/assets/d14b9dfd-5c82-4bf2-b36b-860fd5312d0d" />

### Network Adapter

Just like we use our vocal cords to communicate with our environment, a network adapter lets computers communicate with other systems. Network adapters come in wireless and wired variants. Often they're embedded in the motherboard, but they can also be added as expansion cards. Network cards typically connect via PCI Express ports. The image below shows a plugin network card, typically used in desktops
<img width="839" height="559" alt="image" src="https://github.com/user-attachments/assets/5c660a49-8348-4ba7-9053-ac14b96249f2" />

### Power Supply (PSU)

Every system needs power. Just as our heart pumps blood to our organs, a PSU supplies energy to all system components. The PSU is essential and requires careful consideration - if components need more power than the PSU can provide, the system will fail. The PSU takes power from an outlet and distributes it via various connectors like the main motherboard connector and Molex connectors. The image below shows a PSU used in desktops.
<img width="839" height="559" alt="image" src="https://github.com/user-attachments/assets/b5d821c1-9dc4-442b-89f8-0ebc8fafecc5" />

### Graphics Card

The graphics card is comparable to the visual cortex of our brain. Our eyes pick up information and the visual cortex processes it into images. Similarly, the graphics card receives information from the operating system and programs, then outputs processed visual data to a monitor. Graphics cards connect to PCI Express slots on the motherboard. The image below shows a modern day graphics card used in desktops
<img width="897" height="559" alt="image" src="https://github.com/user-attachments/assets/fb7bbcb2-3874-4880-9d05-9e83166a8655" />

### Input/Output

Just like we have senses to obtain information for our brains to process and then act on, computers have input and output devices. Input devices include keyboards, microphones, mice, and scanners. Output devices include monitors, printers, and speakers. Common connectors for these peripherals include USB, HDMI, and DisplayPort. The image below shows a few of the basic I/O devices
<img width="839" height="559" alt="image" src="https://github.com/user-attachments/assets/1be8c205-345c-46ae-8e4e-76378ba801dd" />



### Computer Boot Process

## What is Booting?

 Booting is the process of starting a computer.
 It begins when the power button is pressed.
-Ends when the Operating System (OS) loads.

## Step 1: Press Power Button

 Power button sends a signal to the PSU.
 PSU starts supplying power to all components.

Example:
Power Button → PSU → Components receive power

## Step 2: Firmware Starts (UEFI/BIOS)

 Firmware starts after power is supplied.
 UEFI initializes hardware components.
 BIOS is the older version of UEFI.

Purpose:
 Prepare hardware for startup

## Step 3: POST (Power-On Self Test)

UEFI runs POST.
Checks if hardware is present and working.

Checks:
 CPU
 RAM
 Keyboard
 Storage devices

If a problem is found:
 Error message or beep sound.

Purpose:
 Verify hardware is functioning correctly.
 
## Step 4: Select Boot Device

 UEFI checks the boot order.
 Looks for a device containing an Operating System.

Examples:
SSD
HDD
USB Drive

Purpose:
 Find where the OS is stored.

## Step 5: Initiate Bootloader

 Bootloader is loaded from the boot device.
 Bootloader loads the Operating System into RAM.
 Control is transferred to the OS.
