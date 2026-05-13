# unitree_uc

基于 CMake 的 C++17 示例工程，通过本机已安装的 [unitree_sdk2](https://github.com/unitreerobotics/unitree_sdk2) 进行链接与开发。

## 依赖

- CMake 3.16 及以上
- 支持 C++17 的编译器
- 已正确安装 **unitree_sdk2**（含 CMake 包配置，例如 `lib/cmake/unitree_sdk2/unitree_sdk2Config.cmake` 及对应头文件、库）

若尚未安装 SDK，请参考官方仓库说明完成编译与安装（`cmake` + `make install` 等）。

## 构建

```bash
cmake -S . -B build -DCMAKE_BUILD_TYPE=Release
cmake --build build
```

运行：

```bash
./build/unitree_uc
```

## SDK 不在默认路径时

若 `unitree_sdk2` 安装在自定义前缀下，配置时指定其一即可：

```bash
cmake -S . -B build -Dunitree_sdk2_ROOT=/你的安装前缀
```

或：

```bash
cmake -S . -B build -DCMAKE_PREFIX_PATH=/你的安装前缀
```

## 工程结构

| 路径 | 说明 |
|------|------|
| `CMakeLists.txt` | 根 CMake：`find_package(unitree_sdk2)` 与可执行目标 |
| `include/unitree_uc/` | 本工程头文件 |
| `src/main.cpp` | 入口：演示链接 SDK 并调用 `unitree::common::GetCurrentTimeMillisecond()` |

## 许可

若与 `unitree_sdk2` 一并分发，请同时遵守其许可条款；本仓库其余部分由项目维护者自行约定许可。
