VimCore
=======

基于AHK编写的一个热键、插件、简单宏的API功能集，用于VIATC 0.6.0 的核心，也可以被其它脚本调用。

How to
=======
  - 在AHK脚本中#include vimcore.ahk
  - 如需要注册热键
    - 调用RegiserHotkey("abcd","\<label\>","notepad") 保存并记录热键，支持多键
    - 调用SetHotkey("shift & a","\<label\>","notepad") 记录热键，不保存记录，而且不支持多键
  - 如果需要控制热键启用/禁用
    - 调用HotkeyControl(control) 当control为true的时候，启用热键 ，当control为false的时候，禁用热键
  - 如果需要添加动作描述
    - 调用CustomActions("\<label\>","测试")
  - 如果需要添加插件，请将插件脚本放置脚本目录的actions\子目录中。
  
  - 变量及数据(超级全局变量)
    - Vim_HotkeyList 
      - 用于保存所有Vimcore的热键体
      - 数据组成 : " 10|TTOTAL_CMD7|\<lwin\>e6|\<test\> "
      - 左右各带一个Tab
    	- 第一个数字加|, 10| 描述CLASS有10位长，即TTOTAL_CMD
	    - 第二个数字加|, 7| 描述Key有7位长，即<lwin>e
    	- 第三个数字加|, 6| 描述Action有6位长，即<test>
    - Vim_HotkeyExist
      - 用于保存当前存在的热键
    - Vim_HotkeyTemp
      - 用于保存已经添加的热键
    - Vim_HotkeyCount
      - 用于保存Count
    - Vim_Actions
      - 用于保存Action的描述
    - Vim_Mode
      - 用于控制Vim的模式
    - Vim_Repeat
      - 用于保存Repeat（重复上一次动作）的数据

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
