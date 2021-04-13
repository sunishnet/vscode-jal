## Just Another Language (JAL) Visual Studio Code Extension README


JAL ([Just another Language](https://justanotherlanguage.org)) is an open source programming language for 8 bit PIC microcontrollers.
It was originally created by Wouter Van Ooijen and later rewritten as JALV2 by Kyle York.

Current version of JAL compiler and libraries are maintained by [Jallib](https://github.com/jallib/) team.

JAL had jaledit as its IDE for a long long time, almost from the begining of JALV2. It worked pretty well on Windows but was not updated since 2010.
Being its author I felt VSCode might be a pretty good IDE which can be extended using its  extension framework.

It's a big learning curve for me as it was developed in Delphi whereas vscode works with node/Javascript/Typescript.
Will try to implement all the features of jaledit in this extension.


## Features
 
 * Extremely fast loading/saving of the largest jal files
 * VSCode features like commenting, searching, file explorer 
 * Git support within vscode 
 * Builtin comparison tool
 * Auto completion
![loading biggest file in jallib](images/vscodeload.gif "Fast loading of largest jal include file" )

* **Syntax highlighting**
    
    * Comments (-- & ;)
    * Keywords (Control, Operator, Other)
    * Constants (Language,Numeric,Other)
    * Strings (Single/Double quote)
    
* **Code Folding**
    
    * Procedures
    * Functions
    * Loops
    * Blocks
![code folding and commenting](/images/jalcodefolding.gif "Code folding")
* **Intellisense, Code Snippets and Comment**
    
    *Partial intellisense without language server*
![Intellisense,code snippets and commenting](/images/autocomp_comment.gif "Intellisense,code snippets and commenting")    
    
* **Build using User tasks.json**
    * Works on Windows and Linux

![Build Fail](/images/buildfail.gif "Ctrl-Click takes to error line on build failure")

* **Jaledit Theme**
    
    Theme added to highlight syntaxes which were not differentiated by default VSCode themes.
    * Jaledit like Light Theme
    * Jaledit Dark theme

![Jaledit Light and Dark themes](/images/themeswitch.gif "Two JALedit themes")

## Requirements

**Prerequisites**
JAL compiler is required. You can download the compiler and libraries from  http://www.justanotherlanguage.org/downloads/ or  https://github.com/jallib/jallib

**Configure Tasks to build the jal file (User Level)**


1. Copy the below json text to Clipboard.
2. Press Ctrl-Shift-P.
3. Type/select "Tasks:Open User Tasks".
4. Select Others (Example to run arbitary command).
5. In the opened tasks.json paste the text from clipboard. 
6. Close the tab and you are ready to compile the JAL file.

![tasks.json config](/images/configtasks.json.gif "a title")

```json
{
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
You can configure the executable path and library path by going to VS Code preferences * Extensions -JAL
Paths with \ and \\ both work.
Multiple library paths can be separated with ; 


## Known Issues
Opening include files,library files not possible unless file is in the same directory

No debugging


## Release Notes
    
    * Two themes added to highlight syntaxes which were not differentiated by default VSCode themes.
    * Changed Icon
    * Added missing keywords

## Change Log 

See the [Change log](https://github.com/sunishnet/vscode-jal/blob/master/CHANGELOG.md) for details about the changes in each version.
Code folding
