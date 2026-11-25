## series Commands

Use commands with the `series` keyword to add, delete, subscribe, and manage a series.

- rhpctl add series
  Adds a series to the Fleet Patching and Provisioning Server configuration.
- rhpctl delete series
  Deletes a series from the Fleet Patching and Provisioning Server configuration.
- rhpctl deleteimage series
  Deletes an image from a series.
- rhpctl insertimage series
  Inserts an existing image into a series.
- rhpctl query series
  Displays the configuration of a series.
- rhpctl subscribe series
  Subscribes a specific user to an image series.
- rhpctl unsubscribe series
  Unsubscribes a user from an image series.

**Parent topic:** [RHPCTL Command Reference](rhpctl-command-reference.md)

### rhpctl add series

Adds a series to the Fleet Patching and Provisioning Server configuration.

#### Syntax

    rhpctl add series -series series_name [-image image_name]

#### Parameters

Table A-51 rhpctl add series Command Parameters

| Parameter               | Description                                                                                             |
|:------------------------|:--------------------------------------------------------------------------------------------------------|
| `-series ``series_name` | Specify a name for the series that you want to add.                                                     |
| `-image ``image_name`   | Optionally, you can specify the name of a configured image. This image becomes the first in the series. |

#### Example

To add a series:

    $ rhpctl add series –series DB12_series

**Parent topic:** series Commands

### rhpctl delete series

Deletes a series from the Fleet Patching and Provisioning Server configuration.

#### Syntax

    rhpctl delete series -series series_name [-force]

#### Usage Notes

- Specify the name of the series that you want to delete.

- Use `-force` to delete an image series even if the series includes images.

- Before deleting an image series, you must first remove all images from the series by using the `rhpctl deleteimage series` command.

- This command does not delete images, only series.

#### Example

The following example deletes a series called PRODDBSERIES:

    $ rhpctl delete series -series PRODDBSERIES

**Parent topic:** series Commands

### rhpctl deleteimage series

Deletes an image from a series.

#### Syntax

    rhpctl deleteimage series -series series_name -image image_name

#### Parameters

Table A-52 rhpctl deleteimage series Command Parameters

| Parameter               | Description                                                            |
|:------------------------|:-----------------------------------------------------------------------|
| `-series ``series_name` | Specify the name of the series from which you want to delete an image. |
| `-image ``image_name`   | Specify the name of the image that you want to delete from a series.   |

#### Example

The following command deletes an image called PRODIMAGEV0 from a series called PRODDBSERIES:

    $ rhpctl deleteimage series -series PRODDBSERIES -image PRODIMAGEV0

**Parent topic:** series Commands

### rhpctl insertimage series

Inserts an existing image into a series.

**Note:**

A single image can belong to one or more series.

#### Syntax

    rhpctl insertimage series -series series_name -image image_name
       [-before image_name]

#### Parameters

Table A-53 rhpctl insertimage series Command Parameters

| Parameter             | Description                                                                                     |
|:----------------------|:------------------------------------------------------------------------------------------------|
| `-series series_name` | Specify the name of the series into which you want to insert an image.                          |
| `-image image_name`   | Specify the name of the image that you want to insert into a series.                            |
| `-before image_name`  | Optionally, you can specify the name of an image before which you want to insert the new image. |

#### Example

To insert an image into a series:

    rhpctl insertimage series -series DB12_series -image DB12102_PSU

**Parent topic:** series Commands

### rhpctl query series

Displays the configuration of a series.

#### Syntax

    rhpctl query series [-series series_name | -image image_name]

#### Parameters

Table A-54 rhpctl query series Command Parameters

| Parameter               | Description                                                                     |
|:------------------------|:--------------------------------------------------------------------------------|
| `-series ``series_name` | Specify the name of the series for which you want to display the configuration. |
| `-image ``image_name`   | Alternatively, you can specify the name of a configured image.                  |

#### Usage Notes

If you do not specify a series or an image by name, then CRSCTL returns information for all series.

#### Example

This command returns output similar to the following:

    $ rhpctl query series

    Image series: DB12_series
    Image series: GRID_series
    Image series: DB112_series

**Parent topic:** series Commands

### rhpctl subscribe series

Subscribes a specific user to an image series.

#### Syntax

    rhpctl subscribe series -series series_name [-user user_name [-client cluster_name]]

#### Parameters

Table A-55 rhpctl subscribe series Command Parameters

| Parameter                | Description                                                                                            |
|:-------------------------|:-------------------------------------------------------------------------------------------------------|
| `-series ``series_name`  | Specify the image series to which you want to subscribe a user.                                        |
| `-user ``user_name`      | Specify an operating system user to whom you are subscribing the image series.                         |
| `-client ``cluster_name` | Optionally, you can specify the name of the client cluster to which the operating system user belongs. |

**Parent topic:** series Commands

### rhpctl unsubscribe series

Unsubscribes a user from an image series.

#### Syntax

    rhpctl unsubscribe series -series series_name [-user user_name [-client cluster_name]]

#### Parameters

Table A-56 rhpctl unsubscribe series Command Parameters

| Parameter                | Description                                                                                            |
|:-------------------------|:-------------------------------------------------------------------------------------------------------|
| `-series ``series_name`  | Specify the image series from which you want to unsubscribe a user.                                    |
| `-user ``user_name`      | Specify an operating system user from whom you are unsubscribing the image series.                     |
| `-client ``cluster_name` | Optionally, you can specify the name of the client cluster to which the operating system user belongs. |

**Parent topic:** series Commands
