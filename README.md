# Getting started VS Code CMake Tools on Windows

## 목차
1. [CMake](#cmake)
- [CMake 설치](#cmake-install)
2. [VS Code](#vs-code)
- [VS Code install](#vs-code-install)
- [VS Code의 CMake 프로젝트 환경설정](#vs-code의-cmake-프로젝트-환경설정)
- [CMake 프로젝트 생성하기](#cmake-프로젝트-생성하기)
3. [ImGui 프로젝트 만들기](#imgui-프로젝트-만들기)
- [프로젝트 파일 트리 구성](#프로젝트-파일-트리-구성)
- [CMakeLIsts.txt 편집하기](#cmakeLIsts.txt-편집하기)

#


## CMake

CMake는 크로스 플랫폼 빌드 환경의 필요로 생긴 오픈소스 프로젝트로 CMakeLists.txt 라는 구성파일을 통해 표준 빌드 파일 ( Unix의 makefile 및 Windows MSVC의 프로젝트/work space )를 생성하는데 사용된다

### CMake install

https://cmake.org/download/ 로 접속하여 자신의 플랫폼에 맞는 최신 릴리즈 버전을 다운로드하여 설치하면 된다.

우리는 Windows 환경의 구축할 것이므로 Windows 플랫폼의 최신 릴리즈 파일을 설치해주면 된다.

## VS Code

윈도우 환경에서 CMake 빌드 시스템을 원활하게 사용하기 위해서는 visual studio 2019 이상의 버전을 이용하거나 VS Code를 이용하는 방법이 존재한다.

다만 VS Code를 사용하면 윈도우 터미널 환경이나 강력한 무료 확장 툴들을 이용할 수 있는 장점이 존재한다.

따라서 본 문서에서는 윈도우 환경에서 VS Code와 CMake를 이용한 빌드 환경을 구축하고 토이 프로젝트를 통해 익숙해지는 과정을 거치도록 한다.

### VS Code install

<img src=".\figure\vscode_homepage.PNG" style="zoom:40%;" />

VS Code를 이용하기 위해 https://code.visualstudio.com/download 로 접속하여 windows용 vs code를 설치하도록 한다.

<img src=".\figure\install.PNG" style="zoom:40%;" />

윈도우 설치 마법사를 이용해 설치가 완료된 것을 확인해준다.



### VS Code의 CMake 프로젝트 환경설정

<img src=".\figure\vscode_first_window.PNG" style="zoom:40%;" />

VS Code의 첫 화면이다. 윈도우에서 VS Code와 CMake Tools 를 연계하여 사용하기 위해서는 빨간 네모 박스로 표시된 Extensions 도구를 클릭해준다.

<img src=".\figure\vscode_cmake_extension.PNG" style="zoom:20%;" />

Extensions 도구메뉴에서 cmake를 검색하면 CMake와 CMake Tools라는 확장 툴들이 검색되어 나온다. 

<img src=".\figure\vscode_cmake_extension_install.PNG" style="zoom:33%;" />

위 화면은  CMake가 이미 설치된 화면이다. CMake와 CMake Tools를 모두 설치하여 다음 내용을 진행하도록 한다.



### CMake 프로젝트 생성하기

다음은 VS Code를 이용하여 CMake 프로젝트를 생성하고 빌드하여 프로그램이 동작하는 과정이다.

<img src=".\figure\vscode_create_cmake_project_1.PNG" style="zoom:33%;" />

우선 CMake 프로젝트를 생성하기 위해 Command Palette를 열어준다. 사진과 같이 View - Command Palette를 선택하거나 Ctrl+Shift+P 로 Command Palette를 열어준다.

<img src=".\figure\vscode_create_cmake_project_2.PNG" style="zoom:33%;" />

Commd Palette에 cmake를 입력하면 다음과 같이 다양한 CMake 관련 메뉴들을 확인할 수 있다. 우선은 프로젝트 생성을 위해 CMake: Quick Start를 선택해준다.

<img src=".\figure\vscode_create_cmake_project_64bit_compiler.PNG" style="zoom:25%;" />

CMake: Quick Start 를 선택하면 첫번째로 프로젝트에서 사용할 컴파일러를 고르게 된다. 우리는 윈도우 환경에 맞는 컴파일러 중 Visual Studio 2017 Express의 컴파일러인 Visual Studio 2017 Desktop Express Release - amd64를 사용하도록 하자. 해당 컴파일러는 64비트 컴파일러임을 유의하도록 한다.

<img src=".\figure\vscode_create_cmake_project_enter_new_name.PNG" style="zoom: 33%;" />

그 다음은 프로젝트의 이름을 결정하도록 한다. 본 문서에서는 프로젝트 이름을 vscode_cmake_windows로 선택하였다.

<img src=".\figure\vscode_create_cmake_project_auto_buildsystem.PNG" style="zoom:33%;" />

프로젝트 이름을 입력하면 vs code에서 자동으로 기본적인 CMakeLists와 main.cpp를 제공한다. main.cpp는 hello world 를 출력하는 기본 예제 코드이다.

![](.\figure\vscode_cmake_build.PNG)

이제 프로젝트가 생성되었으니 빌드를 하고 결과물을 볼 차례이다. VS Code에서는 모든 커맨드 액션을 Command Palette를 통해 이용할 수 있다. Command Palette를 열어주고 CMake: Build를 선택해주면 위 사진과 같이 터미널 창을 통해 CMake 빌드 과정과 빌드 성공 여부가 출력된다. 만약 Build finished with exit code 0 이 출력된다면 정상적으로 빌드가 된 것이다.

![](.\figure\vscode_cmake_select_debug.PNG)

다음으로는 디버그를 이용하여 프로그램을 실행하는 과정이다 Command Palette를 통해 CMake: Debug 를 실행하도록 한다.

![](.\figure\vscode_cmake_debug_result.PNG)

Debug가 성공적으로 실행되었다면 VS Code의 DEBUG CONSOLE을 통해 결과 내용을 확인할 수 있다.

![](.\figure\vscode_cmake_create_solution_and_result_files.PNG)

마지막으로 CMake를 통해 정상적으로 빌드된 작업 디렉토리 목록이다. 흔히 윈도우 환경에서 cmake gui를 이용하여 cmake build를 거친 결과와 같이 build 디렉토리 아래에 visual studio 솔루션 파일과 이외의 결과물들이 생성된 것을 확인할 수 있다.

## ImGui 프로젝트 만들기

앞에 과정을 모두 거쳤다면 VS Code에서 CMake를 이용한 빌드 시스템을 이용할 수 있는 완벽한 환경을 갖춘 상태이다.

다만, Visual Studio 에서 프로젝트 속성을 관리하거나 파일을 추가한 것과 같이 프로젝트를 확장하기 위해서는 CMake 문법에 익숙해질 필요가 있다.

따라서 VS Code에서 CMake를 이용하여 ImGui 프로젝트를 구성하기 위한 간단한 예제를 진행하고자 한다.



### 프로젝트 파일 트리 구성

 본 문서는 ImGui 프로젝트 중 glfw 와 opengl3를 이용한 데모 프로젝트를 구성하고자 한다. 다음은 프로젝트에서 ImGui 프로젝트를 위해 구성한 파일 트리이다.

```
├───3rdparty
│   └───imgui
│       └───backends
├───build
├───libs
│   └───glfw
│       ├───include
│       │   └───GLFW
│       ├───lib-vc2010-32
│       └───lib-vc2010-64
└───src
```

3rdparty 디렉토리에 imgui 관련 헤더와 소스코드를 넣어주고 libs 디렉토리에 glfw library를 넣어주었다. src 디렉토리는 main.cpp 를 넣어주었다.

보다 자세한 내용은 문서와 함께 제공되는 예제 프로젝트를 참고하도록 하자.

### CMakeLIsts.txt 편집하기

다음은 프로젝트를 위한 CMakeLists 작성 내용이다. 

아래 CMake 내용을 보기에 앞서 CMake에서 # 키워드는 주석을 의미함에 주의한다.

```
cmake_minimum_required(VERSION 3.0.0)
project(vscode_cmake_windows VERSION 0.1.0)

#define CMAKE values
set( IMGUI_DIR ${CMAKE_CURRENT_SOURCE_DIR}/3rdparty/imgui )

set( SOURCE # project source files
    ${IMGUI_DIR}/imgui.cpp
    ${IMGUI_DIR}/imgui_demo.cpp
    ${IMGUI_DIR}/imgui_draw.cpp
    ${IMGUI_DIR}/imgui_tables.cpp
    ${IMGUI_DIR}/imgui_widgets.cpp
    ${IMGUI_DIR}/backends/imgui_impl_glfw.cpp
    ${IMGUI_DIR}/backends/imgui_impl_opengl3.cpp   
)

```

위 내용의 cmake_minimum_required 은 프로젝트를 빌드하기 위한 cmake의 최소 버전을 의미한다.

project의 vscode_cmake_windows 는 프로젝트 이름을 의미하며 VERSION은 프로젝트의 버전을 명시하는 것으로 생략 가능하다.

다음으로는 set 키워드이다. set 키워드는 CMake에서 사용할 변수를 생성하는 키워드로써 set( PARAM values  ) 의 경우 PARAM 변수를 선언하고 values  값으로 초기화 하는 의미를 가진다.

위 내용 중 SOURCE 변수를 보면 알 수 있듯이 다양한 값을 입력해줄 수 있다.

```
#added include directories
include_directories(
    ${IMGUI_DIR}
    ${IMGUI_DIR}/backends
    ${CMAKE_CURRENT_SOURCE_DIR}/libs/glfw/include/
)

```

다음은 include_directories 로 프로젝트에 포함할 디렉토리들을 명시하는 과정이다. gcc -I에 해당하며 Visual Studio의 참조 포함 디렉토리에 해당한다.

```

#set project library path
if(WIN32) # if Windows
    if(CMAKE_CL_64) # if 64bit windows
        set(LIB_DIR ${CMAKE_CURRENT_SOURCE_DIR}/libs/glfw/lib-vc2010-64)
    else() # if 32bit windows
        set(LIB_DIR ${CMAKE_CURRENT_SOURCE_DIR}/libs/glfw/lib-vc2010-32)
    endif()
elseif(UNIX) # else if Linux
    add_compile_options(-g -Wall -Wextra)
endif()

```

다음은 if문을 이용하여 시스템 환경을 확인하는 과정이다.

CMake의 경우 WIN32 키워드로 현재 시스템이 윈도우인지, 혹은 UNIX 키워드를 통해 리눅스 환경에 해당하는지를 확인할 수 있다.

또한 CMAKE_CL_64 키워드를 통해 64비트 환경 체크도 가능한 것을 확인할 수 있다.

```

add_executable(${PROJECT_NAME}
    ${CMAKE_CURRENT_SOURCE_DIR}/src/main.cpp
    ${SOURCE}
)

if(WIN32) # if Windows
    target_link_libraries(${PROJECT_NAME}
        PUBLIC
        ${LIB_DIR}/glfw3.lib
        opengl32.lib
        gdi32.lib
    )
elseif(UNIX) # else if Linux
target_link_libraries(${PROJECT_NAME}
    PUBLIC
    GL
    glfw
)
endif()
```

다음은 add_executable을 통해 컴파일 정보를 입력한다.

${PROJECT_NAME} 은 어플리케이션 이름에 해당하며 이후 인자들은 컴파일에 필요한 소스코드들로 이루어져 있다.

target_link_libraryies 는 컴파일에 필요한 라이브러리 정보를 입력하는 것으로 include value와 라이브러리 정보로 이루어져있다. include value는 PUBLIC, PRIVATE, INTERFACE가 존재하며 각 키워드의 정확한 의미는 다음 링크를 참고하기 바란다. ( https://leimao.github.io/blog/CMake-Public-Private-Interface/ )



위와 같이 CMakeLists 를 작성해준 뒤 필요한 코드들을 프로젝트에 포함하여 빌드하면 다음과 같이 정상적으로 imgui가 실행되는 것을 확인할 수 있다.

![](.\figure\run_imgui.PNG)
