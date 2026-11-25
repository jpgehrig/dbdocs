Use the `chactl import model` command to import Oracle Cluster Health Advisor models.

### Syntax

    chactl import model -name model_name -file model_file [-force] [-help]

While importing, if there is an existing model with the same name as the model being imported, then use the `-force` option to overwrite.

Example D-1 Example

    $ chactl import model -name weekday -file /tmp//weekday.mod

**Parent topic:** [chactl Command Reference](chactl-command-reference.md)
