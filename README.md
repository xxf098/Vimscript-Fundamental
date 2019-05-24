# Vimscript Fundamental
* String
```vim
"matchstr
"match a git hash like '981ff54 init'
function! s:GetGitHash(gitlog)
  let gitlog = a:gitlog
  let hash = matchstr(gitlog, '^[0-9a-z]\{7,\}\s')
  return hash
endfunction
```
* Variable
```vim
```
* Array
```vim
let hashes = [
  \'b68d138',
  \'c266945',
  \'1af7d56'
  \]
let hashes = add(hashes, 'a2dabfc')
let hash1 = hash[0]
let hash2 = get(hash, 1, '')
```
* Dictionary
```vim
"multiple line dictionary
let user = {
\'username': 'name',
\'age': '20',
\'gender': 'male',
\'interests': ['something interesting']
\}
"set dictionary item
let user.username = 'newname'
" nested dictionary access
let interest = user.interests[0]
"iterate dictionary
for item in items(user)
  let [key, value] = item
  echom key ': ' . value
endfor
```
* Condition
```vim
  let condition1 = 0
  let condition2 = 1
  if !condition1
    echom 'negate condition'
  endif
  if condition1 || condition2
    echom 'or condition'
  endif
  if !condition1 && condition2
    echom "and condition"
  endif
  " TODO: =~?
```
* Function
```vim
"default parameters
function! s:defaultParams(param1, ...)
  "get param1 value
  let param1 = a:param1
  "get params length
  let param_length = a:0
  "set default value for param2
  let param2 = get(a:, 1, '')
endfunction
```
* execute
```vim
"execute command
execute "normal! gg"
"execute dynamic command
let line_num = 10
execute "normal! " . line_num . "gg"
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
* Regex
```vim
"default is magic mode
" find more here: http://vimdoc.sourceforge.net/htmldoc/pattern.html
" $ end of line
" ^ start of line
" \(\) group
" \s space
" * zero or more times
" \+ one or more times
" \? zero or one time
" \{2,\} 2 or more times
" \{2,4} only match 2,3,4 times
" . match any character
" [a-z] match characters from a to z
" \| or
" \s space
" \n new line
" \. match .
" \\ match \
```
* File
```vim
let filename = 'names.data'
let lines = readfile(filename)
let files = system('ls -thla')
call writefile(files, 'files.data')
```