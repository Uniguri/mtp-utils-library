# Class

## MTP

MTP 연결을 사용하기 위한 클래스이다. 이 클래스를 생성하면 MTP 장치에서 Device 정보와 Storage, Folder, File 등의 정보를 모두 캐싱한다.

만약 파일 업로드, 다운로드, 삭제 등의 동작을 수행하면 캐싱된 정보에도 영향을 준다.

### GetError

### GetNumberOfDevices

### GetDevices

Device(장치)를 순회하는 이터레이터를 반환한다.

다음과 같이 사용한다.

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

LIBMTP의 Debug level을 설정한다. Debug level은 다음과 같다.

```cpp
#define LIBMTP_DEBUG_NONE		0x00
#define LIBMTP_DEBUG_PTP		0x01
#define LIBMTP_DEBUG_PLST		0x02
#define LIBMTP_DEBUG_USB		0x04
#define LIBMTP_DEBUG_DATA		0x08
#define LIBMTP_DEBUG_ALL		0xFF
```

## Device

Device(장치)를 나타내는 클래스이다. MTP 클래스를 생성하면 자동으로 생성된다.

### GetDeviceNumber

### GetBusLocation

### GetFriendlyName

### GetVendorName

### GetVendorID

### GetProductName

### GetProductID

### GetStorages

Storage를 순회하는 이터레이터를 반환한다.

사용 방법은 다음과 같다.

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

특정 파일을 기기에서 다운로드 한다.

사용 방법은 다음과 같다.

```cpp
for (auto& file : storage.GetFilesOnRoot())
{
    storage.ReceiveFile(*file, "C:/blah/blah/blah/");
}
```

### SendFile

특정 파일을 기기로 전송한다.

사용 방법은 다음과 같다.

```cpp
storage.SendFile("C:/blah/blah/blah/temp.txt", folder);
```

### DeleteFile

기기의 특정 파일을 지운다.

사용 방법은 다음과 같다.

```cpp
storage.DeleteFile(*file);
```

### SetFileName

주어진 문자열로 파일의 이름을 변경한다. 파일의 새로운 이름을 반환한다.

사용 방법은 다음과 같다.

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

루트에 있는 폴더를 순회는 이터레이터를 반환한다.

```cpp
for (auto& folder : storage.GetFoldersOnRoot())
{
    // Something...
}
```

### GetFilesOnRoot

루트에 있는 파일을 순회하는 이터레이터를 반환한다.

```cpp
for (auto& file : storage.GetFilesOnRoot())
{
    // Something...
}
```

### GetAllChildFolders

해당 Storage에 존재하는 모든 폴더 순회하는 이터레이터를 반환한다.

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

현재 폴더에 존재하는 모든 폴더를 순회하는 이터레이터를 반환한다.

예를 들어 디렉토리 구조가 다음과 다음과 같다면 DIR0, DIR1, DIR2를 순회한다. 다만, 순서는 이름 순이 아니다.

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

사용 방법은 다음과 같다.

```cpp
for (auto& folder : some_folder.GetChildFoldersOnlyOnThis())
{
    // Something...
}
```

### GetChildFilesOnlyOnThis

현재 폴더에 존재하는 모든 파일을 순회하는 이터레이터를 반환한다.

예를 들어 디렉토리 구조가 다음과 같다면 FILE0, FILE1을 순회한다. 다만, 순서는 이름 순이 아니다.

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

사용 방법은 다음과 같다.

```cpp
for (auto& file: some_folder.GetChildFilesOnlyOnThis())
{
    // Something...
}
```

### GetAllChildFolders

현재 폴더의 하위에 존재하는 모든 폴더를 순회하는 이터레이터를 반환한다.

예를 들어, 디렉토리 구조가 다음과 같다면 DIR0, SUBDIR0, SUBDIR1, DIR1, SUBDIR0, SUBSUBDIR0, SUBSUBDIR1, SUBSUBDIR2, DIR2를 순회한다. 다만, 순서는 이름 순이 아니다.

하지만 상위 폴더가 반환된 후 하위 폴더를 반환한다. 즉 SUBDIR0가 DIR0보다 먼저 반환될 수는 없다.

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

사용하는 방법은 다음과 같다.

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

## 기기의 세이브 파일 폴더에 존재하는 특정 이름의 파일 교체

세이브 파일 폴더(”슈퍼 마리오 메이커 2/shm”)에 존재하는 특정 이름의 파일(”course_thumb_\d{3}”)을 PC에 있는 파일(”C:/SMM2Fuzzing/tmp/course_thumb_\d{3}”)으로 교체하는 코드는 다음과 같다.

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

    Folder* smm2 = storage->FindFolderByExactName("슈퍼 마리오 메이커 2");
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

## 세이브 파일 폴더 다운로드 받기

슈퍼 마리오 메이커 2의 세이브 파일 폴더(”슈퍼 마리오 메이커 2/shm”)를 PC의 폴더(”C:/SMM2Fuzzing/”)에 다운로드 받는 코드는 다음과 같다.

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

    Folder* smm2 = storage->FindFolderByExactName("슈퍼 마리오 메이커 2");
    if (!smm2)
        return 0;
    std::cout << smm2->GetFolderName() << " is found!" << std::endl;

    storage->ReceiveFolder(*smm2, "C:/SMM2Fuzzing/");
}
```

## 기기에 존재하는 모든 파일 보기

기기에 존재하는 모든 폴더와 파일을 트리 구조로 출력하는 프로그램은 다음과 같다.

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

## SMM2 퍼저를 위한 툴

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

    Folder* smm2 = storage->FindFolderByExactName("슈퍼 마리오 메이커 2");
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

    Folder* smm2 = storage->FindFolderByExactName("슈퍼 마리오 메이커 2");
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

## NH 퍼징을 위한 툴

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

    Folder* nh = storage->FindFolderByExactName("모여봐요 동물의 숲");
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

    Folder* nh = storage->FindFolderByExactName("모여봐요 동물의 숲");
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