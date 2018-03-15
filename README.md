the tree of antd add contextmenu.

## images

![image](https://github.com/Tiansuyan/test/blob/master/public/images/index.png)


## coding

use antd and react-contextmenu:

```js
{
  import { ContextMenu, MenuItem, ContextMenuTrigger } from "react-contextmenu"


  handleClick = (e, data) => {
    console.log("handleClick", e, data);
  };
  collect = data => {
    console.log("collect", data);
  };

  /*触发右击的元素 ContextMenuTrigger*/
  const loop = data =>
      data.map(item => {
        const index = item.key.indexOf(searchValue);
        const beforeStr = item.key.substr(0, index);
        const afterStr = item.key.substr(index + searchValue.length);
        const title =
          index > -1 ? (
            <ContextMenuTrigger
              data={item.key}
              collect={this.collect}
              id="some_unique_identifier"
            >
              <span>
                {beforeStr}
                <span style={{ color: "#f50" }}>{searchValue}</span>
                {afterStr}
              </span>
            </ContextMenuTrigger>
          ) : (
            <ContextMenuTrigger
              data={item.key}
              collect={this.collect}
              id="some_unique_identifier"
            >
              <span>{item.key}</span>
            </ContextMenuTrigger>
          );
        if (item.children) {
          return (
            <TreeNode key={item.key} title={title}>
              {loop(item.children)}
            </TreeNode>
          );
        }
        return <TreeNode key={item.key} title={title} />;
      });



      /*菜单信息*/
      <ContextMenu id="some_unique_identifier">
          <MenuItem onClick={this.handleClick}>添加子菜单</MenuItem>
          <MenuItem data={"编辑"} onClick={this.handleClick}>
            编辑
          </MenuItem>
          <MenuItem divider />
          <MenuItem data={"删除"} onClick={this.handleClick}>
            删除
          </MenuItem>
        </ContextMenu>
}
```


## Folder Structure

After creation, your project should look like this:


