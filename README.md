# Vimscript-Fundamenta
* Run system command
```vim
function! s:GetGitLogs() abort
  let cmd = 'git log --oneline'
  let output = system(cmd)
  if v:shell_error
    throw 'Fail to get git logs'
  endif
  return output
endfunction
```
