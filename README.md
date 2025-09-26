🔹 Step 1: GitHub Repository তৈরি

GitHub এ লগইন করুন

Repositories → New

Repository নাম দিন, উদাহরণ: python-ci-demo

Type: Private বা Public (আপনি চাইলে Private রাখতে পারেন)

Initialize this repository with: No (আমরা local থেকে push করব)

Create repository ক্লিক করুন

🔹 Step 2: Local Python Project তৈরি

Local PC তে একটি ফোল্ডার বানান, উদাহরণ:

python-ci-demo/
│── calculator.py
│── test_calculator.py
│── requirements.txt


calculator.py উদাহরণ:

def add(a, b):
    return a + b

def subtract(a, b):
    return a - b

if __name__ == "__main__":
    print("5 + 3 =", add(5, 3))


test_calculator.py উদাহরণ:

from calculator import add, subtract

def test_add():
    assert add(2,3) == 5

def test_subtract():
    assert subtract(5,3) == 2


requirements.txt উদাহরণ:

pytest

🔹 Step 3: Git Initialize এবং push

Terminal (Git Bash) খুলুন:

# ফোল্ডারে ঢোকা
cd /c/Users/DCL/python-ci-demo

# Git repo initialize
git init

# সব ফাইল add
git add .

# প্রথম commit
git commit -m "Initial Python project with unit tests"

# Remote GitHub repo add
git remote add origin https://github.com/Rafsan12345/python-ci-demo.git

# Branch main set
git branch -M main

# Push to GitHub
git push -u origin main


যদি push করতে গিয়ে error আসে “remote contains work”, তাহলে আগে pull করুন:

git pull origin main --allow-unrelated-histories
git push -u origin main

🔹 Step 4: Codespaces setup

GitHub repo এ যান → Code → Codespaces → Create codespace on main

কয়েক সেকেন্ডে Browser এর ভিতরে VS Code-UI খুলবে

Codespaces auto Git clone করবে

🔹 Step 5: Container Environment তৈরি (.devcontainer)

Project root এ .devcontainer/devcontainer.json ফোল্ডার/ফাইল তৈরি করুন:

{
  "name": "Python CI Demo",
  "image": "mcr.microsoft.com/vscode/devcontainers/python:3.10",
  "postCreateCommand": "pip install -r requirements.txt",
  "customizations": {
    "vscode": {
      "extensions": ["ms-python.python", "ms-python.vscode-pylance"]
    }
  }
}


ব্যাখ্যা:

Python 3.10 environment

requirements.txt auto install হবে

Python VS Code extension ready

🔹 Step 6: Codespaces terminal থেকে কোড রান

Codespaces terminal এ:

# Python script চালানো
python calculator.py

# Unit test চালানো
pytest -v


Output দেখাবে: Calculation result + test pass/fail





.............................





☁️ Option 2: সরাসরি GitHub রিপোজিটরিতে (লোকাল মেশিন লাগবে না)

GitHub repo তে যান → Add file → Create new file

File path লিখুন:

.devcontainer/devcontainer.json


(GitHub auto .devcontainer ফোল্ডার তৈরি করবে)

devcontainer.json এর কনটেন্ট paste করুন

Commit changes চাপুন
