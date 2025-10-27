# Lab 5: Static Analysis Issue Report

This table documents a minimum of four issues identified by Pylint, Bandit, and Flake8, along with the approach taken to fix them[cite: 32, 35].

| Issue | Tool(s) | Line(s) | Description | Fix Approach |
| :--- | :--- | :--- | :--- | :--- |
| Use of `eval` | Bandit | ~51 | `eval` is a high-severity security risk [cite: 27] as it can execute arbitrary code. | Replaced the dangerous `eval` call with a simple `print()` statement. |
| Mutable default arg | Pylint | ~7 | `logs=[]` is a mutable default argument[cite: 13, 69], causing all function calls to share the same list by default. | Changed the default value to `None` and added logic to initialize `logs = []` inside the function. |
| Bare `except` | Pylint / Bandit | ~18 | `except:` catches all possible errors[cite: 13, 75], hiding bugs and making the code hard to debug. | Replaced the bare `except:` with specific `except KeyError:` and a general `except Exception as e:` to log other errors. |
| Unused import | Flake8 | ~2 | `import logging` was imported but never used in the code[cite: 24], adding unnecessary clutter. | Deleted the entire `import logging` line. |
| `open` without `with` | Pylint | ~23, ~29 | Files were opened without the `with` statement, risking resource leaks if an error occurred before `f.close()` was called. | Refactored `loadData` and `saveData` to use the `with open(...) as f:` syntax for safer file handling. |
