# How do i make plugin on zerobrane studio IDE?
Tutorial about Making plugin on zerobrane studio IDE

official doc here : https://studio.zerobrane.com/doc-plugin

## What is a zb plugin ?
it is a single .lua file in packages folder zb directory.

## What are plugin features ?
- [interpreter](interpreter.md) (run debuger/ custom binairy)
- [api](api.md) (auto-completion)
- [MenuEditor](menueditor.md) (edit menu/editor acting)

## Plugin template.lua
```lua
local name = "template"

local interpreter={} --your interpreter table
local api={}         --your api table

-- add lua basic to api
local lua = dofile("api/lua/baselib.lua")
for item, def in pairs(lua) do
  if included[item] then
    api[item] = def
  end
end

-- package template
return {
  name = name,
  description = "Implements "..name,
  author = "you",
  version = 0.1,
  onRegister = function(self)
    ide:AddInterpreter(interpreter.name, interpreter)
    ide:AddAPI("lua", api.name, api)
  end,
  onUnRegister = function(self)
    ide:RemoveInterpreter(interpreter.name, interpreter)
    ide:RemoveAPI("lua", api.name)
  end,
  onMenuEditor = function(self, menu, editor, event)
-- menu editor code
  -- menu = wxMenu wignet             (set menu item)
  -- editor = wxStyledTextCtrl wignet (link menu item -> function)
  end
}

```
[editor API](https://docs.wxwidgets.org/trunk/classwx_styled_text_ctrl.html)<br>
[menu API](https://docs.wxwidgets.org/trunk/classwx_menu.html)<br>
source : [github.com/oblerion/How-do-i-make-plugin-on-zerobrane-studio-IDE-](https://github.com/oblerion/How-do-i-make-plugin-on-zerobrane-studio-IDE-)
