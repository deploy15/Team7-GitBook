# 6.3.1  Dodgy Code

•          A dodgy code can be understood as a piece of code which has never been used or has no impact on the overall application execution.

•          After the automated investigation using FindBugs, it was found that there were 64 places in the code which had circular dependencies, unused declaration and initialization of variables and one of the places had the loading of Null value into a function.

•          The analysis is presented in the FindBugs report.

