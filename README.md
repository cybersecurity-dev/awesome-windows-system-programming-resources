<div align="center">
    <p align="center">
        <a href="https://github.com/cybersecurity-dev/awesome-windows-system-programming">
          <img width="30%" src="https://github.com/cybersecurity-dev/cybersecurity-dev/blob/main/assets/Windows.svg" />
        </a>
    </p>

```mermaid
flowchart TB
    SRC["Application Source Code<br/>C or C++"]

    SRC --> API["Windows API call<br/>CreateFile, ReadFile or VirtualAlloc"]

    subgraph USER["User Mode"]
        API --> WIN32["Win32 subsystem DLL<br/>Kernel32, Advapi32 or User32"]
        WIN32 --> KBASE["KernelBase.dll"]
        KBASE --> NTDLL["NTDLL native API"]
        NTDLL --> STUB["System-call stub"]
    end

    STUB --> TRANSITION["User-to-kernel transition"]

    subgraph KMODE["Kernel Mode"]
        TRANSITION --> DISPATCH["System-service dispatcher"]
        DISPATCH --> EXEC{"Requested service"}

        EXEC --> OM["Object Manager"]
        EXEC --> PM["Process Manager"]
        EXEC --> MM["Memory Manager"]
        EXEC --> IO["I/O Manager"]
        EXEC --> SRM["Security Reference Monitor"]

        IO --> DRIVER["File-system or device driver"]
        DRIVER --> HAL["Hardware Abstraction Layer"]
    end

    HAL --> HW["Hardware"]

    OM --> RESULT["Status and result"]
    PM --> RESULT
    MM --> RESULT
    IO --> RESULT
    SRM --> RESULT

    RESULT --> RETURN["Return to user mode"]
    RETURN --> ERROR["Convert status to<br/>API result or error code"]
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
