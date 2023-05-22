`cdiff` -> "Content Diff"

This is a simple program that compares the text content of two HTML documents and then shows the diff in `nvim`.

It tries to align lines, even if the order is different, so that a direct line-by-line comparison can be made.

# Setup

This requires that you configure `nvim` to force a line-by-line diff:

```
" In `init.vim` or equivalent

" Configure vimdiff
" to force line-by-line comparison,
" instead of trying to figure out
" what lines should go together.
set diffexpr=LineDiff()
function LineDiff()
   let opt = ""
   if &diffopt =~ "icase"
     let opt = opt .. "-i "
   endif
   if &diffopt =~ "iwhite"
     let opt = opt .. "-b "
   endif
   silent execute "!diff <(nl -ba " .. v:fname_in .. ") <(nl -ba " .. v:fname_new .. ") > " .. v:fname_out
   redraw!
endfunction
set diffopt+=followwrap " Preserve line-wrapping settings when using vimdiff
```

# Usage

```
cdiff /path/to/source-of-truth.html /path/to/version-to-update.html
```
