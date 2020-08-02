# XSC_Distributed_Platform_for_Acceleration
This is the repository for Xilinx Summer Camp 2020.
The target of our team is construting a distributed platform for acceleration.
Our project is based on two ZCU102 boards and xapp1305.

We have established an FPGA-based distributed platform for acceleration through Ethernet port on ps side.
One of two boards (mother board) send a file to a certain folder, while the other board (child board) is watching that folder. 
When child board receives a file in the folder, it will execute the program for acceleration imediattely.

## Configuration
![Start from SD card]()
