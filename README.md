# RViz 3D 导航目标工具 ROS2版本

随着技术的不断进步，**3D 导航** 需求变得越来越重要。这里提供了一个来自 **Willow Garage** 的旧工具，支持 **3D 导航目标** 的设置。该代码提取自这个 [仓库](https://github.com/HKUST-Aerial-Robotics/plan_utils)，更多详细信息请访问该链接。

## 🚀 版本说明

- **ROS2 版本**：迁移中的版本

## ROS2 版本状态

✅ **ROS2 版本已成功编译** - 已完成从 ROS1 到 ROS2 的完整迁移！

### ✅ 已完成的迁移项目
- ✅ 更新 package.xml 到 ROS2 格式 (format="3")
- ✅ 迁移 CMakeLists.txt 到 ament_cmake
- ✅ 更新头文件包含路径和命名空间
- ✅ 迁移 ROS1 NodeHandle 到 ROS2 rclcpp::Node
- ✅ 迁移 ROS1 Publisher 到 ROS2 Publisher
- ✅ 更新 TF 库从 TF1 到 TF2
- ✅ 更新日志系统从 ROS_* 到 RCLCPP_*
- ✅ 更新插件导出宏
- ✅ 修复 Ogre 头文件冲突
- ✅ 更新 Arrow 类命名空间到 rviz_rendering
- ✅ 修复 Qt5 集成问题
- ✅ **✅ 成功通过 colcon build 编译！**

### 📝 注意事项
- 基本的鼠标交互功能已简化实现
- 3D 投影使用了简化版本，在完整实现中可能需要更精确的视口投影

## 🔧 ROS2 编译方法

对于 **ROS2** 版本，请使用 `ROS2` 分支：

### 📥 克隆仓库

- **HTTPS 克隆**：

```bash
git clone git@github.com:CTGUMARK/rviz-3d-nav-goal-tool.git
cd rviz-3d-nav-goal-tool
git checkout ROS2
```

### 🛠️ ROS2 编译

```bash
# 确保已安装 ROS2 (Humble/Iron/Rolling)
source /opt/ros/humble/setup.bash
colcon build
```

### 🐛 已知问题

编译时可能会遇到以下错误：
- 命名空间相关的编译错误
- RViz2 API 差异导致的方法调用问题

欢迎提交 Pull Request 来帮助解决这些问题！

## 🚀 使用方法

### ROS2 版本使用方法

由于 ROS2 版本还在迁移中，具体使用方法可能会有所不同。基本概念相同，但在 RViz2 中的插件加载和交互方式可能有所调整。

## 🤝 贡献

欢迎为 ROS2 版本的迁移做出贡献！主要需要帮助的方面：
- 解决 RViz2 API 兼容性问题
- 测试和修复编译错误
- 验证功能完整性
- 更新文档

## 📚 参考

更多信息请参考：
🔗 [3D Navigation 官方仓库](https://github.com/ros-planning/3d_navigation)
🔗 [ROS2 迁移指南](https://docs.ros.org/en/rolling/How-To-Guides/Migrating-from-ROS1.html)