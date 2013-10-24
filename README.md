# Ledger2html #

Ledger2html is a simple Ruby script that helps you obtain beautiful HTML5 reports
from [Ledger](http://ledger-cli.org/) output.

## Requirements

- Ledger 3.0
- Ruby 1.8.7 (Ruby 2.0.0 or later recommended)

## Synopsis ##

    Usage: ledger2html <options> <ledger options>
    Options:
        -h, --help                       Show this help message and exit.
        -o, --output  <path>             Save the report to a file.
            --pre                        Use <pre> instead of <table> to wrap Ledger's output.
            --style   <path>             Path to a CSS file (this option can be used multiple times).
            --title   <title>            Title of the report.
            --version                    Print ledger2html version and exit.
            --debug                      Enable debugging.

## Examples

A sample register report:

    ledger2html -f drewr3.dat reg groceries

<table>
<thead>
<tr>
<th scope="col" class="header-"></th>
<th scope="col" class="header-date">Date</th>
<th scope="col" class="header-payee">Payee</th>
<th scope="col" class="header-account">Account</th>
<th scope="col" class="header-amount">Amount</th>
<th scope="col" class="header-balance">Balance</th>
</tr>
</thead>
<tr class="first-posting"><td><input name="status" value="" type="checkbox"></td><td class="date">10-Dec-20</td><td class="payee">Organic Co-op</td><td class="account">Expenses:Food:Groceries</td><td class="amount">$ 37.50</td><td class="amount">$ 37.50</td></tr><tr><td></td><td></td><td></td><td class="account">Expenses:Food:Groceries</td><td class="amount">$ 37.50</td><td class="amount">$ 75.00</td></tr><tr><td></td><td></td><td></td><td class="account">Expenses:Food:Groceries</td><td class="amount">$ 37.50</td><td class="amount">$ 112.50</td></tr><tr><td></td><td></td><td></td><td class="account">Expenses:Food:Groceries</td><td class="amount">$ 37.50</td><td class="amount">$ 150.00</td></tr><tr><td></td><td></td><td></td><td class="account">Expenses:Food:Groceries</td><td class="amount">$ 37.50</td><td class="amount">$ 187.50</td></tr><tr><td></td><td></td><td></td><td class="account">Expenses:Food:Groceries</td><td class="amount">$ 37.50</td><td class="amount">$ 225.00</td></tr><tr class="first-posting pending"><td><input name="status" value="" type="checkbox"></td><td class="date">11-Jan-02</td><td class="payee">Grocery Store</td><td class="account">Expenses:Food:Groceries</td><td class="amount">$ 65.00</td><td class="amount">$ 290.00</td></tr><tr class="first-posting pending"><td><input name="status" value="" type="checkbox"></td><td class="date">11-Jan-19</td><td class="payee">Grocery Store</td><td class="account">Expenses:Food:Groceries</td><td class="amount">$ 44.00</td><td class="amount">$ 334.00</td></tr>
</table>


A sample cash flow report:

    ledger2html -f drewr3.dat bal --dc --related checking

<table>
<thead>
<tr>
<th scope="col" class="header-debit">Debit</th>
<th scope="col" class="header-credit">Credit</th>
<th scope="col" class="header-balance">Balance</th>
</tr>
</thead>
<tr><td class="amount">$ 300.00</td><td class="amount">$ 5,500.00</td><td class="amount partial">$ <span class="neg">-5,200.00</span></td><td class="account">Assets</td></tr><tr><td class="amount">0</td><td class="amount">$ 1,000.00</td><td class="amount partial">$ <span class="neg">-1,000.00</span></td><td class="account">Equity</td></tr><tr><td class="amount">$ 6,634.00</td><td class="amount">0</td><td class="amount partial">$ 6,634.00</td><td class="account">Expenses</td></tr><tr><td class="amount">0</td><td class="amount">$ 2,030.00</td><td class="amount partial">$ <span class="neg">-2,030.00</span></td><td class="account">Income</td></tr><tr><td class="amount">$ 200.00</td><td class="amount">0</td><td class="amount partial">$ 200.00</td><td class="account">Liabilities</td></tr><tr><td class="amount total">$ 7,134.00</td><td class="amount total">$ 8,530.00</td><td class="amount total">$ <span class="neg">-1,396.00</span></td><td></td></tr>
</tr>
</table>

