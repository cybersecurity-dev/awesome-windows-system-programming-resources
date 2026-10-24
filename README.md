<div align="center">
    <p align="center">
        <a href="https://github.com/cybersecurity-dev/awesome-windows-system-programming">
          <img width="30%" src="https://github.com/cybersecurity-dev/cybersecurity-dev/blob/main/assets/Windows.svg" />
        </a>
    </p>

```mermaid
flowchart TB
    SRC["Application Source Code<br/>C or C++"]

    SRC --> API["Windows API call<br/>CreateFile,<br/>ReadFile or<br/>VirtualAlloc"]

    subgraph USER["User Mode"]
        API --> WIN32["Win32 subsystem DLL<br/>Kernel32,<br/>Advapi32<br/>or User32"]
        WIN32 --> KBASE["KernelBase.dll"]
        KBASE --> NTDLL["NTDLL<br/>native API"]
        NTDLL --> STUB["System-call<br/>stub"]
    end

    STUB --> TRANSITION["User-to-kernel<br/>transition"]

    subgraph KMODE["Kernel<br/>Mode"]
        TRANSITION --> DISPATCH["System-service<br/>dispatcher"]
        DISPATCH --> EXEC{"Requested<br/>service"}

        EXEC --> OM["Object<br/>Manager"]
        EXEC --> PM["Process<br/>Manager"]
        EXEC --> MM["Memory<br/>Manager"]
        EXEC --> IO["I/O<br/>Manager"]
        EXEC --> SRM["Security<br/>Reference<br/>Monitor"]

        IO --> DRIVER["File-system or<br/>device<br/>driver"]
        DRIVER --> HAL["Hardware<br/>Abstraction<br/>Layer"]
    end

    HAL --> HW["Hardware"]

    OM --> RESULT["Status<br/>and<br/>result"]
    PM --> RESULT
    MM --> RESULT
    IO --> RESULT
    SRM --> RESULT

    RESULT --> RETURN["Return to<br/>user mode"]
    RETURN --> ERROR["Convert<br/>status to<br/>API result<br/>or<br/>error code"]
    ERROR --> SRC

    classDef source fill:#263238,color:#fff,stroke:#111,stroke-width:2px
    classDef user fill:#e3f2fd,color:#111,stroke:#1e88e5
    classDef boundary fill:#fff8e1,color:#111,stroke:#f9a825,stroke-width:2px
    classDef executive fill:#e8f5e9,color:#111,stroke:#43a047
    classDef driver fill:#f3e5f5,color:#111,stroke:#8e24aa
    classDef result fill:#ffebee,color:#111,stroke:#e53935

    class SRC source
    class API,WIN32,KBASE,NTDLL,STUB user
    class TRANSITION,DISPATCH,EXEC boundary
    class OM,PM,MM,IO,SRM executive
    class DRIVER,HAL,HW driver
    class RESULT,RETURN,ERROR result
```

# **`Awesome`** Windows System Programming Resources
</div>

