# Malmö #

## Инструкция по установке на ОС Windows ##
1. Скачайте архив по [этой ссылке](https://github.com/telezhnaya/malmo/blob/master/Malmo/Malmo-0.21.0-Windows-64bit.zip) и распакуйте его
2. Откройте PowerShell в режиме администратора, введите команду  
	`Set-ExecutionPolicy -Scope CurrentUser Unrestricted`
3. Убедитесь, что на Вашем компьютере не установлен Python и JDK, не установлены переменные окружения `JAVA_HOME` и т.п. Если они установлены - удалите их. Так вы сильно сэкономите себе время и упростите процесс установки. В ходе установки нужные версии Java и Python2 поставятся самостоятельно
4. `cd $env:HOMEPATH\Malmo-0.21.0-Windows-64bit\scripts`
5. `.\malmo_install.ps1`
6. `cd $env:HOMEPATH\Malmo-0.21.0-Windows-64bit\Minecraft`
7. `.\launchClient.bat`  
Последний процесс поднимает сервер, но при первом запуске он также устанавливает всё оставшееся. Приблизительно спустя час в отдельном окне вы должны увидеть запустившийся клиент игры с начальным меню (в терминале в этот момент будет написано Building 95%, это не должно вас смущать). Если всё так - поздравляю, вы справились :)

