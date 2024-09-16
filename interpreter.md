# interpreter

## interpreter table template
```lua
-- name is variable package
local interpreter={
  name=name,
  description="desc interpreter",
  api={name},
  luaversion="5.3",
  frun=function(self,wfilename) -- when interpreter call
    local cur_file =  wfilename:GetFullPath()
    local bin = "interpreter.exe"
    cmd = string.format("%s %s",bin,cur_file)
    return CommandLineRun(cmd,self:fworkdir(wfilename),true,true,nil,nil,nil)
  end,
  skipcompile = true,
  hasdebugger=false,
  scratchextloop = false,
  takeparameters = true
}
```
