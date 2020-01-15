# Adding a code coverage target to your MakeFile

Put this in your MakeFile:

```
coverage:
	g++ -o a.out -std=c++11 -Wall -g --coverage main.cpp
	test # make target to run your tests
	gcov --intermediate-format main.cpp
```