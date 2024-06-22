local_manifest

Local manifests used for building Android custom ROMs for oneplus 5t (dumpling)

To create and work with a local_manifest for building custom ROMs, follow these steps:
Step-by-Step Guide
1. Initialize the ROM's Manifest
First, initialize the ROM's manifest. This involves setting up the repository that contains the source code for the ROM.

bash
repo init -u <URL_TO_ROM_MANIFEST> -b <BRANCH_NAME>

2. Create the Local Manifests Directory
Navigate to the .repo directory and create a local_manifests folder if it doesn't already exist.

bash
cd .repo
mkdir local_manifests

3. Create the Local Manifest File
Create a new XML file within the local_manifests directory. You can name this file anything you like, but a common name is local_manifest.xml.

bash
nano local_manifests/local_manifest.xml

4. Define the Local Manifest
In the local_manifest.xml file, define the repositories you want to add, remove, or replace. Here is an example structure:

xml
<?xml version="1.0" encoding="UTF-8"?>
<manifest>
    <!-- Add a new remote repository -->
    <remote name="example" fetch="https://example.com/repo" />

    <!-- Add a new project from the remote repository -->
    <project path="path/to/project" name="example/project" remote="example" revision="branch_name" />

    <!-- Remove an existing project -->
    <remove-project name="existing/project" />

    <!-- Replace an existing project with a new one -->
    <remove-project name="old/project" />
    <project path="path/to/project" name="new/project" remote="example" revision="branch_name" />
</manifest>

5. Sync the Repositories
After defining your local manifest, sync the repositories to download the necessary source code.

bash
repo sync --force-sync -j$(nproc --all)
