<style>
/* Style copi… inspired by http://coding.smashingmagazine.com/2008/08/13/top-10-css-table-designs/ */
::selection {
  background: rgb(51,51,153);
  color: rgb(252,252,252);
}
body {
  width: 95%;
  margin-top: 4em;
  margin-bottom: 6em;
  font-family: 'Lucida Grande', 'Helvetica Neue', sans-serif;
  font-size: 12px;
  font-style: normal;
  font-weight: normal;
  text-align: left;
  vertical-align: baseline;
  color: rgb(51,51,153);
  background-color: rgb(252,252,252);
}
figure {
  width: 100%;
  margin: 0px;
  padding: 0px;
}
h1, h2, h3, h4, h5, h6 {
  text-align: center;
}
pre {
  font-family: Menlo, Monaco, Courier, monospace;
	color: rgb(102,102,153);
}
table {
  display: table;
  line-height: 22px;
  width:90%;
  margin: auto;
  -webkit-border-horizontal-spacing: 0px;
  -webkit-border-vertical-spacing: 0px;
}
thead {
  display: table-header-group;
  height: 43px;
  line-height: 22px;
  margin: 0px;
  padding: 0px;
  color: rgb(51,51,153);
  background-color: rgba(0,0,0,0);
  outline-color: rgb(51,51,51);
  outline-style: none;
  outline-width: 0px;
}
th {
  display: table-cell;
  font-size: 14px;
  margin: 0px;
  padding: 10px 8px;
  font-weight: normal;
  color: rgb(51,51,153);
	border-bottom: 2px solid rgb(102,120,177);
  border-collapse: collapse;
}
tr {
  display: table-row;
  margin: 0px;
  padding: 0px;
}
tr:nth-child(even) {
 /* background-color: rgb(250, 250, 255);*/
}
tr:hover td {
  color: rgb(0,0,153);
  background-color: rgb(242,243,255);
}
td {
  display: table-cell;
  vertical-align: top;
	padding: 5px 8px;
	color: rgb(102,102,153);
}
.first-posting td {
  border-top: 1px dotted rgb(182,190,216);
  border-collapse: collapse;
}
tr:first-child > td {
  border: none;
}
td.amount {
  white-space: pre;
  text-align: right;
  vertical-align: top;
}
/*svg {
  width: 100%;
}*/
#monthly-expenses .first-period td,
#monthly-expenses-related .first-period td {
	border-top: 2px solid rgb(102,120,177);
  border-collapse: collapse;
}
#monthly-expenses th, #monthly-expenses-related th {
  border-bottom: none;
}
#cash-flow-balance th {
  border-bottom: none;
}
div#monthly-net-worth,
div#weekly-net-worth {
  width:30%;
  margin:auto;
  float:right;
}
.account {
}
.amount {
  font-family: Menlo, Monaco, Courier, monospace;
}
.balance-report table {
  line-height: 16px;
}
.balance-report td {
  vertical-align: top;
  padding-top: 5px;
  padding-bottom: 5px;
	padding-left: 8px;
  padding-right: 8px;
}
.balance-report .account,
.budget-report .account {
  white-space: pre;
}
.balance-report td.amount {
  width: 25%;
  min-width: 130px;
}
.date {
  min-width: 100px;
}
.balance-report td.total,
.budget-report td.total {
  padding-top: 10px;
	border-top: 2px solid rgb(102,120,177);
}
.date {
}
.future {
  font-style: italic;
}
.header-amount, .header-average, .header-balance,
.header-debit, .header-credit, .header-deviation,
.header-net-worth, .header-total,
.header-actual, .header-budgeted,
.header-remaining, .header-used,
.header-cleared, .header-pending {
  text-align: right;
}
.improper {
  color: rgb(153,26,0);
  font-weight: bold;
}
.ledger-command {
  display: none;
}
.neg {
  color: rgb(153,26,0);
}
.payee {
}
.pending .payee {
  color: rgb(153,77,0);
  font-weight: bold;
}
.perc {
  text-align: right;
}
.total {
  font-weight: bold;
}    
</style>

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

