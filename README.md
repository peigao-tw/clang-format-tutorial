# Clang Format 介绍

## 目录

- [介绍](#介绍)
- [安装](#安装)
- [用法](#用法)
  - [独立工具](#独立工具)
  - [与编辑器集成](#与编辑器集成)
- [自动重构代码](#自动重构代码)
- [参考](#参考)

## 介绍

ClangFormat 描述了一组构建在 LibFormat 之上的工具。 它可以通过多种方式支持您的工作流程，包括独立工具和编辑器集成。
可用于格式化 C/C++/Java/JavaScript/JSON/Objective-C/Protobuf/C# 代码。

### 作用

- Clang-Format 是一种流行的代码格式化工具，有助于维护跨团队成员和 IDE 的通用代码样式
- 它将格式设置存储名为 .clang-format 的 YAML 文件中
- 这样一个人、一组开发人员或一个组织可以在所有代码源中建立同质的格式样式。

### 支持的代码样式

- LLVM coding standards
- Google's C++ style guide
- Chromium's style guide
- GNU coding standards
- Mozilla's style guide
- Webkit's style guide
- Microsoft's style guide


## 安装

### Ubuntu

```
sudo apt-get install clang-format
```

## 用法

### 独立工具

#### 基本用法

```bash
clang-format -i -style=“code style” “source code suffixes to be affected”
```

例如，

```bash
clang-format -i -style=llvm *.c *.h
```

将会使用 llvm 编码规范来格式化头文件和源文件，-i 指示就地格式化文件。


#### 配置选项

clang-format 支持两种自定义样式选项

- 命令行指定
  - -style="style-option" 
- 文件指定
  - -style=file
  
#### 预定义的样式

- llvm
- google
- chromium
- mozilla
- webkit
- microsoft
- gnu

#### 样式举例

*AlignConsecutiveAssignments*

```bash
clang-format --style="{AlignConsecutiveAssignments: true}" src/AlignConsecutiveAssignments.cpp
```

```c++
int a            = 1;
int somelangname = 2;
double c         = 3;
```

*AlignConsecutiveDeclarations*

```bash
clang-format --style="{AlignConsecutiveDeclarations: true"} src/AlignConsecutiveDeclarations.cpp
```

```c++
#include <string>

int         aaaaa = 12;
float       bbbbbbbbb = 23;
std::string ccc = "hello";
```

*AlignConsecutiveMacros*

```bash
clang-format --style="{AlignConsecutiveMacros: true}" src/AlignConsecutiveMacros.cpp
```

```c++
#define SHORT_NAME     "short name"
#define LONG_NAME      "long name"
#define EVEN_LONG_NAME "even long name"
#define foo(x)         (x * x)
#define bar(y, z)      (y + z)
```

*IndentCaseBlocks*

```bash
clang-format --style="{IndentCaseBlocks: true}" src/IndentCaseBlocks.cpp
```

```c++
switch (number) {
case 1:
  {
    call_one();
  }
  break;
default:
  {
    call_default();
  }
}
```

*IndentWidth*

```bash
clang-format --style="{IndentWidth: 4}" src/IndentWidth.cpp
```

```c++
int function() {
    if (true) {
        return 1;
    } else {
        return 0;
    }
}
```

#### 创建样式文件

```bash
clang-format -style=llvm -dump-config > .clang-format
```

### 与编辑器集成

#### Vim 集成

## 参考

* [ClangFormat](https://clang.llvm.org/docs/ClangFormat.html)
* [LibFormat](https://clang.llvm.org/docs/LibFormat.html)
* [Clang-Format Style Options](https://clang.llvm.org/docs/ClangFormatStyleOptions.html)
