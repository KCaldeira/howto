# HOW-TO DO VARIOUS THINGS

## CHECK OUT GITHUB ARCHIVE AND MAKE VIRTUAL ENVIRONMENT

### 1) Clone the repo (HTTPS example)
git clone <REPO_URL>  # e.g., https://github.com/owner/project.git
cd <project>          # cd into the new folder

### (If the repo uses submodules)
git submodule update --init --recursive

### 2) Create a project-local virtual environment named .venv
python -m venv .venv

### 3) Activate it
source .venv/bin/activate

### 4) Upgrade packaging tools (prevents many build issues)
python -m pip install --upgrade pip setuptools wheel

### 5) Install dependencies
pip install -r requirements.txt

### 6) (Optional) Verify installs
pip check  # reports broken or conflicting deps, if any

## How to activate or deactivate base environment in conda

Sure — here’s the complete file ready to save as
`conda_environments.md`.
You can copy and paste the whole thing into VS Code or any Markdown editor.

---

# Managing Conda Virtual Environments

## 🧪 Create a New Environment
```bash
# Create a new environment named "myenv" with Python 3.11
conda create -n myenv python=3.11
````

---

## ▶️ Activate / Deactivate

```bash
# Activate the environment
conda activate myenv

# Deactivate the environment (return to previous or base)
conda deactivate
```

---

## ⚙️ Fix “CommandNotFoundError” (Conda Not Initialized)

If you see an error like
`CommandNotFoundError: conda activate not found`,
you need to initialize Conda in your shell.

### For WSL / Ubuntu / macOS (bash or zsh)

```bash
conda init bash     # or conda init zsh
exec "$SHELL"       # reload the shell
```

### For Windows PowerShell

```powershell
conda init powershell
# then close and reopen PowerShell
```

---

## 📋 Useful Commands

```bash
conda env list                 # List all available environments
conda activate /path/to/env    # Activate by full path instead of name
conda env remove -n myenv      # Delete an environment
conda run -n myenv python -V   # Run a command in an environment without activating
conda config --set auto_activate_base false  # Disable automatic base activation
```

---

## 💡 Tip for VS Code

* Press **Ctrl + Shift + P** → select **Python: Select Interpreter**.
* Choose your Conda environment (e.g., `myenv`).
* Alternatively, open a new terminal **after activating** Conda; VS Code will use that environment automatically.

---

## 🧰 Optional: Environment File Workflow

You can save or recreate environments from an `environment.yml` file:

```bash
# Export the current environment
conda env export > environment.yml

# Create a new one from the file
conda env create -f environment.yml

# Update an existing one
conda env update -f environment.yml
```



## How to View CSV Files in WSL 2 (Ubuntu)

This guide shows how to look at CSV files directly from an Ubuntu window in WSL 2, using basic terminal commands and optional tools.

---

### 1. Navigate to the CSV File

```bash
cd /path/to/your/csv
ls
```

---

### 2. Basic Ways to View CSV Files

#### Print Entire File
```bash
cat mydata.csv
```

#### Scrollable View
```bash
less mydata.csv
```
**Controls:**
- `Space` = page down  
- `b` = page up  
- `q` = quit  

#### View Beginning or End
```bash
head mydata.csv        # first 10 lines
head -n 20 mydata.csv  # first 20 lines
tail mydata.csv        # last 10 lines
```

#### Table-Like Formatting
```bash
column -s, -t < mydata.csv | less -#2 -N -S
```
**Options explained:**
- `-s,` → use comma as separator  
- `-t` → format as a table  
- `-N` → show line numbers  
- `-S` → chop long lines instead of wrapping  

---

### 3. Optional: Install an Interactive CSV Viewer

For more advanced viewing, install [VisiData](https://visidata.org/):

```bash
sudo apt update
sudo apt install visidata
vd mydata.csv
```

**VisiData Basic Commands:**
- Arrow keys → move around  
- `s` → sort column under cursor  
- `/text` → search for text  
- `q` → quit  

---

### 4. Opening CSV Files in Excel (or LibreOffice) from WSL 2

If you want to open a CSV file in **Excel** (installed on Windows) directly from your WSL 2 terminal:

```bash
explorer.exe mydata.csv
```

This uses Windows' default program for `.csv` files (often Excel).  
- If Excel is your default app, it will open there.  
- If not, it will open in whatever CSV viewer is default.  

**Tip:** You can also move or copy the file into your Windows filesystem and open it manually. For example:

```bash
cp mydata.csv /mnt/c/Users/<YourWindowsUser>/Documents/
```

---

### Summary

- Use `cat`, `less`, `head`, and `tail` for quick inspection.  
- Use `column -s, -t` for nicely formatted tables.  
- Install **VisiData** for interactive exploration.  
- Use `explorer.exe` to open CSVs in **Excel** (or the default Windows program).  
