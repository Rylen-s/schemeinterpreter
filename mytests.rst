This file holds the tests that you create. Remember to import the python file(s)
you wish to test, along with any other modules you may need.
Run your tests with "python3 ok -t --suite SUITE_NAME --case CASE_NAME -v"
--------------------------------------------------------------------------------

Suite 1

    >>> from scheme_reader import *
    >>> from scheme import scheme_eval, create_global_frame  
   >>> from scheme_builtins import *
    >>> global_env = create_global_frame()

    Case Addition
        >>> expr = scheme_read(Buffer(tokenize_lines(['(+ 3 4)'])))
        >>> scheme_eval(expr, global_env)
        7

    Case LambdaApp
        >>> expr = scheme_read(Buffer(tokenize_lines(['((lambda (x) (* x x)) 5)'])))
        >>> scheme_eval(expr, global_env)
        25

    Case Variables
        >>> expr1 = scheme_read(Buffer(tokenize_lines(['(define a 10)'])))
        >>> scheme_eval(expr1, global_env)
        'a'
        >>> expr2 = scheme_read(Buffer(tokenize_lines(['(+ a 2)'])))
        >>> scheme_eval(expr2, global_env)
        12

    Case NestedExpr
        >>> expr = scheme_read(Buffer(tokenize_lines(['(+ 1 (* 2 3))'])))
        >>> scheme_eval(expr, global_env)
        7