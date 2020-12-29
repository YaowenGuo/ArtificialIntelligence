安装流程 https://index.ros.org/doc/ros2/Installation/Foxy/

MAC 安装中遇到的问题：

```
python3 -m pip install pygraphviz pydot
```
安装编译报错，架构不支持。需要设置一个环境变量。

```
export ARCHFLAGS="-arch x86_64
```

`ros2 run demo_nodes_cpp talker` 执行发生 python 错误时，看一下 `/usr/local/bin/python3` 是否存在，不存在想办法添加一个链接。不要修改成 `/usr/bin/python3`。否则会发生一些 python 执行错误。
```
Fatal Python error: _PyInterpreterState_Get(): no current thread state
Python runtime state: unknown
```

### 常用指令记录

设置环境变量
```
. ~/ros2_foxy/ros2-osx/setup.bash
```

https://index.ros.org/doc/ros2/