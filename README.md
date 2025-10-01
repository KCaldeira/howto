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
