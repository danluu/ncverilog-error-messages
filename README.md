Flat text file with explanations for error messages

I've found that most ncverilog messages are both obscure and ungoogle-able. Hopefully, writing these down will help.

*E,BADDCL: identify declaration while expecting a statement -- declaration occurs where it shouldn't, e.g., you have a declaration in a task that isn't at the top

ncsim: *E,MSSYSTF: User Defined system task or function registered during elaboration and used within the simulation has not been registered during simulation. -- this happens if the $function isn't defined. Any random typo will result in this error.

*E,SVNIMP: SystemVerilog construct not yet implemented:  nested program -- I'm unsure what that mean by nested, since this error occurs even when you try to write a program block inside a module. This error message seems to be the one given any time write a program block where you shouldn't.

X values in a multi-dimensional packed array: are you sure the array is large enough? If you index off the end, it is neither a compile time error nor a runtime error. It "works", but gives you Xs.