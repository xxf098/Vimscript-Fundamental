# Vimscript-Fundamenta
* Dictionary
```vim
"multiple line dictionary
let user = {
\'username': 'name',
\'age': '20',
\'gender': 'male'
\}
"set dictionary item
let user.username = 'newname'
"iterate dictionary
for item in items(user)
  let [key, value] = item
  echom key ': ' . value
endfor
```
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
