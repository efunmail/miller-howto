## WIP

```sh
#!/usr/bin/env -S  mlr -s

--c2j

# // FILTER...
filter '$id > 1'

# // MODIFY a field's value
then put '$id = $id + 1'

# // MODIFY a field's value - with a var
then put -s NUM=$NUM '$id = $id + @NUM'

# // DSL has a `system()` function
# // https://github.com/johnkerl/miller/issues/315#issuecomment-595652559
then put '$sys_call_PATH = system("echo '"$PATH"'")'

# // ADD a field
then put '$period = 2023'

# // ONLY specific fields
#then cut -f name,age

then cat
```
