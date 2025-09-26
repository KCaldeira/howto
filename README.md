# HOW-TO DO VARIATION THINGS

# CHECK OUT GITHUB ARCHIVE AND MAKE VIRTUAL ENVIRONMENT

# 0) Install Git + Python 3.x from git-scm.com and python.org (check "Add Python to PATH")
# 1) Clone
git clone <REPO_URL>
cd <project>

# (If submodules)
git submodule update --init --recursive

# 2) Create venv
py -3 -m venv .venv

# 3) Activate
.\.venv\Scripts\Activate.ps1

# 4) Upgrade packaging tools
python -m pip install --upgrade pip setuptools wheel

# 5) Install requirements
pip install -r requirements.txt

# 6) (Optional) Verify
pip check
