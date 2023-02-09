# VIM Cheatsheet

## Neovim Config Notes/Todo:
* Disable completion dynamically. The following can be used to disable from the prompt:
    * :lua require("cmp").setup({enabled = false})
* lsp-zero's recommened preset doesn't let us handle cmp, need to use lsp-compe preset: https://github.com/VonHeikemen/lsp-zero.nvim/pull/99

## Useful Movements/Commands
* Jump to previous/next jump: *Ctrl-I/Ctrl-0*
* Select entire function:
    * *$* to go to end of line where bracket is
    * *V%* to select to matching bracket using visual-line mode
* Inserting new line at end of file: Go:
