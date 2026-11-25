## patch Commands

Use commands with the `patch` keyword to apply or rollback one-off patches to the specified working copy using the in-place patching method.

- rhpctl evaluate patch
  Evaluates the specified home or gold image to get the health status and patch recommendations.

**Parent topic:** [RHPCTL Command Reference](rhpctl-command-reference.md)

### rhpctl evaluate patch

Evaluates the specified home or gold image to get the health status and patch recommendations.

#### Syntax

    rhpctl evaluate patch {-image image_name | -path oracle_home_path}
    [-applyfrequency <MONTHLY|QUARTERLY|HALF_YEARLY|ANNUALLY>] [-updatelag LATEST | LATEST-1 | LATEST-2]
    [-additionalbuglist bug_list] [-generateimage -importtoimage target_image_name]

Table A-45 rhpctl evaluate patch Command Parameters

| Parameter                                           | Description                                                                                                                                                                                                                                                                                                                                                   |
|:----------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-image ``image_name`                               | Specify the name of a deployed working copy that you want to evaluate.<br>Note: This option is available only for Oracle FPP Server Mode.                                                                                                                                                                                                                     |
| `-path ``oracle_home_path`                          | Specify the absolute path for evaluating the Oracle home.                                                                                                                                                                                                                                                                                                     |
| `-updatelag ``update_lag`                           | Specify the update lag policy for your image or Oracle home.<br>• LATEST: most recently released RU (default)<br>• LATEST-1: 1 RU before the most recent RU<br>• LATEST-2: 2 RUs before the most recent RU<br>The default value is LATEST.                                                                                                                    |
| `-applyfrequency ``apply_frequency`                 | Specify how often you patch your working copy or Oracle home.<br>• MONTHLY: update software every month.<br>• QUARTERLY: update software every 3 months (Oracle recommended - default).<br>• HALF_YEARLY: update software every 6 months.<br>• ANNUALLY: update software every 12 months.<br>The default and Oracle recommended patch frequency is QUARTERLY. |
| `-additionalbuglist ``bug_list`                     | Comma-separated list of additional bugs that you want to apply along with the Oracle Update Advisor recommended patches.                                                                                                                                                                                                                                      |
| `-generateimage -importtoimage ``target_image_name` | Specify this parameter to generate a patched image and import the patched image to the specified gold image.<br>Note: This option is available only for Oracle FPP Local Mode.                                                                                                                                                                                |

#### Examples

To evaluate an Oracle Grid Infrastructure home:

    $ rhpctl evaluate patch -image DB1926000 -generateimage -importtoimage DB192800
    Operation "rhpctl evaluate patch" scheduled with the job ID "53".

**Parent topic:** patch Commands
