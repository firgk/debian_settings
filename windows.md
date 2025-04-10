




## strcpy脚本

	cmd /k "C:\greenmode\scrcpy-win64-v2.3.1\scrcpy.exe"
	cmd /k "C:\Users\lgh\software\scrcpy-win64-v2.3.1\scrcpy.exe -d"



## 电源选项切换脚本

	Powercfg -setactive 381b4222-f694-41f0-9685-ff5bb260df2e



## 连接服务器vbs脚本，免输入密码

	Set ws = CreateObject("WScript.Shell")
	ws.run "ssh root@106.12.11.156"
	wscript.sleep 1000
	ws.sendkeys("mypassword")
	ws.sendkeys("{ENTER}")
	ws.sendkeys("{ENTER}")
	wscript.quit 

mypassword 为我的密码



## 切换路径

	cd C:\Users\lgh\3D Objects\apps\bash


## 资源管理器打开当前文件夹

	explorer .


## 开启软件

```
start https://docs.oracle.com/javase/8/docs/api/index.html
start https://docs.spring.io/spring-framework/docs/4.2.9.RELEASE/javadoc-api/
start https://brucecai55520.gitee.io/bruceblogpages/fe/css/css.html
start https://www.runoob.com/html/html-url.html
cmd /k "code C:\Users\lgh\Desktop\htmlcssjs.md"
cmd /k "code C:\Users\lgh\Desktop\spring.md"
cmd /k "code C:\Users\lgh\Desktop\thymefy.md"

```









## 代理脚本


```
set http_proxy=http://127.0.0.1:7897
set https_proxy=socks://127.0.0.1:7897

curl www.google.com

@echo off
echo !!!!!!!!!!!!!!!!!!!!!!!!! proxy start success !!!!!!!!!!!!!!!!!!!!!!!!! 
echo !!!!!!!!!!!!!!!!!!!!!!!!! proxy start success !!!!!!!!!!!!!!!!!!!!!!!!! 
echo !!!!!!!!!!!!!!!!!!!!!!!!! proxy start success !!!!!!!!!!!!!!!!!!!!!!!!!
```


```

set http_proxy=
set https_proxy=

@echo off
echo !!!!!!!!!!!!!!!!!!!!!!!!! proxy off success !!!!!!!!!!!!!!!!!!!!!!!!! 
echo !!!!!!!!!!!!!!!!!!!!!!!!! proxy off success !!!!!!!!!!!!!!!!!!!!!!!!! 
echo !!!!!!!!!!!!!!!!!!!!!!!!! proxy off success !!!!!!!!!!!!!!!!!!!!!!!!! 
```




## ahk 键位：

	; 将 Alt + Z 映射为 Alt + 左方向键
	!z::  
	Send !{Left}  
	return
	
	; 将 Alt + A 映射为 Win + Ctrl + 左方向键
	!a::  
	Send #^{Left}  
	return
	
	; 将 Alt + D 映射为 Win + Ctrl + 右方向键
	!d::  
	Send #^{Right}  
	return
	
	; 将 Alt + w 映射为 Win + 上方向键
	!w::
	Send #{Up}
	return
	
	; 将 Alt + s 映射为 Win + 下方向键
	!s::
	Send #{Down}
	return
	
	
	; 将 Alt + X 映射为 Alt + F4
	!x::
	Send !{F4}
	return
	
	
	; 将 Alt + E 映射为 Enter
	!e::
	Send {Enter}
	return
	
	
	; 将 Alt + R 映射为 Backspace
	!r::
	Send {Backspace}
	return
	
	
	; 将 Alt + C 映射为打开 PowerShell
	; Run, powershell.exe
	; 将 Alt + C 映射为打开命令提示符（终端）
	!c::
	Run, cmd.exe
	return
	
	
	; 将 Alt + F 映射为 Delete
	!f::
	Send {Delete}
	return
	
	
	
	; 将 CapsLock 映射为 Esc
	CapsLock::
	Send {Esc}
	return
	
	
	!1::
	Send {Left}
	return
	
	
	!2::
	Send {Right}
	return




