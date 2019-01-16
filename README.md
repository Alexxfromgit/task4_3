# task4_3

**Task 4.3 - Simple back-up**

Job condition:

    Create a bash script task4_3.sh, which creates backups of a given directory. This script should:
    • Take 2 command line arguments:
        a. Absolute path to the directory with which you want to create backup
        b. Number of backups to save
    • Backups should be saved in the /tmp/backups/ 
    • When a specified number of backups is reached, the script deletes the oldest backups
      (i.e., no more than n backups of the specified directory should be located in the backups directory)
    • The backup files should be packed with tar and compressed with gzip.
    • The name of the archive file must be in the format <dir name>*.tar.gz
    By “*” is meant any information convenient to you, according to which you can then sort the backup files.
    This can be for example numbering (1,2,3, etc.) or time in any format you like (for example, 2018-03-21-145536).
    • An example of running the script: “./task4_3.sh /etc/default 3”, results in:
        a. Creating the file /tmp/backups/etc-default.tar.gz,
           in which the contents of the directory /etc/default are archived
           (i.e., “/” in the directory path should be replaced with “-”
           and the root directory in the path should be discarded)
        b. The backup directory contains no more than 3 archives (files)
           /tmp/backups/etc-default*.tar.gz.
        
Additional requirements:

    1. Each time the script is run, either a backup should be created or an error message should be displayed.
    2. In the script, it is necessary to provide for checking that the correct number of arguments
       is passed on the command line, and also that the directory with which you want to create a backup exists.
       If problems are detected, the script should display a message in stderr and end with a non-zero return code.
    3. Archive name template for rotation: <archived dirname with dashes>*.tar.gz
    4. Bash scripts with completed tasks must be uploaded to the githab repository with the name ‘task4_3’
    5. The githab repository ‘task4_3’ should contain one script task4_3.sh

Check results:

    • For each launch, a separate VM will be used (OS ubuntu xenial 16.04 server, image).
      Those. Consider that nobody has configured anything before you.
      The script will be launched from under the superuser (root). VM has access to the Internet.
    • The VM will have a repository with a task (for example, https://github.com/user/task4_3),
      if the repository has a different name, then the task will be automatically marked as unfulfilled.
    • The script ‘task4_3.sh’ from the root folder of the repository will be automatically launched
      (if the script is called differently or is in a subfolder, it will not be launched, respectively,
      the task will be automatically marked as not executed)
    • The script will run with different sets of parameters and should correctly handle the following situations:
        ◦ Not all parameters were passed.
        ◦ More than 2 parameters were passed.
        ◦ The folder or file you want to create backup does not exist.
        ◦ The parameter responsible for the number of backups to be stored is not correct.
        ◦ If the folder where the backup will be stored does not exist, you must create it.
        ◦ The path to the folder passed to the script as a parameter may contain spaces and special characters.
    • All error messages should be displayed in stderr. If the message is sent to stdout,
      it will not be caught by the check, and as a result, the script will be considered
      not to meet the specified criteria.
    • The name of the backup must strictly correspond to the given mask case-sensitive
      (if transferred to /etc/default, then the name of the archive file must begin with etc-default and end with .tar.gz).
    • It is assumed that both parameters passed to the script are interconnected:
      i.e. The number of backups for storage applies only to the backup of the transferred folder,
      and not to all the backups in /tmp/backup.
    • If you decide to use numbering in file names (etc-default.1.tar.gz, etc-default.2.tar.gz, etc.)
      then you should implement the generally accepted hierarchy of archives: 
      the “freshest” should have the name etc- default.tar.gz, previous - etc-default.1.tar.gz,
      created 2 starts ago - etc-default.2.tar.gz, etc.
