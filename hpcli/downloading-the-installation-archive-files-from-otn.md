Download installation archive files from Oracle Technology Network (OTN).

1.  Use any browser to access the software download page from Oracle Technology Network:
    <http://www.oracle.com/technetwork/indexes/downloads/index.html>
2.  Go to the download page for the product to install.
3.  On the download page, identify the required disk space by adding the file sizes for each required file.
    The file sizes are listed next to the file names.
4.  Select a file system with enough free space to store and expand the archive files.
    In most cases, the available disk space must be at least twice the size of all of the archive files.
5.  On the file system, create a parent directory for each product (for example, `OraDB19c`) to hold the installation directories.
6.  Download all of the installation archive files to the directory you created for the product.
    **Note:**

    For Oracle Database Client installations, there are two installation archive files available for download. The first file is the client installation binary and the second file is a client gold image file. Download the appropriate zip file based on the type of installation you want to perform.
7.  Verify that the files you downloaded are the same size as the corresponding files on Oracle Technology Network. Also verify the checksums are the same as noted on Oracle Technology Network using a command similar to the following, where filename is the name of the file you downloaded:
        cksum filename.zip
8.  Extract the files in each directory that you just created.

**Parent topic:** [Accessing the Installation Software](accessing-the-installation-software.md)
