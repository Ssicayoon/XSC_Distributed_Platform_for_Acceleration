# XSC_Distributed_Platform_for_Acceleration
This is the repository for Xilinx Summer Camp 2020.
The target of our team is construting a distributed platform for acceleration.
Our project is based on two ZCU102 boards and xapp1305.

We have established an FPGA-based distributed platform for acceleration through Ethernet port on ps side.
One of two boards (mother board) send a file to a certain folder, while the other board (child board) is watching that folder. 
When child board receives a file in the folder, it will execute the program for acceleration imediattely.

## How to run the distributed platform for acceleration

### Step 1
Copy files in */sd_images/shared_images_for_boards/* to SD cards.
Copy the *.exe* in *mother_board_exe* folder to the SD card of mother board.
Copy the *.exe* in *child_board_exe* folder to the SD card of child board.

### Step 2
Start boards from SD card and we need to set ip addresses for each one since they are connected directly through Ethernet cable.
The mother board is set to 192.168.32.1 and the child board is set to 192.168.32.100.
![Start from SD card](https://github.com/Ssicayoon/XSC_Distributed_Platform_for_Acceleration/blob/master/doc_images/set_ip.png?raw=true)

### Step 2
Start a watcher on the child board. 
The watcher program watches the *./* folder, which means */run/media/mmcblk0p1* folder.
Once there is a file created, accessed, deleted, changed in the watched folder, the watcher program will execute the program for acceleration, which is a example *vadd* from Vitis.
![Start a watcher](https://github.com/Ssicayoon/XSC_Distributed_Platform_for_Acceleration/blob/master/doc_images/command_for_watch.png?raw=true)

### Step 4
Send a test file as a trigger from mother board to child board through *scp* command. Note that the password of child board is needed here.
![Transfer file](https://github.com/Ssicayoon/XSC_Distributed_Platform_for_Acceleration/blob/master/doc_images/scp_command_for_data_transfer.png?raw=true)

## Step 5
The program for acceleration is executed after the watcher finds a file is created in the folder.
![Execute program](https://github.com/Ssicayoon/XSC_Distributed_Platform_for_Acceleration/blob/master/doc_images/receive_control_signal_and_execute_program.png?raw=true)
