## 配置nvim
###依赖
```
yay -S nvim fzf python-pip npm yarn notejs clang
pip install neovim
```
### 复制配置文件
首先复制nvim文件夹到~/.config  
之后打开nvim,运行`:PackerSync`即可完成插件安装  
### 后续配置
#### coc.nvim
`coc.nivm`需要进插件文件夹运行`yarn install`方可使用  
``` sh
cd .local/share/nvim/site/pack/packer/start/coc.nvim/
yarn install
```
之后打开nvim  
运行：
```
:CocInstall coc-sh coc-clangd coc-html coc-sumneko-lua coc-markdownlint
```
### 插件列表
插件管理器：packer.nvim  
主题：nord.nvim  
lsp：coc.nvim  
文件查找：nvim-fzf  
文件树：nvim-tree.lua  
markdown阅读：markdown-preview.nvim  
代码高亮：nvim-treesitter  
状态栏：nvim-lualine  

---
[返回到上一页](https://storm-1614.github.io/blog-linux/)  
[返回到主页](https://storm-1614.github.io/)  
