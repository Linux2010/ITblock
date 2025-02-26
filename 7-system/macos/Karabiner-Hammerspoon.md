# Karabiner+Hammerspoon

在 **Karabiner-Elements** 中，您可以通过编写自定义的复杂规则（Complex Modifications）来实现将 `i` 键映射为“按住鼠标右键 + 向上移动 10px”的功能。以下是具体步骤：

---

### **1. 安装 Karabiner-Elements**
如果尚未安装，请先下载并安装 Karabiner-Elements：
- 官方网站：[Karabiner-Elements](https://karabiner-elements.pqrs.org/)

---

### **2. 创建自定义复杂规则**
Karabiner-Elements 本身不支持直接控制鼠标移动，但可以通过结合 **Karabiner-Elements** 和 **Hammerspoon** 实现该功能。以下是具体步骤：

#### **步骤 1：安装 Hammerspoon**
- Hammerspoon 是一个 macOS 自动化工具，支持 Lua 脚本控制鼠标和键盘。
- 下载地址：[Hammerspoon](https://www.hammerspoon.org/)

#### **步骤 2：编写 Hammerspoon 脚本**
1. 打开 Hammerspoon 的配置文件（`~/.hammerspoon/init.lua`）。
2. 添加以下脚本：
   ```lua
   -- 定义鼠标右键按下并向上移动 10px 的函数
   function mouseRightClickAndMoveUp()
       -- 按下鼠标右键
       hs.eventtap.rightClick(nil, nil, 1)  -- 1 表示按下
       -- 向上移动鼠标 10px
       local mousePos = hs.mouse.getAbsolutePosition()
       hs.mouse.setAbsolutePosition({x = mousePos.x, y = mousePos.y - 10})
       -- 释放鼠标右键
       hs.eventtap.rightClick(nil, nil, 0)  -- 0 表示释放
   end

   -- 绑定 i 键触发函数
   hs.hotkey.bind({}, "i", function()
       mouseRightClickAndMoveUp()
   end)
   ```

3. 保存文件并重新加载 Hammerspoon 配置（点击 Hammerspoon 菜单栏图标 → `Reload Config`）。

#### **步骤 3：配置 Karabiner-Elements**
1. 打开 Karabiner-Elements。
2. 进入 `Complex Modifications` 选项卡。
3. 点击 `Add rule`，然后选择 `Import more rules from the Internet`。
4. 在浏览器中打开 [Karabiner-Elements Complex Modifications](https://ke-complex-modifications.pqrs.org/)。
5. 搜索并导入 `Change key to another key` 规则。
6. 在 Karabiner-Elements 中启用规则，将 `i` 键映射为一个不常用的键（如 `F13`）。

#### **步骤 4：修改 Hammerspoon 脚本**
1. 修改 Hammerspoon 脚本，监听 `F13` 键（或其他映射键）：
   ```lua
   hs.hotkey.bind({}, "F13", function()
       mouseRightClickAndMoveUp()
   end)
   ```
2. 保存并重新加载 Hammerspoon 配置。

---

### **3. 测试功能**
1. 按下 `i` 键，Karabiner-Elements 会将其映射为 `F13`。
2. Hammerspoon 监听 `F13` 键，触发鼠标右键按下并向上移动 10px 的操作。

---

### **注意事项**
- **权限问题**：Hammerspoon 需要辅助功能权限。打开 `系统设置` → `隐私与安全性` → `辅助功能`，确保 Hammerspoon 已勾选。
- **脚本调试**：如果脚本未生效，可以通过 Hammerspoon 的控制台查看日志（点击菜单栏图标 → `Console`）。
- **鼠标移动精度**：`hs.mouse.setAbsolutePosition` 的坐标单位为屏幕像素，可根据需要调整移动距离。

---

通过以上步骤，您可以实现将 `i` 键映射为“按住鼠标右键 + 向上移动 10px”的功能。如果需要更复杂的鼠标操作，可以进一步扩展 Hammerspoon 脚本。