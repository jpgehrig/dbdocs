# Description of the illustration lnpls009.eps

This figure shows the outline of an anonymous block that contains another anonymous block. The inner block has an `IF-ELSIF-ELSE` statement that raises either exception A, B, or C, and an exception-handling part with an exception handler for A. The outer block has, immediately after the inner block, an exception-handling part with an exception handler for B.

Two arrows show the flow of control. The first arrow points from the `RAISE A` statement in the inner block to the exception-handling part of the inner block. The second arrow points from the end of the exception handler for A to the next statement of the outer block (where the exception-handling part of the outer block begins).
