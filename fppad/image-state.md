## Image State

Am image state is a way to restrict provisioning of an image for users with specified roles.

You can set the state of an image to `TESTABLE` or `RESTRICTED` so that only users with the GH_IMG_TESTABLE or GH_IMG_RESTRICT roles can provision working copies from this image. Once the image has been tested or validated, you can change the state and make the image available for general use by running the `rhpctl promote image -image ``image_name`` -state PUBLISHED` command. The default image state is `PUBLISHED` when you add a new gold image, but you can optionally specify a different state with the `rhpctl add image` and `rhpctl import image` commands.

**Parent topic:** [Adding Gold Images to the Fleet Patching and Provisioning Server](adding-gold-images-to-oracle-fpp-server.md)
