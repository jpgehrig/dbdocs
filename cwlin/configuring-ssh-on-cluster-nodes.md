## Configuring SSH on Cluster Nodes

You must configure SSH separately for each Oracle software installation owner that you intend to use for installation.

To configure SSH, you must first create RSA or DSA keys on each cluster node, and then copy all the keys generated on all cluster node members into an authorized keys file that is identical on each node. Note that the SSH files must be readable only by `root` and by the software installation user (`oracle`, `grid`), as SSH ignores a private key file if it is accessible by others. In the examples that follow, the DSA key is used.

To configure SSH, complete the following:

- [Create SSH Directory and Create SSH Keys On Each Node](create-ssh-directory-and-create-ssh-keys-on-each-node.md)
  To configure SSH, you must first create RSA or DSA keys on each cluster node.
- [Add All Keys to a Common authorized_keys File](add-all-keys-to-a-common-authorized_keys-file.md)
  To configure SSH, copy all the generated keys on all cluster node members into an authorized keys file that is identical on each node.

**Parent topic:** [Configuring SSH Manually on All Cluster Nodes](configuring-ssh-manually-on-all-cluster-nodes.md)