[![Windows](https://custom-icon-badges.demolab.com/badge/Windows-0078D6?style=for-the-badge&logo=windows11&logoColor=white)](https://en.wikipedia.org/wiki/Architecture_of_Windows_NT)
[![Reddit](https://img.shields.io/badge/Reddit-FF4500?style=for-the-badge&logo=reddit&logoColor=white)](https://www.reddit.com/r/windows/new/) 
[![YouTube](https://img.shields.io/badge/YouTube-%23FF0000.svg?style=for-the-badge&logo=YouTube&logoColor=white)](https://youtube.com/playlist?list=PL9V4Zu3RroiU0opdpyV_TZGHRteNp3G5s&si=qeR4hke08fKQ62IP)

<p align="center">
    <a href="https://github.com/cybersecurity-dev/"><img height="25" src="https://github.com/cybersecurity-dev/cybersecurity-dev/blob/main/assets/github.svg" alt="GitHub"></a>
    &nbsp;
    <a href="https://www.youtube.com/@CyberThreatDefense"><img height="25" src="https://github.com/cybersecurity-dev/cybersecurity-dev/blob/main/assets/youtube.svg" alt="YouTube"></a>
    &nbsp;
    <a href="https://cyberthreatdefence.com/my_awesome_lists"><img height="20" src="https://github.com/cybersecurity-dev/cybersecurity-dev/blob/main/assets/blog.svg" alt="My Awesome Lists"></a>
    <img src="https://github.com/cybersecurity-dev/cybersecurity-dev/blob/main/assets/bar.gif">
</p>

```mermaid
flowchart LR
    STUDENT["Student or Developer"]

    subgraph DEVELOPMENT["Development Environment"]
        VS["Visual Studio"]
        VSCODE["Visual Studio Code"]
        SDK["Windows SDK"]
        MSVC["MSVC Compiler"]
        CMAKE["CMake"]
        NUGET["NuGet"]
    end

    subgraph BUILD["Build Pipeline"]
        PRE["Preprocessor"]
        COMPILER["Compiler"]
        OBJ["Object Files"]
        LINKER["Linker"]
        PDB["Program Database"]
        EXE["EXE or DLL"]
    end

    subgraph RUNTIME["Windows<br/>Runtime<br/>Environment"]
        APP["Application"]
        DLL["System<br/>DLLs"]
        SUBSYS["Windows<br/>Subsystem"]
        KERNEL["Windows<br/>Kernel"]
        DRIVER["Device<br/>Drivers"]
        HW["Hardware"]
    end

    subgraph ANALYSIS["Analysis<br/>Toolkit"]
        DEBUGGER["Visual<br/>Studio<br/>Debugger"]
        WINDBG["WinDbg"]
        PROCMON["Process<br/>Monitor"]
        PROCEXP["Process<br/>Explorer"]
        DUMPBIN["Dumpbin"]
        ETW["ETW"]
        WPA["Windows<br/>Performance<br/>Analyzer"]
    end

    STUDENT --> VS
    STUDENT --> VSCODE

    VS --> MSVC
    VSCODE --> CMAKE
    SDK --> MSVC
    NUGET --> VS

    MSVC --> PRE
    CMAKE --> PRE
    PRE --> COMPILER
    COMPILER --> OBJ
    OBJ --> LINKER
    LINKER --> EXE
    LINKER --> PDB

    EXE --> APP
    APP --> DLL
    DLL --> SUBSYS
    SUBSYS --> KERNEL
    KERNEL --> DRIVER
    DRIVER --> HW

    APP -.-> DEBUGGER
    APP -.-> PROCMON
    APP -.-> PROCEXP
    EXE -.-> DUMPBIN
    PDB -.-> WINDBG
    KERNEL -.-> WINDBG
    APP -.-> ETW
    ETW --> WPA

    DEBUGGER --> STUDENT
    WINDBG --> STUDENT
    PROCMON --> STUDENT
    WPA --> STUDENT

    classDef person fill:#263238,color:#fff,stroke:#111,stroke-width:2px
    classDef development fill:#e3f2fd,color:#111,stroke:#1e88e5
    classDef build fill:#e8f5e9,color:#111,stroke:#43a047
    classDef runtime fill:#fff3e0,color:#111,stroke:#fb8c00
    classDef analysis fill:#f3e5f5,color:#111,stroke:#8e24aa

    class STUDENT person
    class VS,VSCODE,SDK,MSVC,CMAKE,NUGET development
    class PRE,COMPILER,OBJ,LINKER,PDB,EXE build
    class APP,DLL,SUBSYS,KERNEL,DRIVER,HW runtime
    class DEBUGGER,WINDBG,PROCMON,PROCEXP,DUMPBIN,ETW,WPA analysis
```
## 📖 Contents
- [Books](#books)
- [Videos](#videos)
- [My Other Awesome Lists](#my-other-awesome-lists)
- [Contributing](#contributing)
- [Contributors](#contributors)

##

### Books

### Videos

### Video Series
- [Windows System Programming in C/C++ by @ASystemProgrammingChannel](https://youtube.com/playlist?list=PLDpFwQfbVxIw_rysNCHPeGmh6wIUnhjrt&si=iJ3z__JQXribLRPF)
- [Windows System Programming by @pentesteracademy](https://youtube.com/playlist?list=PLRJWiLCmxyxiSujVWVL-SpLelqU7L3urx&si=AR25IlMyD1cPqKBO)


##

### My Other Awesome Lists
You can access the my other awesome lists [here](https://cyberthreatdefence.com/my_awesome_lists)

### Contributing
[Contributions of any kind welcome, just follow the guidelines](contributing.md)!

### Contributors
[Thanks goes to these contributors](https://github.com/cybersecurity-dev/awesome-windows-system-programming-resources/graphs/contributors)!

### License
[![CC0](http://mirrors.creativecommons.org/presskit/buttons/88x31/svg/cc-zero.svg)](http://creativecommons.org/publicdomain/zero/1.0)

[🔼 Back to top](#awesome-windows-system-programming-resources)
