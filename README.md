# accounting-systems
Implementations of double-entry accounting systems

## Introduction
I gave a talk last fall to a business school faculty, advocating that they digitze their teaching methods and that their courses instruct students on how to digitize businesses. Part of such a curriculum would be a course similar to the Berkeley Data 8 course (see `data8.org`). That course teaches how to write simple Python programs that run in a Jupyter notebook and then how to use re-sampling statistics to make inferences on samples. For example, a student would be able to write a short program that determined a 95 percent confidence interval for the mean of a sample such as a survey of customer preferences.

Along the way, I claimed that a double-entry accounting system could be created in about 100 lines of code. Having students create such a system themselves would be make sure that they knew how double-entry accounting work and would provide a tool that they could use in not only their accounting courses but also in other courses where accounting is needed.

This repository provides two accounting systems of increasing complexity. Each defines an `Accounts` class, a `post` method to add a transaction to the system, a `ledgers` method that returns the T-accounts and their postings, and a `balances` method that returns the balances in each account. A typical accounting cycle is to create an `Accounts` instance, post transactions to that instance, then create and examine the ledgers. From the ledgers, the closing entries for an accounting period may be created and posted.

## The modules

The module `accounts1.py` defines an `Account` class which assumes that each account holds a positive or negative balance. What is traditionally called a debit balance is positive. A credit balance is negative. A new account is created just by posting to it. The `Accounts` class is less than 70 lines of Python.

The module `accounts2.py` defines an `Account` class in which the amount in a class is either a debit or credit amount, just like in traditional accounting text book. In addition, to help avoid having a misspelled name in a post method call create an unexpected account, all account names must be predefined. The `account` method does this. The file is less than 90 lines of Python.

## Possible extensions

The work can be extended in many ways. For example, both implementations are single currency. Adding multiple currencies is straight forward to do by changing the definition of the `Amount` class to allow a denomination and requiring that a transaction when posted balance across all the currencies. The denominations might be USD (which would be a good default in the United States), CAD (Canadian dollars), and so forth. Also, in some settings, allowing accounts demoninations like "IBM-shares" or would allow tracking of shares of stocks and other similar goods. Then the accounting system becomes a basic inventory tracking system.

Another extension would be to create an input-file format for using the program. At present, the user must write a Python program to instantiate the `Accounts` class and post to it. With an input-file, the user would create a file and run a program that read the file and produced the t-accounts and account balances. One approach to the design of the input file is illustrated by `ledger-cli.org` which defines a way to layout a file containing journal entries.

## Wrap up

This work provides implementations of simple accounting systems that students can program themselves. The implementations are short.
