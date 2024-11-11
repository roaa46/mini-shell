# Mini Shell Program

This is a simple shell program written in C called **mini shell**. It allows users to run commands either interactively or through a batch file. The shell includes basic commands like `exit` and `cd` and looks for other commands in the directories listed in the system’s `PATH` environment variable.

## Features

- **Interactive Mode**: Lets users enter commands one by one.
- **Batch Mode**: Reads and executes commands from a file.
- **Built-in Commands**: Supports `exit` to quit the shell and `cd` to change directories.
- **Command Execution**: Looks for commands in `PATH` and runs them in a new process.

## Compilation

Compile the program using:

```bash
gcc -o mini-shell shell.c
```

## Usage

### Interactive Mode

To start the shell interactively, run:

```bash
./mini-shell
```

You'll see the prompt:

```bash
shell>
```

You can enter commands like:

- **Change directory**:

  ```bash
  shell> cd /home/user
  ```

- **List files**:

  ```bash
  shell> ls
  ```

- **Exit**:

  ```bash
  shell> exit
  ```

### Batch Mode

Run the shell with a file of commands:

```bash
./mini-shell batchfile.txt
```

This will execute each command from `batchfile.txt` in order.

Example `batchfile.txt`:

```bash
cd /home/user
ls
exit
```

In batch mode, the `shell>` prompt won’t be displayed, and the shell will exit once all commands are executed.

### Built-in Commands

The shell has these built-in commands:

- **`exit`**: Closes the shell, printing `Exiting shell`.
- **`cd <directory>`**: Changes the current directory. If unsuccessful, an error is shown.

### Command Execution

For other commands, the shell:

1. **Parses the command** into arguments.
2. **Creates a child process** to run the command.
3. **Searches `PATH`** for the command's executable.
4. **Executes the command** if found; otherwise, it shows an error.

## Error Handling

The shell handles these errors:

- **No `PATH` variable**: Shows an error.
- **Command not found**: Shows an error.
- **Failed `cd`**: Shows an error if the directory is invalid.
- **Forking error**: Shows an error if process creation fails.

## Example Usage

### Interactive Example

```bash
$ ./mini-shell
shell> cd /home/user
shell> ls
shell> exit
Exiting shell
```

### Batch Mode Example

Given a `cmds.txt` with:

```bash
echo Hello, world!
ls
pwd
exit
```

Run in batch mode:

```bash
$ ./mini-shell cmds.txt
```

This will execute each command and exit.

## Limitations

- **No command history**
- **No background processes**
- **No signal handling (like `Ctrl+C`)**
- **Only `exit` and `cd` as built-in commands**
- **No piping or redirection support**
- **No tab completion**