## UPD для тех, кто забыл/не успел ##
Я крайне рекомендую подготовиться заранее и поставить все локально, вам будет комфортнее. Но все же:
1. Зайдите на [Azure портал](portal.azure.com)`и откройте терминал (кнопка сверху)
2. `git clone git@github.com:telezhnaya/june-mc.git`
3. `cd june-mc/`
4. `./deploy-malmo-vm.sh <resource group name> <vm name>`
5. Зайдите в полученную виртуалку, логин `malmo`, пароль `MinecraftAI1234` и откройте PowerShell
6. `cd C:\malmomc\Malmo-0.21.0-Windows-64bit\Minecraft\`
7. `.\launchClient.bat`

Project Malmö is a platform for Artificial Intelligence experimentation and research built on top of Minecraft. We aim to inspire a new generation of research into challenging new problems presented by this unique environment.

[![Join the chat at https://gitter.im/Microsoft/malmo](https://badges.gitter.im/Microsoft/malmo.svg)](https://gitter.im/Microsoft/malmo?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge) [![Build Status](https://travis-ci.org/Microsoft/malmo.svg?branch=master)](https://travis-ci.org/Microsoft/malmo) [![license](https://img.shields.io/github/license/mashape/apistatus.svg?maxAge=2592000)](https://github.com/Microsoft/malmo/blob/master/LICENSE.txt)
----
    
## Getting Started ##

1. [Download the latest *pre-built* version, for Windows, Linux or MacOSX.](https://github.com/Microsoft/malmo/releases)   
      NOTE: This is _not_ the same as downloading a zip of the source from Github. _Doing this **will not work** unless you are planning to build the source code yourself (which is a lengthier process). If you get errors along the lines of "`ImportError: No module named MalmoPython`" it will probably be because you have made this mistake._

2. Install the dependencies for your OS: [Windows](doc/install_windows.md), [Linux](doc/install_linux.md), [MacOSX](doc/install_macosx.md).

3. Launch Minecraft with our Mod installed. Instructions below.

4. Launch one of our sample agents, as Python, Lua, C#, C++ or Java. Instructions below.

5. Follow the [Tutorial](https://github.com/Microsoft/malmo/blob/master/Malmo/samples/Python_examples/Tutorial.pdf) 

6. Explore the [Documentation](http://microsoft.github.io/malmo/). This is also available in the readme.html in the release zip.

7. Read the [Blog](http://microsoft.github.io/malmo/blog) for more information.

If you want to build from source then see the build instructions for your OS: [Windows](doc/build_windows.md), [Linux](doc/build_linux.md), [MacOSX](doc/build_macosx.md).

----

## Problems: ##

We're building up a [Troubleshooting](https://github.com/Microsoft/malmo/wiki/Troubleshooting) page of the wiki for frequently encountered situations. If that doesn't work then please ask a question on our [chat page](https://gitter.im/Microsoft/malmo) or open a [new issue](https://github.com/Microsoft/malmo/issues/new).

----

## Launching Minecraft with our Mod: ##

Minecraft needs to create windows and render to them with OpenGL, so the machine you do this from must have a desktop environment.

Go to the folder where you unzipped the release, then:

`cd Minecraft`  
`launchClient` (On Windows)  
`./launchClient.sh` (On Linux or MacOSX)

or, e.g. `launchClient -port 10001` to launch Minecraft on a specific port.

on Linux or MacOSX: `./launchClient.sh -port 10001`

*NB: If you run this from a terminal, the bottom line will say something like "Building 95%" - ignore this - don't wait for 100%! As long as a Minecraft game window has opened and is displaying the main menu, you are good to go.*

By default the Mod chooses port 10000 if available, and will search upwards for a free port if not, up to 11000.
The port chosen is shown in the Mod config page.

To change the port while the Mod is running, use the `portOverride` setting in the Mod config page.

The Mod and the agents use other ports internally, and will find free ones in the range 10000-11000 so if administering
a machine for network use these TCP ports should be open.

----

## Launch an agent: ##

#### Running a Python agent: ####

```
cd Python_Examples
python run_mission.py
```

On MacOSX we currently only support the system python, so please use `/usr/bin/python run_mission.py` if not the default. 

#### Running a Lua agent: (Linux only) ####

```
cd Lua_Examples
lua run_mission.lua
```

#### Running a Torch agent: (Linux only) ####

```
cd Torch_Examples
th run_mission.lua
```

#### Running a C++ agent: ####

`cd Cpp_Examples`

To run the pre-built sample:

`run_mission` (on Windows)  
`./run_mission` (on Linux or MacOSX)

To build the sample yourself:

`cmake .`  
`cmake --build .`  
`./run_mission` (on Linux or MacOSX)  
`Debug\run_mission.exe` (on Windows)

#### Running a C# agent: ####

To run the pre-built sample:

`cd CSharp_Examples`  
`CSharpExamples_RunMission.exe` (on Windows)  
`mono CSharpExamples_RunMission.exe` (on Linux or MacOSX)

To build the sample yourself, open CSharp_Examples/RunMission.csproj in Visual Studio or MonoDevelop.

Or from the command-line:

`cd CSharp_Examples`

Then, on Windows:  
```
msbuild RunMission.csproj /p:Platform=x64
bin\x64\Debug\CSharpExamples_RunMission.exe
```

On Linux or MacOSX:  
```
xbuild RunMission.csproj /p:Platform=x64
mono bin/x64/Debug/CSharpExamples_RunMission.exe
```

#### Running a Java agent: ####

`cd Java_Examples`  
`java -cp MalmoJavaJar.jar:JavaExamples_run_mission.jar -Djava.library.path=. JavaExamples_run_mission` (on Linux or MacOSX)  
`java -cp MalmoJavaJar.jar;JavaExamples_run_mission.jar -Djava.library.path=. JavaExamples_run_mission` (on Windows)

#### Running an Atari agent: (Linux only) ####

```
cd Python_Examples
python ALE_HAC.py
```

----

# Citations #

Please cite Malmo as:

Johnson M., Hofmann K., Hutton T., Bignell D. (2016) [_The Malmo Platform for Artificial Intelligence Experimentation._](http://www.ijcai.org/Proceedings/16/Papers/643.pdf) [Proc. 25th International Joint Conference on Artificial Intelligence](http://www.ijcai.org/Proceedings/2016), Ed. Kambhampati S., p. 4246. AAAI Press, Palo Alto, California USA. https://github.com/Microsoft/malmo

----

# Code of Conduct #

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/). For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.
