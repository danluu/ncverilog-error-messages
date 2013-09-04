Flat text file with explanations for error messages

I've found that most ncverilog messages are both obscure and ungoogle-able. Hopefully, writing these down will help.

*E,BADDCL: identify declaration while expecting a statement -- declaration occurs where it shouldn't, e.g., you have a declaration in a task that isn't at the top

ncsim: *E,MSSYSTF: User Defined system task or function registered during elaboration and used within the simulation has not been registered during simulation. -- this happens if the $function isn't defined. Any random typo will result in this error.

*E,SVNIMP: SystemVerilog construct not yet implemented:  nested program -- I'm unsure what that mean by nested, since this error occurs even when you try to write a program block inside a module. This error message seems to be the one given any time write a program block where you shouldn't.

ncvlog: *E,NOTSTT: expecting a statement [9(IEEE)] -- there are many reasons this can happen. If you get a ridiculously large number of these, it could be because you left off an 'end'. The first one has the location of the error.

ncelab: *E,DLCSMD: Dependent checksum verilog_package worklib.sq:svh (VST) doesn't match with the checksum that's in the header of: module worklib.foo:v (VST).
ncverilog: *E,ELBERR: Error during elaboration (status 1), exiting. -- ncelab's caching doesn't seem to be coherent. This commonly pops up if you use git and checkout different branches. Sometimes, checking out a different branch and the checking the original branch back out fixes it. Sometimes, not. A common problem is that you don't include something you should, but it's cached in some strage way that causes the build to incorrectly work. If you wipe out your INCA_libs directory and try again, the build will fail. So, the real error is that something wasn't included correctly, which will often fail as follows, once you wipe out INCA_libs:

ncelab: *E,CUVMUR (../rtl/foo,314|618): instance 'foo.bar@foo<module>.baz[0].@qux<module>.quux' of design unit 'baz' is unresolved in 'worklib.foo:sv'


Non-errors that cause problems:

X values in a multi-dimensional packed array: are you sure the array is large enough? If you index off the end, it is neither a compile time error nor a runtime error. It "works", but gives you Xs.

Connecting 'logic' to an enum. If you have something that should be an enum and change just the port type on the module to input logic, it still works! Well, for some definition of works. There's no warning or error.