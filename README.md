VimCore
=======

基于AHK编写的一个热键、插件、简单宏的API功能集，用于VIATC 0.6.0 的核心，也可以被其它脚本调用。

API 列表
=======


  - RegisterHotkey(Key,Action,Class="")
    - 注册热键 并保存记录
  - SetHotkey(key,Action,Class="")
    - 注册热键 但不保存记录
  - HotkeyLabel()
    - 所有的热键都会调用这个函数，用来分析当前热键对应哪个标签。相当于接收功能
  - ExecSub(Action,Count=0,Class="")
    - 热键标签或者其它功能。相当于输出功能
  - Repeat()
    - 重复执行上一次成功执行的动作
  - Micro(action,class)
    - 解析宏代码，并运行
  - LoadPlugin()
    - 载入插件
  - CustomActions(Action,Info="")
    - 添加动作描述
  - HotkeyControl(Control)
    - 控制热键启动或禁止
  - ToMatch(Key)
    - 用于转换为正则式
  - IsVimHotkey(Key,Class)
    - 判断热键是否存在
  - IsVimLabel(Label)
    - 判断是否为一个可以的动作
  - GetThisHotkey()
    - 获取当前热键名称（会转换为VIMCORE可识别的热键体）
  - TransSendKey(hotkey)
    - 发送热键（将Hotkey以AHK的形式发送）
  - ResolveHotkey(KeyList)
    - 将VIMCORE格式的热键体转换为多个AHK可识别的热键体
  - HK_Match(Class,Key)
    - 查看Key是否存在相于的动作
  - HK_write(Key,Action,Class="")
    - 添加VIMCORE热键体
  - HK_Read(string)
    - 读取VIMCORE热键体中的热键、类、动作
  - HK_Delete(Key,Class)
    - 删除相应的VIMCORE热键体


##  2013.4.16  --  Version 0.2.1
   - 初始化发布到Github
   - 修改定义热键体的结构
   - 修改判定热键的逻辑
   - 添加简单宏支持，需要ini文件