### frp

```
cmd /k "frpc.exe -c frpc.ini"
```


```
[common]
server_addr=frXX.onlXe
server_port=12365
token=asdXX23


[lgh1001pub]
local_ip=127.0.0.1
local_port= 1111
remote_port=1001


[lgh1002nas]
local_ip=127.0.0.1
local_port=5244
remote_port=1002





```


## glazewm

`C:\Users\lgh\.glzr\glazewm`

```
general:
  # Commands to run when the WM has started. This is useful for running a
  # script or launching another application.
  # Example: The below command launches Zebar.
  # startup_commands: ['shell-exec zebar']

  # Commands to run just before the WM is shutdown.
  # Example: The below command kills Zebar.
  # shutdown_commands: ['shell-exec taskkill /IM zebar.exe /F']

  # Commands to run after the WM config is reloaded.
  config_reload_commands: []

  # Whether to automatically focus windows underneath the cursor.
  focus_follows_cursor: false

  # Whether to switch back and forth between the previously focused
  # workspace when focusing the current workspace.
  toggle_workspace_on_refocus: false

  cursor_jump:
    # Whether to automatically move the cursor on the specified trigger.
    enabled: true

    # Trigger for cursor jump:
    # - 'monitor_focus': Jump when focus changes between monitors.
    # - 'window_focus': Jump when focus changes between windows.
    trigger: 'monitor_focus'

  # How windows should be hidden when switching workspaces.
  # - 'cloak': Recommended. Hides windows with no animation.
  # - 'hide': Legacy method (v3.5 and earlier) that has a brief animation,
  # but has stability issues with some apps.
  hide_method: 'cloak'

  # Affects which windows get shown in the native Windows taskbar. Has no
  # effect if `hide_method: 'hide'`.
  # - 'true': Show all windows (regardless of workspace).
  # - 'false': Only show windows from the currently shown workspaces.
  show_all_in_taskbar: false

gaps:
  # Whether to scale the gaps with the DPI of the monitor.
  scale_with_dpi: true

  # Gap between adjacent windows.
  inner_gap: '0px'

  # Gap between windows and the screen edge.
  outer_gap:
    top: '0px'
    right: '0px'
    bottom: '0px'
    left: '0px'

window_effects:
  # Visual effects to apply to the focused window.
  focused_window:
    # Highlight the window with a colored border.
    # ** Exclusive to Windows 11 due to API limitations.
    border:
      enabled: true
      color: '#ff0000'

    # Remove the title bar from the window's frame. Note that this can
    # cause rendering issues for some applications.
    hide_title_bar:
      enabled: false

    # Change the corner style of the window's frame.
    # ** Exclusive to Windows 11 due to API limitations.
    corner_style:
      enabled: false
      # Allowed values: 'square', 'rounded', 'small_rounded'.
      style: 'square'

  # Visual effects to apply to non-focused windows.
  other_windows:
    border:
      enabled: true
      color: '#a1a1a1'
    hide_title_bar:
      enabled: false
    corner_style:
      enabled: false
      style: 'square'

window_behavior:
  # 新打开的窗口的状态
  # New windows are created in this state whenever possible.
  # Allowed values: 'tiling', 'floating'.
  initial_state: 'tiling'

  # Sets the default options for when a new window is created. This also
  # changes the defaults for when the state change commands, like
  # `set-floating`, are used without any flags.
  state_defaults:
    floating:
      # Whether to center floating windows by default.
      centered: true

      # Whether to show floating windows as always on top.
      shown_on_top: false

    fullscreen:
      # Maximize the window if possible. If the window doesn't have a
      # maximize button, then it'll be fullscreen'ed normally instead.
      maximized: false

      # Whether to show fullscreen windows as always on top.
      shown_on_top: false

workspaces:
  - name: '1'
  - name: '2'
  - name: '3'
  - name: '4'
  - name: '5'
  - name: '6'
  - name: '7'
  - name: '8'
  - name: '9'

window_rules:
  - commands: ['ignore']
    match:
      # Ignores any Zebar windows.
      # - window_process: { equals: 'zebar' }

      # Ignores picture-in-picture windows for browsers.
      - window_title: { regex: '[Pp]icture.in.[Pp]icture' }
        window_class: { regex: 'Chrome_WidgetWin_1|MozillaDialogClass' }

      # Ignore rules for various 3rd-party apps.
      - window_process: { equals: 'PowerToys' }
        window_class: { regex: 'HwndWrapper\[PowerToys\.PowerAccent.*?\]' }
      - window_process: { equals: 'PowerToys' }
        window_title: { regex: '.*? - Peek' }
      - window_process: { equals: 'Lively' }
        window_class: { regex: 'HwndWrapper' }

binding_modes:
  # When enabled, the focused window can be resized via arrow keys or HJKL.
  - name: 'resize'
    keybindings:
      # - commands: ['resize --width -2%']
      #   bindings: ['h', 'left']
      # - commands: ['resize --width +2%']
      #   bindings: ['l', 'right']
      # - commands: ['resize --height +2%']
      #   bindings: ['k', 'up']
      # - commands: ['resize --height -2%']
      #   bindings: ['j', 'down']
      # Press enter/escape to return to default keybindings.
      # - commands: ['wm-disable-binding-mode --name resize']
      #   bindings: ['escape', 'enter']

keybindings:
  # 重激活主区
  # Shift focus in a given direction.
  # - commands: ['focus --direction left']
  #   bindings: ['alt+h', 'alt+left']
  # - commands: ['focus --direction right']
  #   bindings: ['alt+l', 'alt+right']
  # - commands: ['focus --direction up']
  #   bindings: ['alt+k', 'alt+up']
  # - commands: ['focus --direction down']
  #   bindings: ['alt+j', 'alt+down']
  - commands: ['focus --direction left']
    bindings: ['alt+left']
  - commands: ['focus --direction right']
    bindings: ['alt+right']
  - commands: ['focus --direction up']
    bindings: ['alt+up']
  - commands: ['focus --direction down']
    bindings: ['alt+down']

  # 移动窗口
  # Move focused window in a given direction.
  # - commands: ['move --direction left']
  #   bindings: ['alt+shift+h', 'alt+shift+left']
  # - commands: ['move --direction right']
  #   bindings: ['alt+shift+l', 'alt+shift+right']
  # - commands: ['move --direction up']
  #   bindings: ['alt+shift+k', 'alt+shift+up']
  # - commands: ['move --direction down']
  #   bindings: ['alt+shift+j', 'alt+shift+down']
  - commands: ['move --direction left']
    bindings: ['alt+shift+left']
  - commands: ['move --direction right']
    bindings: ['alt+shift+right']
  - commands: ['move --direction up']
    bindings: ['alt+shift+up']
  - commands: ['move --direction down']
    bindings: ['alt+shift+down']


  # 调整大小
  # Resize focused window by a percentage or pixel amount.
  - commands: ['resize --width -16%']
    bindings: ['alt+o']
  - commands: ['resize --width +16%']
    bindings: ['alt+p']
  - commands: ['resize --height +16%']
    bindings: ['alt+u']
  - commands: ['resize --height -16%']
    bindings: ['alt+i']


  # As an alternative to the resize keybindings above, resize mode enables
  # resizing via arrow keys or HJKL. The binding mode is defined above with
  # the name 'resize'.
  # - commands: ['wm-enable-binding-mode --name resize']
  #   bindings: ['alt+r']


  # 暂定所有快捷键
  # Disables window management and all other keybindings until alt+shift+p
  # is pressed again.
  # - commands: ['wm-toggle-pause']
  #   bindings: ['alt+shift+p']


  # 切换新打开窗口的折叠方向
  # Change tiling direction. This determines where new tiling windows will
  # be inserted.
  - commands: ['toggle-tiling-direction']
    bindings: ['alt+shift+enter']

  
  # Change focus from tiling windows -> floating -> fullscreen.
  - commands: ['wm-cycle-focus']
    bindings: ['alt+m+q']


  # 切换为浮动
  # Change the focused window to be floating.
  - commands: ['toggle-floating --centered']
    bindings: ['alt+enter']


  # 切换为铺排
  # Change the focused window to be tiling.
  - commands: ['toggle-tiling']
    bindings: ['alt+enter']


  # 全屏
  # Change the focused window to be fullscreen.
  # - commands: ['toggle-fullscreen']
  #   bindings: ['alt+w']


  # 最小化
  # Minimize focused window.
  # - commands: ['toggle-minimized']
  #   bindings: ['alt+s']

  # Close focused window.
  # - commands: ['close']
  #   bindings: ['alt+x']

  # Kill GlazeWM process safely.
  - commands: ['wm-exit']
    bindings: ['alt+shift+q']

  # Re-evaluate configuration file.
  # - commands: ['wm-reload-config']
  #   bindings: ['alt+shift+r']

  # Redraw all windows.
  # - commands: ['wm-redraw']
  #   bindings: ['alt+shift+w']

  # Launch CMD terminal. Alternatively, use `shell-exec wt` or
  # `shell-exec %ProgramFiles%/Git/git-bash.exe` to start Windows
  # Terminal and Git Bash respectively.
  - commands: ['shell-exec cmd']
    bindings: ['alt+k']

  - commands: ['shell-exec chrome']
    bindings: ['alt+l']

  - commands: ['shell-exec p']
    bindings: ['alt+m']

  
  # 前一个后一个桌面
  # Focus the next/previous active workspace defined in `workspaces` config.
  # - commands: ['focus --next-active-workspace']
  #   bindings: ['alt+d']
  # - commands: ['focus --prev-active-workspace']
  #   bindings: ['alt+a']

  # 上个桌面
  # Focus the workspace that last had focus.
  # - commands: ['focus --recent-workspace']
  #   bindings: ['alt+q']


  # 多显示器
  # Move the focused window's parent workspace to a monitor in a given
  # direction.
  # - commands: ['move-workspace --direction left']
  #   bindings: ['alt+shift+a']
  # - commands: ['move-workspace --direction right']
  #   bindings: ['alt+shift+f']
  # - commands: ['move-workspace --direction up']
  #   bindings: ['alt+shift+d']
  # - commands: ['move-workspace --direction down']
  #   bindings: ['alt+shift+s']
  

  
  # 切换桌面
  # Change focus to a workspace defined in `workspaces` config.
  # - commands: ['focus --workspace 1']
  #   bindings: ['alt+1']
  # - commands: ['focus --workspace 2']
  #   bindings: ['alt+2']
  # - commands: ['focus --workspace 3']
  #   bindings: ['alt+3']
  # - commands: ['focus --workspace 4']
  #   bindings: ['alt+4']
  # - commands: ['focus --workspace 5']
  #   bindings: ['alt+5']
  # - commands: ['focus --workspace 6']
  #   bindings: ['alt+6']
  # - commands: ['focus --workspace 7']
  #   bindings: ['alt+7']
  # - commands: ['focus --workspace 8']
  #   bindings: ['alt+8']
  # - commands: ['focus --workspace 9']
  #   bindings: ['alt+9']





  # 移动窗口去某个桌面
  # Move focused window to a workspace defined in `workspaces` config.
  # - commands: ['move --workspace 1', 'focus --workspace 1']
  #   bindings: ['alt+shift+1']
  # - commands: ['move --workspace 2', 'focus --workspace 2']
  #   bindings: ['alt+shift+2']
  # - commands: ['move --workspace 3', 'focus --workspace 3']
  #   bindings: ['alt+shift+3']
  # - commands: ['move --workspace 4', 'focus --workspace 4']
  #   bindings: ['alt+shift+4']
  # - commands: ['move --workspace 5', 'focus --workspace 5']
  #   bindings: ['alt+shift+5']
  # - commands: ['move --workspace 6', 'focus --workspace 6']
  #   bindings: ['alt+shift+6']
  # - commands: ['move --workspace 7', 'focus --workspace 7']
  #   bindings: ['alt+shift+7']
  # - commands: ['move --workspace 8', 'focus --workspace 8']
  #   bindings: ['alt+shift+8']
  # - commands: ['move --workspace 9', 'focus --workspace 9']
  #   bindings: ['alt+shift+9']

```


