# 🐚  Nushell Cheat Sheet

A quick reference for experienced Bash users learning Nushell.

---

## 🔧 Basic Shell

| Task              | Bash                    | Nushell                 |     |
| ----------------- | ----------------------- | ----------------------- | --- |
| Current directory | `pwd`                   | `pwd`                   |     |
| Change directory  | `cd dir`                | `cd dir`                |     |
| List files        | `ls`                    | `ls`                    |     |
| Make directory    | `mkdir newdir`          | `mkdir newdir`          |     |
| Remove file/dir   | `rm file` / `rm -r dir` | `rm file` / `rm -r dir` |     |
| Copy file         | `cp a.txt b.txt`        | `cp a.txt b.txt`        |     |
| Move file         | `mv a.txt b.txt`        | `mv a.txt b.txt`        |     |
| Command history   | `history`               | `history`               |     |
| Exit shell        | `exit`                  | `exit`                  |     |

---

## 📂 File Inspection

| Task                      | Bash                             | Nushell                         |
|---------------------------|----------------------------------|---------------------------------|
| Read a file               | `cat file.txt`                   | `open file.txt`                |
| View file line by line    | `cat file.txt \| less`           | `open file.txt \| less`        |
| JSON/YAML/TOML viewer     | Use `jq`, `yq`, etc.             | `open file.json`               |

---

## 🔄 Pipes & Data

| Task                        | Bash                                 | Nushell                             |
|-----------------------------|--------------------------------------|-------------------------------------|
| Pipe output                 | `cmd1 \| cmd2`                        | `cmd1 \| cmd2`                      |
| Filter rows                 | `grep "foo"`                         | `where name == "foo"`              |
| Select column/field         | `cut -d',' -f1`                      | `get column_name`                  |
| Count lines/items           | `wc -l`                              | `length`                           |
| Sort data                  | `sort`                               | `sort-by column_name`              |
| Unique values              | `sort \| uniq`                       | `uniq`                             |

---

## 🔁 Loops & Variables

| Task                     | Bash                                   | Nushell                          |
|--------------------------|----------------------------------------|----------------------------------|
| Set variable             | `foo=123`                              | `let foo = 123`                 |
| Print variable           | `echo $foo`                            | `$foo` or `echo $foo`           |
| For loop                 | `for f in *.txt; do echo $f; done`     | `for f in ls *.txt { echo $f.name }` |
| If condition             | `if [ $x -gt 5 ]; then ... fi`         | `if $x > 5 { ... } else { ... }` |

---

## 📊 Working with Structured Data

| Task                     | Nushell Only (No real Bash equivalent) |
|--------------------------|----------------------------------------|
| Open and inspect CSV     | `open data.csv`                        |
| Open JSON                | `open data.json`                       |
| Query JSON               | `open data.json \| get users.0.name`   |
| Filter CSV rows          | `open data.csv \| where age > 30`      |
| Group and count          | `... \| group-by city \| each { ... }` |

---

## ⚙️ Misc

| Task                     | Bash                                   | Nushell                          |
|--------------------------|----------------------------------------|----------------------------------|
| Alias                    | `alias ll="ls -la"`                    | `alias ll = ls -la`              |
| Functions                | `myfn() { echo "hi"; }`                | `def myfn [] { echo "hi" }`      |
| Help command             | `man cmd` or `cmd --help`              | `help cmd`                       |
| Run external program     | `./script.sh`                          | `^./script.sh`                   |
| Use `ENV` vars           | `$HOME`                                | `$env.HOME`                      |


## 🧠 Core Keybindings

| Key             | Action                                           |
|----------------|--------------------------------------------------|
| `Tab`          | Show and cycle through completions               |
| `→` (Right Arrow) | Accept *ghost* suggestion (inline, like Fish) |
| `↑` / `↓`      | Navigate command history                         |
| `Ctrl + C`     | Cancel current input or running command          |
| `Ctrl + L`     | Clear the screen                                 |
| `Ctrl + U`     | Clear the line before the cursor                 |
| `Ctrl + A`     | Move cursor to beginning of line                 |
| `Ctrl + E`     | Move cursor to end of line                       |
| `Ctrl + W`     | Delete the word before the cursor                |
| `Ctrl + D`     | Exit the shell (EOF)                             |
| `Ctrl + R`     | Search through history (incremental search)      |

---

## 🛠️ Other Useful Behaviors

| Key Combination | Action                              |
|-----------------|-------------------------------------|
| `Ctrl + Space`  | Trigger completions manually        |
| `Alt + B`       | Move cursor one word backward       |
| `Alt + F`       | Move cursor one word forward        |

---

### ⚙️ Customize Keybindings

Edit or create a custom keybindings file:

open ~/.config/nushell/keybindings.nu

---


### 📦 Bonus: Common Translations

##### Bash
cat data.csv | grep "CA" | cut -d',' -f1

##### Nushell
open data.csv | where state == "CA" | get name
