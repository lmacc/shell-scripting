# shell-scripting
# shell-scripting
Assignment 1.
Write an interactive script that allows a user to copy an existing file from an existing directory to another named new directory. The script should ask the user for:
● the name of a source directory from which to copy a file,
● the name of the file to copy, and
● the name of a destination directory to create and into which to place the copied file.
The script should report errors (and abort the program) where:
1. no source directory name is given;
2. no source file name is given;
3. no destination directory name is given;
4. the source directory name given does not name an existing directory;
5. the source file name given does not name an existing file;
6. the destination directory name given names an already existing directory;
7. the attempt to create the new directory fails;
8. the attempt to copy the file fails.


Pseudocode for assignment 1:
1. Get name of source directory.
2. Check if name of source directory is blank
3. If so exit with error message.
4. Check that source directory exists.
5. If not then exit with error.
6. Get name of source file.
7. Check if name of source file is blank
8. If so exit with error message.
9. Check that source file exists.
10. If not then exit with error.
11. Get name for destination directory.
12. Check if name of destination directory is blank.
13. If so exit with error message.
14. Check if name given for destination directory names an existing directory.
15. If so exit with error message.
16. Try to create the destination directory
17. If fail send error message and exit.
18. Try to copy source file from source directory to destination directory.
19. If fail send error message and exit.
20. If successful send confirmation message.

Assignment 2.

Assignment
Write a non-interactive script that allows to copy all of the ordinary files from an
existing directory to another named new directory. The script should expect the user to
supply arguments on the command line giving:
● the name of a source directory from which to copy the ordinary files,
● the name of a new destination directory to create and into which to place the
copied files.
The script should report errors where:
1. the number of arguments given is below 2 (fatal error);
2. the source directory name given does not name an existing directory (fatal
error);
3. the destination directory name given names an already existing directory
(fatal error);
4. the destination directory name given names an already existing file (fatal
error);
5. the attempt to create the new directory fails (fatal error);
6. the attempt to copy any of the files fails (warning errors).

Examples
Here’s how some example runs would look (assume the program is called 'ass2' and user
input in bold):
A successful run would look something like this (user input in bold):
ass2 source destdir
ass2: All ordinary files from directory source have been copied to destdir.
An unsuccessful run would look something like this (user input in bold):
ass2
ass2: ERROR: Incorrect number of arguments supplied.
ass2: USAGE: ass2 <source directory> <new destination directory>
Another unsuccessful run would look something like this (user input in bold):
ass2 source
ass2: ERROR: Incorrect number of arguments supplied.
ass2: USAGE: ass2 <source directory> <new destination directory>
Another unsuccessful run would look something like this (user input in bold):
ass2 sourceNotThere destdir
ass2: ERROR: Source directory SourceNotThere does not exist.
ass2: USAGE: ass2 <source directory> <new destination directory>
A partly unsuccessful run would look something like this (user input in bold):
ass2 source destdir
ass2: WARNING: File somefile could not be copied to destdir.
ass2: WARNING: File someotherfile could not be copied to destdir.
ass2: Some ordinary files from directory source have been copied to destdir.

Notes:
Errors should be echoed to the standard error channel and adhere to the standard syntax
as before. For example:
echo "${0}: ERROR: Destination directory already exists." 1>&2
echo "${0}: USAGE: ${0} <source directory> <new destination directory>" 1>&2
exit 4 #if required
Which, in an example run would display on the error channel as:
ass2: ERROR: Destination directory already exists.
ass2: USAGE: ass2 <source directory> <new destination directory>
All your exits for errors should be given a unique exit status number 1-255.

Pseudocode for assignment 2:
1. Check number of arguments given.
2. Exit with error message if incorrect.
3. Check that source directory exists.
4. If not then exit with error.
5. Check if name given for destination directory names an existing directory.
6. If so exit with error message.
7. Check if name given for destination directory names an existing file.
8. If so exit with error message.
9. Try to create the destination directory.
10. If fail send error message and exit.
11.Initialise variables for number of copied files and number of failed copies.
12. Enter loop to copy all ordinary files from source directory to destination directory.
a) Try to copy the next file
b) If this copy fails send warning message, record extra fail, and continue.
c) Otherwise record extra copied file and continue.
13.If completely successful send confirmation message and exit.
14.Otherwise, if partial fail send partial confirmation and exit.
15.Otherwise if no files copied send information message and exit.