can use without ahk:

```
general:
  # Commands to run when the WM has started. This is useful for running a
  # script or launching another application.
  # Example: The below command launches Zebar.
  # startup_commands: ['shell-exec zebar']

  # Commands to run just before the WM is shutdown.
  # Example: The below command kills Zebar.
  # shutdown_commands: ['shell-exec taskkill /IM zebar.exe /F']

  # Commands to run after the WM config is reloaded.
  config_reload_commands: []

  # Whether to automatically focus windows underneath the cursor.
  focus_follows_cursor: false

  # Whether to switch back and forth between the previously focused
  # workspace when focusing the current workspace.
  toggle_workspace_on_refocus: false

  cursor_jump:
    # Whether to automatically move the cursor on the specified trigger.
    enabled: true

    # Trigger for cursor jump:
    # - 'monitor_focus': Jump when focus changes between monitors.
    # - 'window_focus': Jump when focus changes between windows.
    trigger: 'monitor_focus'

  # How windows should be hidden when switching workspaces.
  # - 'cloak': Recommended. Hides windows with no animation.
  # - 'hide': Legacy method (v3.5 and earlier) that has a brief animation,
  # but has stability issues with some apps.
  hide_method: 'cloak'

  # Affects which windows get shown in the native Windows taskbar. Has no
  # effect if `hide_method: 'hide'`.
  # - 'true': Show all windows (regardless of workspace).
  # - 'false': Only show windows from the currently shown workspaces.
  show_all_in_taskbar: false

gaps:
  # Whether to scale the gaps with the DPI of the monitor.
  scale_with_dpi: true

  # Gap between adjacent windows.
  inner_gap: '0px'

  # Gap between windows and the screen edge.
  outer_gap:
    top: '0px'
    right: '0px'
    bottom: '0px'
    left: '0px'

window_effects:
  # Visual effects to apply to the focused window.
  focused_window:
    # Highlight the window with a colored border.
    # ** Exclusive to Windows 11 due to API limitations.
    border:
      enabled: true
      color: '#ff0000'

    # Remove the title bar from the window's frame. Note that this can
    # cause rendering issues for some applications.
    hide_title_bar:
      enabled: false

    # Change the corner style of the window's frame.
    # ** Exclusive to Windows 11 due to API limitations.
    corner_style:
      enabled: false
      # Allowed values: 'square', 'rounded', 'small_rounded'.
      style: 'square'

  # Visual effects to apply to non-focused windows.
  other_windows:
    border:
      enabled: true
      color: '#a1a1a1'
    hide_title_bar:
      enabled: false
    corner_style:
      enabled: false
      style: 'square'

window_behavior:
  # 新打开的窗口的状态
  # New windows are created in this state whenever possible.
  # Allowed values: 'tiling', 'floating'.
  initial_state: 'tiling'

  # Sets the default options for when a new window is created. This also
  # changes the defaults for when the state change commands, like
  # `set-floating`, are used without any flags.
  state_defaults:
    floating:
      # Whether to center floating windows by default.
      centered: true

      # Whether to show floating windows as always on top.
      shown_on_top: false

    fullscreen:
      # Maximize the window if possible. If the window doesn't have a
      # maximize button, then it'll be fullscreen'ed normally instead.
      maximized: false

      # Whether to show fullscreen windows as always on top.
      shown_on_top: false

workspaces:
  - name: '1'
  - name: '2'
  - name: '3'
  - name: '4'
  - name: '5'
  - name: '6'
  - name: '7'
  - name: '8'
  - name: '9'

window_rules:
  - commands: ['ignore']
    match:
      # Ignores any Zebar windows.
      # - window_process: { equals: 'zebar' }

      # Ignores picture-in-picture windows for browsers.
      - window_title: { regex: '[Pp]icture.in.[Pp]icture' }
        window_class: { regex: 'Chrome_WidgetWin_1|MozillaDialogClass' }

      # Ignore rules for various 3rd-party apps.
      - window_process: { equals: 'PowerToys' }
        window_class: { regex: 'HwndWrapper\[PowerToys\.PowerAccent.*?\]' }
      - window_process: { equals: 'PowerToys' }
        window_title: { regex: '.*? - Peek' }
      - window_process: { equals: 'Lively' }
        window_class: { regex: 'HwndWrapper' }

binding_modes:
  # When enabled, the focused window can be resized via arrow keys or HJKL.
  - name: 'resize'
    keybindings:
      - commands: ['resize --width -2%']
        bindings: ['h', 'left']
      - commands: ['resize --width +2%']
        bindings: ['l', 'right']
      - commands: ['resize --height +2%']
        bindings: ['k', 'up']
      - commands: ['resize --height -2%']
        bindings: ['j', 'down']
      # Press enter/escape to return to default keybindings.
      - commands: ['wm-disable-binding-mode --name resize']
        bindings: ['escape', 'enter']

keybindings:
  # 重激活主区
  # Shift focus in a given direction.
  - commands: ['focus --direction left']
    bindings: ['alt+h', 'alt+left']
  - commands: ['focus --direction right']
    bindings: ['alt+l', 'alt+right']
  - commands: ['focus --direction up']
    bindings: ['alt+k', 'alt+up']
  - commands: ['focus --direction down']
    bindings: ['alt+j', 'alt+down']


  # 移动窗口
  # Move focused window in a given direction.
  - commands: ['move --direction left']
    bindings: ['alt+shift+h', 'alt+shift+left']
  - commands: ['move --direction right']
    bindings: ['alt+shift+l', 'alt+shift+right']
  - commands: ['move --direction up']
    bindings: ['alt+shift+k', 'alt+shift+up']
  - commands: ['move --direction down']
    bindings: ['alt+shift+j', 'alt+shift+down']


  # 调整大小
  # Resize focused window by a percentage or pixel amount.
  - commands: ['resize --width -16%']
    bindings: ['alt+o']
  - commands: ['resize --width +16%']
    bindings: ['alt+p']
  - commands: ['resize --height +16%']
    bindings: ['alt+u']
  - commands: ['resize --height -16%']
    bindings: ['alt+i']


  # As an alternative to the resize keybindings above, resize mode enables
  # resizing via arrow keys or HJKL. The binding mode is defined above with
  # the name 'resize'.
  - commands: ['wm-enable-binding-mode --name resize']
    bindings: ['alt+r']

  # 暂定所有快捷键
  # Disables window management and all other keybindings until alt+shift+p
  # is pressed again.
  - commands: ['wm-toggle-pause']
    bindings: ['alt+shift+p']

  # 切换新打开窗口的折叠方向
  # Change tiling direction. This determines where new tiling windows will
  # be inserted.
  - commands: ['toggle-tiling-direction']
    bindings: ['alt+shift+o']

  
  # Change focus from tiling windows -> floating -> fullscreen.
  - commands: ['wm-cycle-focus']
    bindings: ['alt+m+q']

  # 切换为浮动
  # Change the focused window to be floating.
  - commands: ['toggle-floating --centered']
    bindings: ['alt+enter']

  # 切换为铺排
  # Change the focused window to be tiling.
  - commands: ['toggle-tiling']
    bindings: ['alt+enter']

  # 全屏
  # Change the focused window to be fullscreen.
  - commands: ['toggle-fullscreen']
    bindings: ['alt+w']

  # 最小化
  # Minimize focused window.
  - commands: ['toggle-minimized']
    bindings: ['alt+s']

  # Close focused window.
  - commands: ['close']
    bindings: ['alt+x']

  # Kill GlazeWM process safely.
  - commands: ['wm-exit']
    bindings: ['alt+shift+e']

  # Re-evaluate configuration file.
  - commands: ['wm-reload-config']
    bindings: ['alt+shift+r']

  # Redraw all windows.
  - commands: ['wm-redraw']
    bindings: ['alt+shift+w']

  # Launch CMD terminal. Alternatively, use `shell-exec wt` or
  # `shell-exec %ProgramFiles%/Git/git-bash.exe` to start Windows
  # Terminal and Git Bash respectively.
  - commands: ['shell-exec cmd']
    bindings: ['alt+k']

  - commands: ['shell-exec chrome']
    bindings: ['alt+l']

  - commands: ['shell-exec p']
    bindings: ['alt+m']

  
  # 前一个后一个桌面
  # Focus the next/previous active workspace defined in `workspaces` config.
  - commands: ['focus --next-active-workspace']
    bindings: ['alt+d']
  - commands: ['focus --prev-active-workspace']
    bindings: ['alt+a']

  # 上个桌面
  # Focus the workspace that last had focus.
  - commands: ['focus --recent-workspace']
    bindings: ['alt+q']


  # 多显示器
  # Move the focused window's parent workspace to a monitor in a given
  # direction.
  - commands: ['move-workspace --direction left']
    bindings: ['alt+shift+a']
  - commands: ['move-workspace --direction right']
    bindings: ['alt+shift+f']
  - commands: ['move-workspace --direction up']
    bindings: ['alt+shift+d']
  - commands: ['move-workspace --direction down']
    bindings: ['alt+shift+s']
  

  
  # 切换桌面
  # Change focus to a workspace defined in `workspaces` config.
  - commands: ['focus --workspace 1']
    bindings: ['alt+1']
  - commands: ['focus --workspace 2']
    bindings: ['alt+2']
  - commands: ['focus --workspace 3']
    bindings: ['alt+3']
  - commands: ['focus --workspace 4']
    bindings: ['alt+4']
  - commands: ['focus --workspace 5']
    bindings: ['alt+5']
  - commands: ['focus --workspace 6']
    bindings: ['alt+6']
  - commands: ['focus --workspace 7']
    bindings: ['alt+7']
  - commands: ['focus --workspace 8']
    bindings: ['alt+8']
  - commands: ['focus --workspace 9']
    bindings: ['alt+9']


  # 移动窗口去某个桌面
  # Move focused window to a workspace defined in `workspaces` config.
  - commands: ['move --workspace 1', 'focus --workspace 1']
    bindings: ['alt+shift+1']
  - commands: ['move --workspace 2', 'focus --workspace 2']
    bindings: ['alt+shift+2']
  - commands: ['move --workspace 3', 'focus --workspace 3']
    bindings: ['alt+shift+3']
  - commands: ['move --workspace 4', 'focus --workspace 4']
    bindings: ['alt+shift+4']
  - commands: ['move --workspace 5', 'focus --workspace 5']
    bindings: ['alt+shift+5']
  - commands: ['move --workspace 6', 'focus --workspace 6']
    bindings: ['alt+shift+6']
  - commands: ['move --workspace 7', 'focus --workspace 7']
    bindings: ['alt+shift+7']
  - commands: ['move --workspace 8', 'focus --workspace 8']
    bindings: ['alt+shift+8']
  - commands: ['move --workspace 9', 'focus --workspace 9']
    bindings: ['alt+shift+9']

```


## powertoys 配置文件


![](doc/powertoys_settings_133819102381786548.ptb)



## linux reader



























