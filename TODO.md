## WIP

- `script.mlr`:

```sh
#!/usr/bin/env -S  mlr -s

--c2j

# // FILTER...
filter '$id > 1'

# // MODIFY a field's value
then put '$id = $id + 1'

# // MODIFY a field's value - with a var
then put -s NUM=2 '$id = $id + @NUM'


# // Can access ENV variables...
then put '$id = $id + int(ENV["NUM"])'
then put '@x = ENV["NUM"]; $ENV_NUM = @x'

# // DSL has a `system()` function
# // https://github.com/johnkerl/miller/issues/315#issuecomment-595652559
then put '$sys_call_PATH = system("echo '"$PATH"'")'


# // ADD a field
then put '$period = 2023'

# // ONLY specific fields
#then cut -f name,age

then cat
```

- CSV:

```csv
id,name,age
1,Ami,20
2,Bob,80
```

- Run:

```sh
cat csv.csv | ./script.mlr
cat csv.csv | NUM=10 ./script.mlr

./script.mlr csv.csv
NUM=10 ./script.mlr csv.csv
```

- Output:

```json
[
{
  "id": 6,
  "name": "Bob",
  "age": 80,
  "ENV_NUM": "",
  "sys_call_PATH": "/usr/local/bin:/usr/bin:/bin:/usr/local/games:/usr/games:/sbin:/usr/sbin",
  "period": 2023
}
]
```
