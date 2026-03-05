# Minishell - @42Born2Code

## 💡 About

**Minishell** is a 42 school project that challenges us to create our own shell. It is a miniature version of **Bash**, providing a command-line interface to interact with the operating system.

This project is a deep dive into the **process lifecycle**, **file descriptors**, **signal handling**, and **abstract syntax trees (AST)** or complex linked lists for parsing.

---

## 🛠️ Features

My implementation of Minishell includes:

* **Interactive Prompt**: Displays a prompt while waiting for a new command.
* **Command History**: Working history (up/down arrows) using the `readline` library.
* **Executable Search**: Finds and executes binaries based on the `PATH` variable or relative/absolute paths.
* **Built-ins**:
* `echo` (with `-n` option)
* `cd` (with relative or absolute paths)
* `pwd`, `export`, `unset`, `env`, `exit`


* **Redirections**:
* `<` : Redirects input.
* `>` : Redirects output (truncate).
* `<<` : Here-doc (reads input until a delimiter is reached).
* `>>` : Redirects output (append).


* **Pipes** (`|`): The output of each command in the pipeline is connected to the input of the next command via a pipe.
* **Environment Variables**: Handles `$` expansions and `$?` (exit status of the last pipeline).
* **Signals**: Handles `Ctrl-C`, `Ctrl-D`, and `Ctrl-\` similarly to Bash.

---

## 📐 Architecture

The execution of a command follows four main stages:

1. **Lexer (Tokenization)**: Breaks the input string into "tokens" (words, pipes, redirections).
2. **Parser**: Organizes tokens into a data structure (like a command table or a tree) while handling syntax errors.
3. **Executor**: Handles forks, pipes, and redirections to run the commands.

---

## 🚀 Usage

### Compilation

The project requires the `readline` library. To compile, run:

```bash
make

```

### Execution

Launch the shell:

```bash
./minishell

```

Once inside, you can use it like a regular Bash shell:

```bash
minishell$ ls -l | grep "txt" > output.txt
minishell$ cat < output.txt
minishell$ export MY_VAR=hello
minishell$ echo $MY_VAR

```

---

## ⚠️ Technical Challenges

* **Memory Management**: Since a shell runs indefinitely, every single byte allocated during a command cycle must be freed to avoid leaks.
* **Concurrency**: Properly waiting for child processes and preventing "zombie" processes.
* **Terminal State**: Managing the `readline` state and ensuring the terminal configuration is restored correctly.

---
