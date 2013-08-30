Flat text file with explanations for error messages

I've found that most ncverilog messages are both obscure and ungoogle-able. Hopefully, writing these down will help.

*E,BADDCL: identify declaration while expecting a statement -- declaration occurs where it shouldn't, e.g., you have a declaration in a task that isn't at the top

*E,SVNIMP: SystemVerilog construct not yet implemented:  nested program -- I'm unsure what that mean by nested, since this error occurs even when you try to write a program block inside a module. This error message seems to be the one given any time write a program block where you shouldn't.