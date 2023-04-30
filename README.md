Download Link: https://assignmentchef.com/product/solved-csce314-homework-4-problem-set
<br>
Keep the name and type of each function exactly the same as given in the problem statement and the skeleton code. Also, do not remove or modify the test list or the main function. If you remove or modify those, then you will be penalized for that.

This homework set is on Monadic Parsing, Chapter 13 of the Haskell textbook. Please, read the textbook sections 13.1–13.8 very carefully! Also, download the Parsing library (which is already included in the skeleton code of this homework), load it into GHCi and try out the examples in the textbook (and my lecture slides) for the basic parsers and derived primitives. This will help you understand the basic parsing functionalities such as the sequencing operation (&gt;&gt;=) for parsers and the choice operator (&lt;|&gt;) (Section 13.5). The choice parser p &lt;|&gt; q returns the result of the first parser p if p succeeds on the input; otherwise it returns the result of the second parser q applied to the same input.

<strong>Problem 1. </strong>Put your full name, UIN, and <em>acknowledgements of any help received </em>in the head comment in your .hs file for this assignment.

<strong>Problem 2.</strong> The parser for expressions discussed in section 13.8 (page 190) is of type expr :: Parser Int, term :: Parser Int and factor :: Parser Int. That is, the parsed result of an expression is an integer. For example, if the input string was

“2*(3+4)”, the parsed result (by parse expr “2*(3+4)”) would be [(14,””)] (note that the eval function given in the end of section 13.8 extracts the integer value 14 out of this singleton list). Your task is to explain the step-by-step working of the two example expressions below.

<ol>

 <li></li>

</ol>

&gt; parse expr “2*(3+4)”

results in

[(14,””)]

<ol start="2">

 <li></li>

</ol>

&gt; parse expr “1+2*3″

results in

[(7,””)]

Your explanation should be as specific as possible, strictly using the definitions of expr, term and factor given in section 13.8 (page 190) in the textbook.

<strong>Problem 3. </strong> Exercise 13.5 (Modified). Use the following type Expr.

data Expr = Val Int | Add Expr Expr | Mul Expr Expr deriving Show

Your task in this problem is to modify the parser for expressions to have type expr :: Parser Expr, term :: Parser Expr and factor :: Parser Expr. Thus, the parsed result will be an abstract syntax tree, for example, if you do

&gt; parse expr 2*(3+4)

it should output

[(Mul (Val 2) (Add (Val 3) (Val 4)),””)] and

&gt; parse expr “1+2*3″

should output

[(Add (Val 1) (Mul (Val 2) (Val 3)),””)]