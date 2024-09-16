# How do i make plugin on zerobrane studio IDE?
Tutorial about Making plugin on zerobrane studio IDE

official doc here : https://studio.zerobrane.com/doc-plugin

## What is a zb plugin ?
it is a single .lua file in packages folder zb directory.

## What are plugin features ?
- [interpreter](interpreter.md) (run debuger/ custom binairy)
- [api](api.md) (auto-completion)
- an other ...

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
    ide:AddInterpreter(name, interpreter)
    ide:AddAPI("lua", name, api)
  end,
  onUnRegister = function(self)
    ide:RemoveInterpreter(name, interpreter)
    ide:RemoveAPI("lua", name)
  end,
}

```
