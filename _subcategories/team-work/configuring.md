# Configuring


## Share certain files of the .idea folder

We don't need:

COPY AND CHECK MY GIT-IGNORE AND SEBASTIANO POST ABOUT

- assetWizardSettings.xml: It stores the last icon added with the Android Studio Wizard. It could be safely removed from VCS.
- caches: For obvious reasons.
- gradle.xml: contains path to your gradle version. Not necessary.
- libraries: This directory contains file which indicates where the jar files of your libraries are stored. As the download path may be user specific, you should not keep this directory in your VCS.
- modules.xml: This file contains the path to your modules .iml file. Same as gradle.xml file, it should not be kept in git.

- workspace.xml: This file contains information about your workspace on Android Studio, such as the last position of the cursor on a file you opened, … So it is definitely user specific information which should absolutely not be kept in git.

So the files we don't need, can be added to .gitignore
MAKE THE LIST

What could be useful:

- codeStyles:??? This folder contains the code style settings of the project. It may be useful to keep it if you change the default value.????

- dictionaries:??? This folder contains the entry you have added to dictionary. This has to do with inspection of the code, and this dictionary may be important if you have strict rules in your continuous integration system.

- inspectionProfiles: This folder contains your specific Lint rules for the project. Same as for dictionary folder, it should be kept in git.

- misc.xml: It contains information about the project, such as Java version, project type, and some others.

- navEditor.xml: This file stores the position of your elements in the Navigation Editor. If keeping this information is relevant for your project, you should keep this file. Otherwise, feel free to add it to .gitignore file in order to avoid conflicts with it.

- runConfigurations.xml
As it name may let you guess, this file stores the configurations you may add by clicking Edit Configurations. You definitively should keep this file in VCS.

- vcs.xml: This file contains informations about VCS you use in your project, to allow you using the GUI to perform versioning operations. You definitively should keep it in your project


Those information are about the project, and are not user specific. So it should be kept in git.
