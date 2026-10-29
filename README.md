# Assignment 4 — Python CI Pipeline with GitHub Actions

[!\[Python CI](https://github.com/mhatreanuj57-alt/First_CI_Pipeline/actions/workflows/python-ci.yml/badge.svg)](https://github.com/sakshu172007/First\_CI\_Pipeline/actions/workflows/python-ci.yml)

Build ten beginner-friendly Python algorithms and verify them with pytest locally
and automatically on GitHub. Each program is added in its own commit, after the
previous program passes CI.

Repository: [First\_CI\_Pipeline](https://github.com/mhatreanuj57-alt/First_CI_Pipeline)

## Technologies

Python 3.12 or newer, pytest, Git, and GitHub Actions on Ubuntu.

## Programs 21–30

|No.|Function|Purpose|
|-|-|-|
|21|`largest\\\_word(sentence)`|Longest word; strip surrounding punctuation; first wins ties|
|22|`is\\\_anagram(first, second)`|Compare letters ignoring case and spaces|
|23|`bubble\\\_sort(numbers)`|Return a new ascending list using bubble sort|
|24|`merge\\\_sorted\\\_lists(list1, list2)`|Merge two sorted lists|
|25|`find\\\_max\\\_min(numbers)`|Return maximum and minimum; reject an empty list|
|26|`sum\\\_of\\\_list(numbers)`|Accumulate list elements with a loop|
|27|`rotate\\\_list(items, k)`|Rotate right; negative positions rotate left|
|28|`set\\\_intersection(first, second)`|Return common set elements|
|29|`is\\\_armstrong(number)`|Check digit powers; negative numbers return false|
|30|`decimal\\\_to\\\_binary(number)`|Convert by repeated division; reject negative numbers|

## Final project structure

```text
First\\\_CI\\\_Pipeline/
├── .github/workflows/python-ci.yml
├── codes/
│   ├── 21\\\_largest\\\_word.py
│   ├── 22\\\_anagram\\\_strings.py
│   ├── 23\\\_sort\\\_without\\\_sort.py
│   ├── 24\\\_merge\\\_sorted\\\_lists.py
│   ├── 25\\\_max\\\_min\\\_list.py
│   ├── 26\\\_sum\\\_of\\\_list.py
│   ├── 27\\\_rotate\\\_list.py
│   ├── 28\\\_set\\\_intersection.py
│   ├── 29\\\_armstrong\\\_number.py
│   └── 30\\\_decimal\\\_to\\\_binary.py
├── test\\\_cases/                 # One corresponding test\\\_<program>.py per program
├── .gitignore
├── pytest.ini
├── requirements.txt
└── README.md
```

## Local setup and tests

```sh
git clone https://github.com/sakshu172007/First\\\_CI\\\_Pipeline.git
cd First\\\_CI\\\_Pipeline
python -m venv .venv
```

Activate on PowerShell with `.venv\\\\Scripts\\\\Activate.ps1`, on Windows Command
Prompt with `.venv\\\\Scripts\\\\activate`, or on Linux/macOS with
`source .venv/bin/activate`.

```sh
python -m pip install -r requirements.txt
python -m pytest -v
python -m pytest -v test\\\_cases/test\\\_21\\\_largest\\\_word.py
```

`pytest.ini` adds `codes` to the import path and discovers tests in `test\\\_cases`.
Tests use `importlib.import\\\_module()` because program filenames begin with digits.
The local `.venv`, Python bytecode, and pytest cache are ignored by Git.

## CI pipeline

The `Python CI` workflow runs on pushes to `main` and pull requests targeting
`main`. A fresh `ubuntu-latest` runner checks out the repository, installs Python
3.12, installs `requirements.txt`, and runs pytest. A failed test fails the job;
all passing tests produce a green success status in the Actions tab.

Program 21 and the initial configuration are pushed first. The workflow is added
in a separate commit. Programs 22–30 are then tested, committed, and pushed one
at a time, waiting for GitHub to confirm success before starting the next program.
Assignment 4: Python CI pipeline with GitHub Actions and pytest

