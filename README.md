# 🚀 Customised Virtual File System (CVFS)

## 👨‍💻 Author
**Pranav Manoj Narkhede**  
Technology: **C Programming (System Programming)**  

---

# 📌 1. Project Overview

The **Customised Virtual File System (CVFS)** is a Linux-like file system simulation built completely in **C language**.

This project mimics the internal working of the Linux File System using:

- Inode Structure
- SuperBlock
- File Table
- UAREA (User Area)
- User File Descriptor Table

It provides a **custom shell interface** where users can create, read, write, and delete files just like a real operating system.

---

# 🏗️ 2. Architecture Design

The project is designed based on Linux File System Internals.

## 🔹 BootBlock
Stores boot information of CVFS.

## 🔹 SuperBlock
Maintains:
- Total Inodes
- Free Inodes

## 🔹 Inode (Core of File System)
Each file contains:
- File Name
- Inode Number
- File Size
- Actual File Size
- File Type
- Reference Count
- Permission
- Data Buffer

## 🔹 File Table
Stores:
- Read Offset
- Write Offset
- Mode
- Pointer to Inode

## 🔹 UAREA (User Area)
Maintains:
- Process Name
- User File Descriptor Table (UFDT)

---

# 🌟 3. Key Features

✅ Custom Shell Interface  
✅ Linux-like Commands  
✅ In-Memory File System  
✅ Permission-Based Access  
✅ Error Handling using Macros  
✅ Dynamic Memory Allocation  
✅ File Descriptor Management  
✅ Platform Independent  

---

# 🔥 4. Backup Feature (Data Loss Prevention)

⚠️ IMPORTANT:

This CVFS works completely in **memory (RAM)**.

That means:

- If you close the program without backup,
- All created files and data will be permanently lost.

---

## 💾 Data Loss Prevention System

Before exiting the program, user is asked:

Do you want to store that file Y/N :

### ✅ If user selects Y (Yes):
- `SaveFile()` function is executed
- All in-memory files are saved to local machine
- Files are stored permanently
- Data is preserved

### ❌ If user selects N (No):
- All allocated memory is deallocated
- All data is lost
- Program terminates

---

## 🛠️ Backup Function Used

```c
void SaveFile()
```

This function:
- Traverses all Inodes
- Creates actual files
- Writes buffer data into local files
- Prevents data loss

---

# 📌 5. Supported Commands

| Command | Description |
|----------|------------|
| creat filename permission | Create new file |
| write fd | Write data into file |
| read fd size | Read data from file |
| unlink filename | Delete file |
| ls | List all files |
| man command | Show manual page |
| help | Display help menu |
| clear | Clear terminal |
| exit | Exit CVFS |

---

# 🔐 Permission Model

| Value | Permission |
|-------|------------|
| 1 | READ |
| 2 | WRITE |
| 3 | READ + WRITE |

---

# ⚙️ 6. How To Compile & Execute

## Step 1: Compile

```bash
gcc cvfs.c -o Myexe
```

## Step 2: Run

```bash
./Myexe
```

After running:

----- Pranav CVFS started successfully -----

---

# 📖 7. How To Explore Using Help Option

Inside the shell, type:

help

This will display all supported commands.

To understand a specific command:

man command_name

Example:

man ls  
man creat  
man read  

This makes it easy for users to explore functionality.

---

# 🧪 8. Demo Execution

```bash

Booting process of Pranav CVFS is done
Pranav CVFS : Super block gets initialised succesfully
Pranav CVFS : DILB created succesfully
Pranav CVFS : UAREA gets initialised succesfully
Pranav CVFS : Auxillary data initialised succesfully
-----------------------------------------------
----- Pranav CVFS started succesfully -----
-----------------------------------------------

Pranav CVFS : > help
-----------------------------------------------
---------- pranav CVFS Help Page ----------
-----------------------------------------------
man    : It is used to display manual page
clear  : It is used to clear the terminal
creat  : It is used to create new file
write  : It is used to write the data into file
read   : It is used to read the data from the file
stat   : It is used to display statistical information
unlink : It is used to delete the file
exit   : It is used to terminate Pranav CVFS
-----------------------------------------------

Pranav CVFS : > creat Demo.txt 3
Total number of inodes remaining : 5
Files gets succesfully created with FD 3

Pranav CVFS : > creat pranav.txt 3
Total number of inodes remaining : 4
Files gets succesfully created with FD 4

Pranav CVFS : > ls
-----------------------------------------------
------Pranav CVFS Files Information--------
-----------------------------------------------
1       Demo.txt        0
2       pranav.txt      0
-----------------------------------------------

Pranav CVFS : > write 3
Enter the data that we want to write :
That is demo txt file
File descriptor : 3
Data that we want to write : That is demo txt file

Number of bytes that we want to write : 21
21 bytes gets succesfully writtened

Pranav CVFS : > ls
-----------------------------------------------
------Pranav CVFS Files Information--------
-----------------------------------------------
1       Demo.txt        21
2       pranav.txt      0
-----------------------------------------------

Pranav CVFS : > exit
Do you want to store that file Y/N : Y
File backup complete
```

---

# 🧠 9. Learning Outcomes

This project demonstrates:

- Deep understanding of Linux File System
- OS-level architecture design
- Inode-based implementation
- System call simulation
- Shell design
- Memory management
- Low-level C programming

---


# 📂 Project Structure

cvfs.c  
README.md  

---

