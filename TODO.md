## WIP

```sh
#!/usr/bin/env -S  mlr -s

--c2j

# // FILTER...
filter '$id > 1'

# // MODIFY a field's value
then put '$id = $id + 1'

# // MODIFY a field's value - with an ENV VAR
then put -s NUM=3 '$id = $id + @NUM'

# // ADD a field
then put '$period = 2023'

# // ONLY specific fields
#then cut -f name,age

then cat
```
