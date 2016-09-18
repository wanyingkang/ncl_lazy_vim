in progress...

ncl_lazy_vim README
===================

If you are using vi/vim/gvim for scripting with NCL, you can sometimes hardly remember NCL commands or you are just too lazy to type out "gsFillWTF..." all the time, this might be something for you.

![animation]( ncl_completion.gif )

Configuration instructions
--------------------------

* Add the lines of "add_ncl_complete_to_your_vimrc" to your "~/.vimrc" to include the complete function <br>
```
cat add_ncl_complete_to_your_vimrc >> ~/.vimrc
```

Optional: <br>
1. Variable completion: Set a file path and enable vars_completion in your ".vimrc" <br>
![animation]( vars_completion.gif ) <br>
2. If you want to use &lt;Tab> for auto-completion like in your shell, add those lines to your .vimrc <br> FIXME: Doesnt replace <C-U><C-U> yet, but only <C-N>
```
" Use TAB to complete when typing words, else inserts TABs as usual.
" Uses dictionary and source files to find matching words to complete.
" "See help completion for source,
" Note: usual completion is on <C-n> but more trouble to press all the time.
" Never type the same word twice and maybe learn a new spellings!
" Use the Linux dictionary when spelling is in doubt.
" Window users can copy the file to their machine.
function! Tab_Or_Complete()
  if col('.')>1 && strpart( getline('.'), col('.')-2, 3 ) =~ '^\w'
    return "\<C-N>"
  else
      return "\<Tab>"
  endif
endfunction
:inoremap <Tab> <C-R>=Tab_Or_Complete()<CR>
```
Source: http://vim.wikia.com/wiki/Smart_mapping_for_tab_completion <br>
The usual &lt;Tab> command will still be executed when no completion is feasable, eg. in the beginning of (empty) lines <br>
3. If you fancy other auto-completion setting, play with the line
```
set complete=longest,menuone
```
The current setting completes up to the last common string and then shows a menu. Other options are listed in the vim help or http://vimdoc.sourceforge.net/htmldoc/options.html#'completeopt' <br>

<br>

For syntax highlighting: <br>
1. coming soon dynamical hopefully <br> for now data from https://www.ncl.ucar.edu/Applications/editor.shtml


Operating instructions
----------------------
Start typing your desired cdo command and hit &lt;Control-X>&lt;Control-U>
```
res@gsF<Ctrl-X><Ctrl-U>
addf<Ctrl-X><Ctrl-U>
```
Get the following autocompletion options 
```
gsFillBackgroundColor   NCL Res: This resource of type ... Default: Transparent
gsFillColor             NCL Res: This resource of type ... Default: Foreground
or
addfile                 NCL Func.: 
addfiles                NCL Func.:
or
<ncl_command>           <type>: <description>         ... Default: <value>
...
```
Hit &lt;Ctrl-N> go get the first shown match
```
res@gsFillBackgroundColor
or
addfile
```
Hit another &lt;Ctrl-N> to choose the next match or move down with arrow keys and hit <Enter> for your choice 



Copyright and licensing information
-----------------------------------
* helpme

Known bugs
----------
* just starting
* static ncl data

Contact information
-------------------
Aaron Spring <br> Bundesstraße 53 <br> ZMAW Room 229 <br> aaron.spring@mpimet.mpg.de <br> <br> 
Looking forward to receiving your questions, comments or wishes


Changelog
---------
* v0.1:  uses all NCL resources and NCL functions from website <br>
        also completes variables gathered by 'cdo vardes files' if cdo installed <br>
        requires '*.ncl' files, variable_completion <br>
        ncl_completion can be enabled or disabled in .vimrc <br> 

Working on
----------
* syntax highlighting
* getting functions and resources dynamically, see https://github.com/aaronspring/cdo_lazy_vim
* anything else needed?

Credits and acknowledgements
----------------------------
* Prince K Xavier, the dude who set up auto-completion for NCL and made me think to do this for CDO 
 

Sister project
--------------
* same stuff for NCL: https://github.com/aaronspring/cdo_lazy_vim