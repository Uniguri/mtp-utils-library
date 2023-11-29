# Table of Contents
- [Table of Contents](#table-of-contents)
- [Class](#class)
  - [MTP](#mtp)
    - [GetError](#geterror)
    - [GetNumberOfDevices](#getnumberofdevices)
    - [GetDevices](#getdevices)
    - [DetectDevice](#detectdevice)
    - [IsSuccess](#issuccess)
    - [GetDeviceByDeviceNumber](#getdevicebydevicenumber)
    - [FindDeviceByFriendlyName](#finddevicebyfriendlyname)
    - [FindDeviceByExactFriendlyName](#finddevicebyexactfriendlyname)
    - [FindDeviceByProductName](#finddevicebyproductname)
    - [FindDeviceByExactProductName](#finddevicebyexactproductname)
    - [FindDeviceByVendorName](#finddevicebyvendorname)
    - [FindDeviceByExactVendorName](#finddevicebyexactvendorname)
    - [SetDebugLevel](#setdebuglevel)
  - [Device](#device)
    - [GetDeviceNumber](#getdevicenumber)
    - [GetBusLocation](#getbuslocation)
    - [GetFriendlyName](#getfriendlyname)
    - [GetVendorName](#getvendorname)
    - [GetVendorID](#getvendorid)
    - [GetProductName](#getproductname)
    - [GetProductID](#getproductid)
    - [GetStorages](#getstorages)
    - [FindStorageByID](#findstoragebyid)
    - [FindStorageByStorageDescription](#findstoragebystoragedescription)
    - [FindStorageByExactStorageDescription](#findstoragebyexactstoragedescription)
    - [FindStorageByVolumIdentifier](#findstoragebyvolumidentifier)
    - [FindStorageByExactVolumIdentifier](#findstoragebyexactvolumidentifier)
  - [Storage](#storage)
    - [GetStorageID](#getstorageid)
    - [GetStorageDescription](#getstoragedescription)
    - [GetVolumIdentifier](#getvolumidentifier)
    - [GetRootFolder](#getrootfolder)
    - [FindFileIDByName](#findfileidbyname)
    - [FindFolderIDByName](#findfolderidbyname)
    - [FindFileIDByExactName](#findfileidbyexactname)
    - [FindFolderIDByExactName](#findfolderidbyexactname)
    - [FindFileByName](#findfilebyname)
    - [FindFolderByName](#findfolderbyname)
    - [FindFileByExactName](#findfilebyexactname)
    - [FindFolderByExactName](#findfolderbyexactname)
    - [FindFileByID](#findfilebyid)
    - [FindFolderByID](#findfolderbyid)
    - [IsFileExistByID](#isfileexistbyid)
    - [IsFolderExistByID](#isfolderexistbyid)
    - [ReceiveFile](#receivefile)
    - [SendFile](#sendfile)
    - [DeleteFile](#deletefile)
    - [SetFileName](#setfilename)
    - [MoveFile](#movefile)
    - [ReceiveFolder](#receivefolder)
    - [MakeEmptyFolderToFolder](#makeemptyfoldertofolder)
    - [SendFolder](#sendfolder)
    - [DeleteFolder](#deletefolder)
    - [SetFolderName](#setfoldername)
    - [MoveFolder](#movefolder)
    - [GetFoldersOnRoot](#getfoldersonroot)
    - [GetFilesOnRoot](#getfilesonroot)
    - [GetAllChildFolders](#getallchildfolders)
  - [Folder](#folder)
    - [GetFolderID](#getfolderid)
    - [GetFolderName](#getfoldername)
    - [GetParentFolder](#getparentfolder)
    - [GetNumberOfChildFoldersOnThis](#getnumberofchildfoldersonthis)
    - [GetNumberOfChildFiles](#getnumberofchildfiles)
    - [IsRootFolder](#isrootfolder)
    - [FindChildFileByID](#findchildfilebyid)
    - [FindChildFolderByID](#findchildfolderbyid)
    - [FindChildFileByName](#findchildfilebyname)
    - [FindChildFolderByName](#findchildfolderbyname)
    - [FindChildFileByExactName](#findchildfilebyexactname)
    - [FindChildFolderByExactName](#findchildfolderbyexactname)
    - [GetChildFoldersOnlyOnThis](#getchildfoldersonlyonthis)
    - [GetChildFilesOnlyOnThis](#getchildfilesonlyonthis)
    - [GetAllChildFolders](#getallchildfolders-1)
  - [File](#file)
    - [GetStorageID](#getstorageid-1)
    - [GetFileID](#getfileid)
    - [GetParent](#getparent)
    - [GetFileName](#getfilename)
    - [GetFileType](#getfiletype)
    - [IsOnRoot](#isonroot)
- [Example](#example)
  - [Replace a file with a specific name that exists in your device's save file folder](#replace-a-file-with-a-specific-name-that-exists-in-your-devices-save-file-folder)
  - [Receive the save file folder](#receive-the-save-file-folder)
  - [Print directory tree of the device](#print-directory-tree-of-the-device)
  - [Tools for SMM2 Fuzzers](#tools-for-smm2-fuzzers)
  - [Tools for ACNH purging](#tools-for-acnh-purging)

# Class

## MTP

Class for using MTP connection. When you create this class, it cache all of the Device information and Storage, Folder, File, etc. information.

### GetError

### GetNumberOfDevices

### GetDevices

Returns an iterator that traverses the Device.

Use this following:

```cpp
for (auto& device : mtp.GetDevices())
{
    // Something..
}
```

### DetectDevice

### IsSuccess

### GetDeviceByDeviceNumber

### FindDeviceByFriendlyName

### FindDeviceByExactFriendlyName

### FindDeviceByProductName

### FindDeviceByExactProductName

### FindDeviceByVendorName

### FindDeviceByExactVendorName

### SetDebugLevel

Set the debug level of LIBMTP. The debug level is as follows

```cpp
#define LIBMTP_DEBUG_NONE		0x00
#define LIBMTP_DEBUG_PTP		0x01
#define LIBMTP_DEBUG_PLST		0x02
#define LIBMTP_DEBUG_USB		0x04
#define LIBMTP_DEBUG_DATA		0x08
#define LIBMTP_DEBUG_ALL		0xFF
```

## Device

A class that represents a Device. It is created automatically when you create an MTP class.

### GetDeviceNumber

### GetBusLocation

### GetFriendlyName

### GetVendorName

### GetVendorID

### GetProductName

### GetProductID

### GetStorages

Returns an iterator that traverses the Storage.

Use this following:

```cpp
for (auto& storage : device.GetStorages())
{
    // Something...
}
```

### FindStorageByID

### FindStorageByStorageDescription

### FindStorageByExactStorageDescription

### FindStorageByVolumIdentifier

### FindStorageByExactVolumIdentifier

## Storage

### GetStorageID

### GetStorageDescription

### GetVolumIdentifier

### GetRootFolder

### FindFileIDByName

### FindFolderIDByName

### FindFileIDByExactName

### FindFolderIDByExactName

### FindFileByName

### FindFolderByName

### FindFileByExactName

### FindFolderByExactName

### FindFileByID

### FindFolderByID

### IsFileExistByID

### IsFolderExistByID

### ReceiveFile

Receive a target file from device.

Use this following:

```cpp
for (auto& file : storage.GetFilesOnRoot())
{
    storage.ReceiveFile(*file, "C:/blah/blah/blah/");
}
```

### SendFile

Send a target file to device.

Use this following:

```cpp
storage.SendFile("C:/blah/blah/blah/temp.txt", folder);
```

### DeleteFile

Erase a target file on device.

Use this following:

```cpp
storage.DeleteFile(*file);
```

### SetFileName

Rename a target file.
Return a new name of the file.

Use this following:

```cpp
std::string new_name = storage.SetFileName(file, "new_name");
```

### MoveFile

### ReceiveFolder

### MakeEmptyFolderToFolder

### SendFolder

### DeleteFolder

### SetFolderName

### MoveFolder

### GetFoldersOnRoot

Returns an iterator that traverses the folders in the root.

Use this following:

```cpp
for (auto& folder : storage.GetFoldersOnRoot())
{
    // Something...
}
```

### GetFilesOnRoot

Returns an iterator that traverses the files in the root.

Use this following:

```cpp
for (auto& file : storage.GetFilesOnRoot())
{
    // Something...
}
```

### GetAllChildFolders

Returns an iterator that traverses all the folders that exist in this Storage.

Use this following:

```cpp
for (auto& folder : storage.GetAllChildFolders())
{
    // Something...
}
```

## Folder

### GetFolderID

### GetFolderName

### GetParentFolder

### GetNumberOfChildFoldersOnThis

### GetNumberOfChildFiles

### IsRootFolder

### FindChildFileByID

### FindChildFolderByID

### FindChildFileByName

### FindChildFolderByName

### FindChildFileByExactName

### FindChildFolderByExactName

### GetChildFoldersOnlyOnThis

Returns an iterator that traverses all the folders that exist in the target folder.

For example, if the directory structure is as follows, it will traverse DIR0, DIR1, and DIR2. However, the order is not in name order.
```
<Now Folder>
├─DIR0
│  ├─SUBDIR0
│  └─SUBDIR1
├─DIR1
│  └─SUBDIR0
│      ├─SUBSUBDIR0
│      ├─SUBSUBDIR1
│      └─SUBSUBDIR2
└─DIR2
```

Use this following:

```cpp
for (auto& folder : some_folder.GetChildFoldersOnlyOnThis())
{
    // Something...
}
```

### GetChildFilesOnlyOnThis

Returns an iterator that traverses all the files in the target folder.

For example, if the directory structure looks like this, it will traverse FILE0, FILE1. However, the order is not by name.

```cpp
<Now Folder>
│  FILE0
│  FILE1
│
├─DIR0
│  ├─SUBDIR0
│  └─SUBDIR1
├─DIR1
│  └─SUBDIR0
│      ├─SUBSUBDIR0
│      ├─SUBSUBDIR1
│      └─SUBSUBDIR2
└─DIR2
        FILE0
```

Use this following:

```cpp
for (auto& file: some_folder.GetChildFilesOnlyOnThis())
{
    // Something...
}
```

### GetAllChildFolders

Returns an iterator that traverses all folders that exist under the current folder.

For example, if the directory structure is DIR0, SUBDIR0, SUBDIR1, DIR1, SUBDIR0, SUBSUBDIR0, SUBSUBDIR1, SUBSUBDIR2, DIR2. However, the order is not by name.

However, the subfolders are returned after the parent folder is returned, i.e. SUBDIR0 cannot be returned before DIR0.

```cpp
<Now Folder>
├─DIR0
│  ├─SUBDIR0
│  └─SUBDIR1
├─DIR1
│  └─SUBDIR0
│      ├─SUBSUBDIR0
│      ├─SUBSUBDIR1
│      └─SUBSUBDIR2
└─DIR2
```

Use this following:

```cpp
for (auto& folder : some_folder.GetAllChildFolders())
{
    // Something...
}
```

## File

### GetStorageID

### GetFileID

### GetParent

### GetFileName

### GetFileType

### IsOnRoot

# Example

## Replace a file with a specific name that exists in your device's save file folder

The code to replace a file with a specific name ("course_thumb_\d{3}") that exists in your save file folder ("Super Mario Maker 2/shm") with a file on your PC ("C:/SMM2Fuzzing/tmp/course_thumb_\d{3}") is as follows.

```cpp
MTP mtp;
if (mtp.IsSuccess())
{
    Device* device = mtp.FindDeviceByExactFriendlyName("DBI MTP Responder");
    if (!device)
        return 0;
    std::cout << device->GetFriendlyName() << " is found!" << std::endl;

    Storage* storage = device->FindStorageByExactStorageDescription("7: Saves");
    if (!storage)
        return 0;
    std::cout << storage->GetStorageDescription() << " is found!" << std::endl;

    Folder* smm2 = storage->FindFolderByExactName("슈퍼 마리오 메이커 2"); // Super mario maker 2
    if (!smm2)
        return 0;
    std::cout << smm2->GetFolderName() << " is found!" << std::endl;

    Folder* shm = smm2->FindChildFolderByExactName("shm");
    if (!shm)
        return 0;
    std::cout << "shm is found!" << std::endl;

    std::queue<File*> thumbnails;

    for (auto& file : shm->GetChildFilesOnlyOnThis())
    {
        const std::string& file_name = file->GetFileName();
        if (file_name.find("course_thumb_") == std::string::npos)
            continue;
        std::cout << file->GetFileName() << " is found" << std::endl;
        thumbnails.push(file);
    }

    const std::filesystem::path pc_location = "C:/SMM2Fuzzing/tmp";
    while (!thumbnails.empty())
    {
        File* file = thumbnails.front();
        const std::string& name = file->GetFileName();
        std::cout << "Replace " << name << std::endl;
        thumbnails.pop();
        storage->DeleteFile(*file);
        storage->SendFile(pc_location / name, *shm);
    }
}
```

## Receive the save file folder

The following code will receive the Super Mario Maker 2 save file folder ("Super Mario Maker 2/shm") to a folder on your PC ("C:/SMM2Fuzzing/").

```cpp
MTP mtp;
if (mtp.IsSuccess())
{
    Device* device = mtp.FindDeviceByExactFriendlyName("DBI MTP Responder");
    if (!device)
        return 0;
    std::cout << device->GetFriendlyName() << " is found!" << std::endl;

    Storage* storage = device->FindStorageByExactStorageDescription("7: Saves");
    if (!storage)
        return 0;
    std::cout << storage->GetStorageDescription() << " is found!" << std::endl;

    Folder* smm2 = storage->FindFolderByExactName("슈퍼 마리오 메이커 2"); // Super mario maker 2
    if (!smm2)
        return 0;
    std::cout << smm2->GetFolderName() << " is found!" << std::endl;

    storage->ReceiveFolder(*smm2, "C:/SMM2Fuzzing/");
}
```

## Print directory tree of the device

The following code will print all the folders and files that exist on your device in a tree structure.

```cpp
MTP mtp;
if (mtp.IsSuccess())
{
    Device* device = mtp.FindDeviceByExactFriendlyName("DBI MTP Responder");
    if (!device)
        return 0;
    std::cout << device->GetFriendlyName() << " is found!" << std::endl;

    for (auto& storage : device->GetStorages())
    {
        std::cout << storage.GetStorageDescription() << std::endl;

        auto folder_iterator = storage.GetAllChildFolders();
        for (auto itr = folder_iterator.begin(); itr != itr.end(); ++itr)
        {
            const std::string& indent = std::string(4 * itr.GetDepth() + 4, ' ');
            std::cout << indent + itr->GetFolderName() << std::endl;
            for (auto& file : itr->GetChildFilesOnlyOnThis())
                std::cout << indent + "  " + file->GetFileName() << std::endl;
        }

        for (auto& file : storage.GetFilesOnRoot())
            std::cout << "   " + file->GetFileName() << std::endl;
    }
}
```

## Tools for SMM2 Fuzzers

```cpp
#include <iostream>
#include <queue>

#include <libmtp.h>

#include "mtp.hpp"

using namespace mtp_utils;

void ReplaceThumbnails(MTP& mtp, const std::string& username, const std::filesystem::path& thumbnail_location_on_pc)
{
    Device* device = mtp.FindDeviceByExactFriendlyName("DBI MTP Responder");
    if (!device)
        return;
    std::cout << device->GetFriendlyName() << " is found!" << std::endl;

    Storage* storage = device->FindStorageByExactStorageDescription("7: Saves");
    if (!storage)
        return;
    std::cout << storage->GetStorageDescription() << " is found!" << std::endl;

    Folder* smm2 = storage->FindFolderByExactName("슈퍼 마리오 메이커 2"); // Super mario maker 2
    if (!smm2)
        return;
    std::cout << smm2->GetFolderName() << " is found!" << std::endl;

    Folder* user = smm2->FindChildFolderByExactName(username);
    if (!user)
        return;
    std::cout << username << " is found!" << std::endl;

    std::queue<File*> thumbnails;

    for (auto& file : user->GetChildFilesOnlyOnThis())
    {
        const std::string& file_name = file->GetFileName();
        if (file_name.find("course_thumb_") == std::string::npos)
            continue;
        std::cout << file->GetFileName() << " is found" << std::endl;
        thumbnails.push(file);
    }

    while (!thumbnails.empty())
    {
        File* file = thumbnails.front();
        const std::string& name = file->GetFileName();
        std::cout << "Replace " << name << std::endl;
        thumbnails.pop();
        storage->DeleteFile(*file);
        storage->SendFile(thumbnail_location_on_pc / name, *user);
    }
}

void DumpSMM2SaveFiles(MTP& mtp, const std::string& username, const std::filesystem::path& location)
{
    Device* device = mtp.FindDeviceByExactFriendlyName("DBI MTP Responder");
    if (!device)
        return;
    std::cout << device->GetFriendlyName() << " is found!" << std::endl;

    Storage* storage = device->FindStorageByExactStorageDescription("7: Saves");
    if (!storage)
        return;
    std::cout << storage->GetStorageDescription() << " is found!" << std::endl;

    Folder* smm2 = storage->FindFolderByExactName("슈퍼 마리오 메이커 2"); // Super mario maker 2
    if (!smm2)
        return;
    std::cout << smm2->GetFolderName() << " is found!" << std::endl;

    Folder* user = smm2->FindChildFolderByExactName(username);
    if (!user)
        return;
    std::cout << username << " is found!" << std::endl;

    std::cout << "Dump " << username << " to " << location.string() << std::endl;
    storage->ReceiveFolder(*user, location);
    std::cout << "Done" << std::endl;;
}

void ShowDirectoryTree(MTP& mtp)
{
    Device* device = mtp.FindDeviceByExactFriendlyName("DBI MTP Responder");
    if (!device)
        return;
    std::cout << device->GetFriendlyName() << " is found!" << std::endl;

    for (auto& storage : device->GetStorages())
    {
        std::cout << storage.GetStorageDescription() << std::endl;

        auto folder_iterator = storage.GetAllChildFolders();
        for (auto itr = folder_iterator.begin(); itr != itr.end(); ++itr)
        {
            const std::string& indent = std::string(4 * itr.GetDepth() + 4, ' ');
            std::cout << indent + itr->GetFolderName() << std::endl;
            for (auto& file : itr->GetChildFilesOnlyOnThis())
                std::cout << indent + "  " + file->GetFileName() << std::endl;
        }

        for (auto& file : storage.GetFilesOnRoot())
            std::cout << "   " + file->GetFileName() << std::endl;
    }
}

void Usage(const char* file_name)
{
    std::cout << "Usage: " << file_name << " fuzz [username] [path_of_thumbnails]" << std::endl;
    std::cout << "                    or" << std::endl;
    std::cout << "       " << file_name << " dump [username] [path_to_dump]" << std::endl;
    std::cout << "                    or" << std::endl;
    std::cout << "       " << file_name << " tree" << std::endl;
}

int main(int argc, char** argv)
{
    if (argc < 2)
    {
        Usage(argv[0]);
        return -1;
    }
    MTP mtp;
    if (mtp.IsSuccess())
    {
        const std::string& arg = argv[1];
        if (argc == 4)
        {
            if (arg == "fuzz")
            {
                ReplaceThumbnails(mtp, argv[2], argv[3]);
                return 0;
            }
            else if (arg == "dump")
            {
                DumpSMM2SaveFiles(mtp, argv[2], argv[3]);
                return 0;
            }
            Usage(argv[0]);
        }
        else if (argc == 2)
        {
            if (arg == "tree")
            {
                ShowDirectoryTree(mtp);
                return 0;
            }
            Usage(argv[0]);
        }
        Usage(argv[0]);
        return 0;
    }
    LIBMTP_error_number_t err = mtp.GetError();
    switch (err) {
    case LIBMTP_ERROR_NO_DEVICE_ATTACHED:
        std::cout << "   No raw devices found." << std::endl;
        return 0;
    case LIBMTP_ERROR_CONNECTING:
        std::cerr << "Detect: There has been an error connecting. Exiting" << std::endl;
        return 1;
    case LIBMTP_ERROR_MEMORY_ALLOCATION:
        std::cerr << "Detect: Encountered a Memory Allocation Error. Exiting" << std::endl;
        return 1;
    case LIBMTP_ERROR_NONE:
        break;
    case LIBMTP_ERROR_GENERAL:
    default:
        std::cerr << "Unknown connection error." << std::endl;
        return 1;
    }
}
```

## Tools for ACNH purging

```cpp
#include <iostream>
#include <queue>

#include <libmtp.h>

#include "mtp.hpp"

using namespace mtp_utils;

void ReplaceSaveFolder(MTP& mtp, const std::filesystem::path& save_folder_location_on_pc)
{
    Device* device = mtp.FindDeviceByExactFriendlyName("DBI MTP Responder");
    if (!device)
        return;
    std::cout << device->GetFriendlyName() << " is found!" << std::endl;

    Storage* storage = device->FindStorageByExactStorageDescription("7: Saves");
    if (!storage)
        return;
    std::cout << storage->GetStorageDescription() << " is found!" << std::endl;

    Folder* nh = storage->FindFolderByExactName("모여봐요 동물의 숲"); // Animal crossing new horizon
    if (!nh)
        return;
    std::cout << nh->GetFolderName() << " is found!" << std::endl;

    Folder* savefolder = nh->FindChildFolderByExactName("Device");
    if (savefolder)
    {
        std::cout << savefolder->GetFolderName() << " is found!" << std::endl;
        
        std::queue<File*> files;
        for (auto& file : savefolder->GetChildFilesOnlyOnThis())
            files.push(file);
        for (auto& file : savefolder->FindChildFolderByExactName("Villager0")->GetChildFilesOnlyOnThis())
            files.push(file);
        
        while (!files.empty())
        {
            File* f = files.front();
            files.pop();
            Folder* p = f->GetParent();
            const std::string file_name = f->GetFileName();
            storage->DeleteFile(*f);
            if(p->GetFolderName() == "Device")
                storage->SendFile(save_folder_location_on_pc / file_name, *p);
            else
                storage->SendFile(save_folder_location_on_pc / p->GetFolderName() / file_name, *p);
        }
    }
    else
    {
        std::cout << "Device is not found. Create folder." << std::endl;
        storage->SendFolder(save_folder_location_on_pc, *nh);
    }
}

void DumpNHSaveFolder(MTP& mtp, const std::filesystem::path& location)
{
    Device* device = mtp.FindDeviceByExactFriendlyName("DBI MTP Responder");
    if (!device)
        return;
    std::cout << device->GetFriendlyName() << " is found!" << std::endl;

    Storage* storage = device->FindStorageByExactStorageDescription("7: Saves");
    if (!storage)
        return;
    std::cout << storage->GetStorageDescription() << " is found!" << std::endl;

    Folder* nh = storage->FindFolderByExactName("모여봐요 동물의 숲"); // Animal crossing new horizon
    if (!nh)
        return;
    std::cout << nh->GetFolderName() << " is found!" << std::endl;

    Folder* savefolder = nh->FindChildFolderByExactName("Device");
    if (!savefolder)
        return;
    std::cout << savefolder->GetFolderName() << " is found!" << std::endl;

    std::cout << "Dump Device to " << location.string() << std::endl;
    storage->ReceiveFolder(*savefolder, location);
    std::cout << "Done" << std::endl;;
}

void ShowDirectoryTree(MTP& mtp)
{
    Device* device = mtp.FindDeviceByExactFriendlyName("DBI MTP Responder");
    if (!device)
        return;
    std::cout << device->GetFriendlyName() << " is found!" << std::endl;

    for (auto& storage : device->GetStorages())
    {
        std::cout << storage.GetStorageDescription() << std::endl;

        auto folder_iterator = storage.GetAllChildFolders();
        for (auto itr = folder_iterator.begin(); itr != itr.end(); ++itr)
        {
            const std::string& indent = std::string(4 * itr.GetDepth() + 4, ' ');
            std::cout << indent + itr->GetFolderName() << std::endl;
            for (auto& file : itr->GetChildFilesOnlyOnThis())
                std::cout << indent + "  " + file->GetFileName() << std::endl;
        }

        for (auto& file : storage.GetFilesOnRoot())
            std::cout << "   " + file->GetFileName() << std::endl;
    }
}

void Usage(const char* file_name)
{
    std::cout << "Usage: " << file_name << " fuzz [path_of_savefolder_on_pc]" << std::endl;
    std::cout << "                    or" << std::endl;
    std::cout << "       " << file_name << " dump [path_to_dump]" << std::endl;
    std::cout << "                    or" << std::endl;
    std::cout << "       " << file_name << " tree" << std::endl;
}

int main(int argc, char** argv)
{
    if (argc < 2)
    {
        Usage(argv[0]);
        return -1;
    }
    MTP mtp;
    if (mtp.IsSuccess())
    {
        const std::string& command = argv[1];
        if (command == "fuzz" && argc >= 3)
        {
            const std::filesystem::path& path = argv[2];
            if (path.filename() != "Device")
            {
                std::cout << "Folder name must be \"Device\"." << std::endl;
                return 0;
            }
            ReplaceSaveFolder(mtp, argv[2]);
            return 0;
        }
        else if (command == "dump" && argc >= 3)
        {
            DumpNHSaveFolder(mtp, argv[2]);
            return 0;
        }
        else if (command == "tree")
        {
            ShowDirectoryTree(mtp);
            return 0;
        }
        Usage(argv[0]);
        return 0;
    }
    LIBMTP_error_number_t err = mtp.GetError();
    switch (err) {
    case LIBMTP_ERROR_NO_DEVICE_ATTACHED:
        std::cout << "   No raw devices found." << std::endl;
        return 0;
    case LIBMTP_ERROR_CONNECTING:
        std::cerr << "Detect: There has been an error connecting. Exiting" << std::endl;
        return 1;
    case LIBMTP_ERROR_MEMORY_ALLOCATION:
        std::cerr << "Detect: Encountered a Memory Allocation Error. Exiting" << std::endl;
        return 1;
    case LIBMTP_ERROR_NONE:
        break;
    case LIBMTP_ERROR_GENERAL:
    default:
        std::cerr << "Unknown connection error." << std::endl;
        return 1;
    }
}
```