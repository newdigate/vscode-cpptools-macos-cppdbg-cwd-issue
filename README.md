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