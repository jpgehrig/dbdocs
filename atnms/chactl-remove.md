Use the `chactl remove model` command to delete an Oracle Cluster Health Advisor model along with the calibration data and metadata of the model from the Oracle Cluster Health Advisor repository.

**Note:**

If the model is being used to monitor the targets, then the `chactl remove model` command cannot delete any model.

### Syntax

    chactl remove model -name model_name [-help]

### Error Message

Error: `model_name`` does not exist`

Description: The specified Oracle Cluster Health Advisor model does not exist in the Oracle Cluster Health Advisor repository.

**Parent topic:** [chactl Command Reference](chactl-command-reference.md)
