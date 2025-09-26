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
