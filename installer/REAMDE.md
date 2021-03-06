### Open-App Windows installer 

#### Requirements
- All the requirements from Open-Stream app in the root folder.
- Qt Installer framework in Msys2 platform:  `mingw-w64-qt-installer-framework`.

#### Build installer
- Go to `./packages/com.openstream.openstreamapp/data`
- Copy the `openstreamapp.exe` file obtained when you build the project (copy into `./packages/com.openstream.openstreamapp/data`).
- Copy the `openstreamhost.exe` obtained when you build the project. Copy it in the folder `./packages/com.openstream.openstreamapp/dataopenstreamhost`.
- Copy the `AutoLoginTaskSchedulerProject.exe` for the auto logging functionality. Copy it in the folder `./packages/com.openstream.openstreamapp/utils` (Source and instructions on how to compile this file can be found in `AutoLoginTaskSchedulerProject` in openstream-server base folder). 
- Execute `windeployqt` for `openstreamapp.exe`.
- Extract `data.rar` there. (Contains the `dlls` required by the app to run. They can be statically added later on, but for now they are required).
- Inside of `openstreamhost` extract the `dlls.rar` to extract the dll's required by the host at runtime. 
- Add the manifest file `openstream.exe.manifest.xml` to the `openstreamapp.exe` using the Windows SDK tool `mt.exe`. 
- Open `MSYS2 MinGW 64` console, and cd to `.` (`installer` folder).
- Run command: `/mingw64/bin/binarycreator.exe -c config/config.xml -p packages [Installer Name]`
- Wait for the command to finish.
