# api

```lua
local api={
-- function print(text) 
  print = {
    type = "function",
    description = [[A print function]],
    --       var:type
    args = "(text:string)",
    returns = "()"
  },
-- function getX() => x
  getX = {
    type = "function",
    description = [[A function to get x value]],
    args = "()",
    returns = "(x:number)"
  }
}
```

[back](README.md)
