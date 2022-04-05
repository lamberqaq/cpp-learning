# cpp-learning
## 环境
### Apple clang version 11.0.0 (clang-1100.0.33.8)
### Target: x86_64-apple-darwin20.5.0

## ide:vscode
### tasks.json
{
	"version": "2.0.0",
	"tasks": [
		{
			"type": "cppbuild",
			"label": "C/C++: clang++ 生成活动文件",
			"command": "/usr/bin/clang++",
			"args": [
				"-std=c++17",
        		"-stdlib=libc++",
				"-fdiagnostics-color=always",
				"-g",
				"${workspaceFolder}/*.cpp",
				"-o",
				"${fileDirname}/${fileBasenameNoExtension}"
			],
			"options": {
				"cwd": "${fileDirname}"
			},
			"problemMatcher": [
				"$gcc"
			],
			"group": {
				"kind": "build",
				"isDefault": true
			},
			"detail": "编译器: /usr/bin/clang++"
		}
	]
}
### launch.json
{
    // Use IntelliSense to learn about possible attributes.
    // Hover to view descriptions of existing attributes.
    // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [
        {
            "name": "(lldb) 启动",
            "type": "cppdbg",
            "request": "launch",
            "program": "${fileDirname}/${fileBasenameNoExtension}",
            "args": [],
            "stopAtEntry": false,
            "cwd": "${fileDirname}",
            "environment": [],
            "MIMode": "lldb",
            "console": "integratedTerminal" 
        }
    ]
}
### code-runner
这里的*.cpp是关键，默认的配置为$fileName，支持当前workspace单一的c++文件。
e.g.只有一个helloworld.cpp（包含main函数），如果helloworld.cpp中引用了自己写的其他c++类等，会出现链接错误
C++ Error: Undefined symbols for architecture x86_64
"code-runner.executorMap": {
...
"cpp": "cd $dir && g++ -std=c++17 *.cpp -o $fileNameWithoutExt && $dir$fileNameWithoutExt",
...
}

