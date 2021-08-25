# demonstration of vscode cppdbg ignoring cwd on macos

When I debug the application on macos using vscode's cppdbg extension, I would expect the executable to be launched from the ```${workspace}``` folder, as I have specified ```cwd``` in launch.json... 

However, the executable is launched from the ```build``` folder.

extract from ```launch.json```:
``` json
{
    "configurations": [
        {
            "name": "(gdb) Launch",
            "cwd": "${workspaceRoot}",
            "osx": {
                "program": "${workspaceRoot}/build/fib.out",
                "MIMode": "lldb"
            }
        }
    ]
}
```
main.cpp:

``` c++
#include <stdlib.h>

int main(int argc, char **argv)
{
    system("echo ${PWD}");
    return 0;
}
```

output:
```
/Users/xxx/vscode-cpptools/Code Samples/Fib/build
```

versions:

C/C++ for Visual Studio Code: ```Version 1.6.0: August 24, 2021```
nodejs: ```v14.17.5```
vscode: ```
    Version: 1.59.1 (Universal)
    Commit: 3866c3553be8b268c8a7f8c0482c0c0177aa8bfa
    Date: 2021-08-19T11:53:52.479Z (6 days ago)
    Electron: 13.1.7
    Chrome: 91.0.4472.124
    Node.js: 14.16.0
    V8: 9.1.269.36-electron.0
    OS: Darwin x64 20.6.0
```
   
