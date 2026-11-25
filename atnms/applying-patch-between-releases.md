Use the list of commands to manage patches.

### Syntax

    orachk –applypatch orachk_bug_id.zip
    exachk –applypatch exachk_bug_id.zip

    orachk –querypatch all
    exachk –querypatch all
    orachk –querypatch bug_id
    exachk –querypatch bug_id

    orachk –rollbackpatch bug_id
    exachk –rollbackpatch bug_id

Table 2-6 Managing Patches

| Command          | Description                                                                                   |
|:-----------------|:----------------------------------------------------------------------------------------------|
| `–applypatch`    | Applies a new patch for the specified bug ID.                                                 |
| `–querypatch`    | Lists the details of all of the installed patches or for the specified bug ID.                |
| `–rollbackpatch` | Rolls back the applied patch to its previous state, the state at which the patch was applied. |

Example 2-17 -applypatch

    ./orachk -applypatch orachk_27836477.zip

    Patched file /scratch/test_user/lib/messages.pyc
    Patched file /scratch/test_user/lib/utils.pyc
    Patched file /scratch/test_user/lib/help.pyc
    Patched file /scratch/test_user/lib/watchdog.pyc
    Patched file /scratch/test_user/lib/constant.pyc
    Patched file /scratch/test_user/lib/execute_checks.pyc
    Patched file /scratch/test_user/lib/security.pyc
    Patched file /scratch/test_user/orachk.pyc
    Patching of file orachk_27836477.zip completed
    orachk Patched to 18.4.1(PATCH1) from 18.4.0(DEV)
    orachk Patch fixes 27836477

Example 2-18 -querypatch all

    ./orachk -querypatch all

    Patch: ORACHK_PATCH_18.4.1
    Status: INSTALLED
    Fixes: 27836477
    Applied on: Fri Oct 26 10:50:53 2018

Example 2-19 -querypatch bug_id

    ./orachk -querypatch 27836477

    Patch: ORACHK_PATCH_18.4.1
    Status: INSTALLED
    Fixes: 27836477
    Applied on: Fri Oct 26 10:50:53 2018

Example 2-20 –rollbackpatch

    ./orachk -rollbackpatch 27836477

    Rolled-back file /scratch/test_user/lib/security.pyc
    Rolled-back file /scratch/test_user/lib/execute_checks.pyc
    Rolled-back file /scratch/test_user/lib/utils.pyc
    Rolled-back file /scratch/test_user/lib/help.pyc
    Rolled-back file /scratch/test_user/lib/watchdog.pyc
    Rolled-back file /scratch/test_user/lib/constant.pyc
    Rolled-back file /scratch/test_user/lib/messages.pyc
    Rolled-back file /scratch/test_user/orachk.pyc
    orachk Rolled-back to 18.4.0(DEV) from 18.4.1(PATCH1)
    orachk Rolled-back fixes for 27836477

**Parent topic:** [Analyzing Risks and Complying with Best Practices](purpose-oracle-orachk-and-oracle-exachk.md)
