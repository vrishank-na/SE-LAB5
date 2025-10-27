Lab 5: Reflection Answers

1. Which issues were the easiest to fix, and which were the hardest? Why?
The easiest fix was the unused import logging from Flake8, because I just had to delete one line of code. 

The hardest fix was the "bare except" in the removeItem function.as i had to replace the except: with two separate handlers (KeyError and Exception) to make the code safer without hiding all errors.


2. Did the static analysis tools report any false positives? If so, describe one example.
I did not find any obvious false positives. All the major issues reported by Bandit and Pylint  were real bugs or security risks that needed to be fixed.



3. How would you integrate static analysis tools into your actual software development workflow?

I'd run all three tools (Pylint, Bandit, Flake8) from my terminal before I commit my code. This would let me fix my own mistakes early.

 Second, I would set them up in a Continuous Integration (CI) workflow on GitHub. This way, the tools would automatically run for every new code push, preventing bad code from being merged.

4. What tangible improvements did you observe in the code quality, readability, or potential robustness after applying the fixes?

The code improved a lot. It is more secure because the dangerous eval function is gone. 

It is more robust because it won't crash if inventory.json is missing (thanks to the new loadData fix) or if removeItem is called on an item that doesn't exist. 

Finally, it's less buggy because the addItem function no longer shares a single log list.