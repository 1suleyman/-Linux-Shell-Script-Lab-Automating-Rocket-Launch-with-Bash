# 🛰️ Linux Shell Script Lab – Automating Rocket Launch with Bash

In this lab, I learned how to **automate a sequence of commands** into a single **shell script**, turning a manual process (launching rockets using the `rocket` CLI) into an efficient, repeatable automation.
The lab demonstrated **how to create, execute, and configure shell scripts** — including permissions, PATH setup, and best practices for script naming.

---

## 📋 Lab Overview

**Goal:**

* Automate the **rocket launch sequence** (from creation to lift-off) using a **Bash script**
* Learn how to **make scripts executable** and **add them to the PATH**
* Understand **file permissions**, **environment variables**, and **naming conventions** for commands

**Learning Outcomes:**

* Write and execute a simple Bash script step-by-step
* Configure PATH for running custom scripts globally
* Set executable permissions using `chmod +x`
* Apply best practices for script naming and reusability

---

## 🛠 Step-by-Step Journey

### Step 1 — Define the Problem

From the previous lab, we manually ran multiple commands to launch a rocket:

1. Create a mission directory
2. Add a rocket
3. Start power systems
4. Start sequence, engine, and lift-off
5. Verify status

Repeating these steps manually for each mission can be time-consuming — so we decided to **automate it using a shell script**.

---

### Step 2 — Plan the Script Logic

Before writing, outline the sequence clearly:

```text
mkdir <mission>
rocket-add <mission>
rocket-start-power <mission>
rocket-internal-power <mission>
rocket-start-sequence <mission>
rocket-start-engine <mission>
rocket-lift-off <mission>
rocket-status <mission>
```

✅ Having a plan ensures a clean, error-free script flow.

---

### Step 3 — Create the Script File

Created a script named `create_and_launch_rocket.sh` and added all commands in the same order as above:

```bash
#!/bin/bash
# Script to create and launch a rocket mission

MISSION_NAME=$1

mkdir $MISSION_NAME
rocket-add $MISSION_NAME
rocket-start-power $MISSION_NAME
rocket-internal-power $MISSION_NAME
rocket-start-sequence $MISSION_NAME
rocket-start-engine $MISSION_NAME
rocket-lift-off $MISSION_NAME
rocket-status $MISSION_NAME
```

✅ The `.sh` extension indicates a **shell script**, and the first line (`#!/bin/bash`) defines the interpreter.

---

### Step 4 — Run the Script Using Bash

Execute the script directly with Bash:

```bash
bash create_and_launch_rocket.sh luna-mission
```

✅ Bash executes each command **sequentially**, waiting for each step to complete before proceeding.

---

### Step 5 — Make the Script Executable

Initially, running the script directly (e.g., `./create_and_launch_rocket.sh`) results in a **Permission denied** error.
This happens because the **execute bit** is not set.

Check permissions:

```bash
ls -l create_and_launch_rocket.sh
```

Set execute permissions:

```bash
chmod +x create_and_launch_rocket.sh
```

✅ Now you can run the script as:

```bash
./create_and_launch_rocket.sh luna-mission
```

---

### Step 6 — Run Script Like a Command (No Path Needed)

To execute the script like any Linux command, it must be accessible in your system’s **PATH**.

Append the directory path containing the script to the PATH variable:

```bash
export PATH=$PATH:/home/michael
```

✅ This lets you run it from anywhere:

```bash
create_and_launch_rocket luna-mission
```

No need to specify `./` or the full directory path.

---

### Step 7 — Verify Command Location

Use the `which` command to confirm where the executable is located:

```bash
which create_and_launch_rocket
```

Output:

```
/home/michael/create_and_launch_rocket
```

✅ Confirms your script is now recognized as a system command.

---

### Step 8 — Best Practices for Shell Scripts

| ✅ **Good Practice**                                   | 🚫 **Avoid**                                  |
| ----------------------------------------------------- | --------------------------------------------- |
| Use descriptive names (`create_and_launch_rocket.sh`) | Names like `test.sh` or `script1.sh`          |
| Use `.sh` extension if not making executable          | Unclear file types                            |
| Leave off `.sh` if creating a custom command          | `create_and_launch_rocket.sh` as command name |
| Include a shebang (`#!/bin/bash`)                     | Forgetting interpreter                        |
| Keep logic ordered and commented                      | Messy, unstructured scripts                   |

---

## 🧠 Key Concepts Reinforced

| Concept                       | Description                                 |
| ----------------------------- | ------------------------------------------- |
| **Bash script structure**     | Scripts run top-to-bottom, line by line     |
| **Execution permissions**     | Controlled with `chmod +x`                  |
| **PATH environment variable** | Defines where the OS searches for commands  |
| **Command creation**          | Custom scripts can act like system commands |
| **Naming clarity**            | Names should reflect functionality          |

---

## 💡 Notes / Tips

* Think of shell scripts as **automation blueprints** for repetitive tasks.
* Always **plan logic first** before writing — clarity saves debugging time.
* Use `chmod +x` to make your script executable, and `export PATH` for convenience.
* Avoid generic names; imagine a teammate reading your script in six months.

---

## ✅ Summary Commands

| Task            | Command                                         |
| --------------- | ----------------------------------------------- |
| Create script   | `vi create_and_launch_rocket.sh`                |
| Make executable | `chmod +x create_and_launch_rocket.sh`          |
| Run with Bash   | `bash create_and_launch_rocket.sh luna-mission` |
| Run directly    | `./create_and_launch_rocket.sh luna-mission`    |
| Add to PATH     | `export PATH=$PATH:/home/michael`               |
| Check location  | `which create_and_launch_rocket`                |

---

### 🏁 End of Lab

Successfully automated the **Rocket Launch sequence** using a **custom Bash script** — learning to:
✅ Create structured scripts
✅ Set execution permissions
✅ Configure PATH for custom commands
✅ Follow naming and scripting best practices

This lab transforms repetitive CLI work into **simple, reusable automation** — a key step toward becoming a proficient **DevOps engineer**.
