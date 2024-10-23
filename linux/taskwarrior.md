Taskwarrior is a command line tui that manage tasks.

# Config Command

Used to change the defaults of taskwarrior.

```zsh
task config confermation off

task config $Name $Value
```

# Show Command

To show all the default of taskwarriror that you can change with `config`

``` zsh
task show confermation

task show $Name
```

# Tasks 

### add task

To add tasks we use:

```zsh
task add house work
task add $Name
```

The name can have spaces.

### add project

```zsh
task add project:$NameofProject $NameofTask
```

We use the same proejct name to add different tasks.

### Add priority

```zsh
task add priority:H reading
```

### delete task

```zsh
task $Num delete
```

Num is the number of id.

