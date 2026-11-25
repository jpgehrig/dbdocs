Use the `chactl rename model` command to rename an Oracle Cluster Health Advisor model in the Oracle Cluster Health Advisor repository.

Assign a descriptive and unique name to the model. Oracle Cluster Health Advisor preserves all the links related to the renamed model.

### Syntax

    chactl rename model -from model_name -to model_name [-help]

### Error Messages

Error: `model_name`` does not exist`

Description: The specified model name does not exist in the Oracle Cluster Health Advisor repository.

Error: `dest_name`` already exist`

Description: The specified model name already exists in the Oracle Cluster Health Advisor repository.

**Parent topic:** [chactl Command Reference](chactl-command-reference.md)
