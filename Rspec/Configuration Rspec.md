
Configuration Rspec in ` ~/.rspec` fil 

#### To open Rspec file 

```shell
$ echo ~/.rspec
/Users/username/.rspec
```

#### To display config in terminal 
```shell
$ cat ~/.rspec                             
--color --format documentation
--format=progress
--format=documentation
```

Config format:
- progress : Display only dots
- documentation : Display context and name of spec 

#### To add config format in file 

```shell
$ echo "--format=documentation" >> ~/.rspec
```


Here are a few things you can write in the `.rspec` file to configure rspec:

1. `--no-color`, `--color` (`--color` Shows green output for passing tests, red for failing tests)
2. `--format progress`, `--format documentation` (`--format progress` will show your test examples like this in the terminal: "`....F..`" - Dots are passing, F is failed. `--format documentation` will instead of showing dots and f's, will instead show the example descriptions of your tests in a green(passing) or red(failing) color.
3. `--no-profile`, `--profile` (This one will determine whether or not RSpec shows you your fastest and slowest tests)
4. `--no-fail-fast`, `--fail-fast` (`--no-fail-fast` will run all tests, `--fail-fast` will only output the first test that fails if any)
5. `--order defined`, `--order random` (This one will either run the tests you have written in the order they are defined or at random)

If you create a `.rspec` file in your computers user directory, you can configure RSpec globally there and the rest of your projects will use that configuration.

If you use a `.rspec` file in the project directory, it will override any global `.rspec` configurations for that project.