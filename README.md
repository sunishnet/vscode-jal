## Just Another Language (JAL) Visual Studio Code Extension README


JAL ([Just another Language](https://justanotherlanguage.org)) is an open source programming language for 8 bit PIC microcontrollers.
It was originally created by Wouter Van Ooijen and later rewritten as JALV2 by Kyle York.

Current version of JAL compiler and libraries are maintained by [Jallib](https://github.com/jallib/) team.

JAL had jaledit as its IDE for a long long time, almost from the begining of JALV2. It worked pretty well on Windows but was not updated since 2010.
Being its author I felt VSCode might be a pretty good IDE which can be extended using its  extension framework.

It's a big learning curve for me as it was developed in Delphi whereas vscode works with node/Javascript/Typescript.
Will try to implement all the features of jaledit in this extension.


## Features
* **Syntax highlighting**
    
    - Comments (-- & ;)
    - Keywords (Control, Operator, Other)
    - Constants (Language,Numeric,Other)
    - Strings (Single/Double quote)
    
* **Code Folding**
    
    - Procedures
    - Functions
    - Loops
    - Blocks
    
* **Build using User tasks.json**
    - Works on Windows and Linux



## Requirements
Configure Tasks to build the jal file 
Please copy the below json text to tasks.json which can be opened by Selecting Terminal - Configure Tasks menu option in vscode.

```json
{
    // See https://go.microsoft.com/fwlink/?LinkId=733558
    // for the documentation about the tasks.json format
    // prefilled tasks.json for compiling a JAL file
    "version": "2.0.0",
    "tasks": [
        {
            "label": "Compile JAL File",
            "type": "process",
            "command": "${config:jal.paths.exePath}",
            "args": [
                "${file}",
                "-s",
                "${config:jal.paths.LibPath}"
            ],
            "presentation": {
                "reveal": "always",
                "panel": "new"
            },
            "problemMatcher": [],
            "group": {
                "kind": "build",
                "isDefault": true
            }
        }
    ]
}
```



## Extension Settings
You can configure the executable path and library path by going to VS Code preferences - Extensions -JAL
Paths with \ and \\ both work.
Multiple library paths can be separated with ; 


## Known Issues
Opening include files,library files not possible unless file is in teh same directory
No debugging


## Release Notes

First version on marketplace

### 2021.4.10

Initial release of JAL VS Code Extension ...

Basic syntax highlighting
Code folding
Snippets working
Build using Terminal - Run task