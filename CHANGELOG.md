##### 0.4.1
* Version renaming.

### 0.4.0
* Version renaming.

### 0.3.0
* Dropped support for providing strings using double quotes. Only single quotes are supported now.
* Added support for providing the initial epoch using the date format 'YYYY-MM-DD hh:mm:ss'. Moreover, when not using a formatted date, now the epoch has to be provided in seconds (since J2000) rather than in years, in order to avoid inconsistencies about the definition of year (Julian year, sidereal year, etc).
* Changed the supported file extension from "orbinp" to "tespin" for input files, although "orbinp" files are still recognized temporarily until the next major or minor release.
* Added support for files with extension "tespvar", which can be provided to TESP's MATLAB package to quickly generate a set of "orbinp" files.
* Added support for single-quoted strings. Now, both 'this' and "this" are valid strings. By default, single-quotes are provided in by the snippets, as "tespvar" files include some MATLAB code and MATLAB only supports single-quoted strings.
* Changed the "help" snippet prefix to "list".
* Added an "example" snippet for "tespvar" files.

##### 0.2.3
* Removed support for "orbout" files. These files should not be modified by the user and will generally be read and processed by other programs rather than manually. Moreover, even when support was provided, the TESP grammar was not loaded by Atom when the file was very large, i.e. when it contained a large results matrix.

##### 0.2.2
* Added a comment to the help-snippet indicating which version of TESP the installed language package supports.
* Fixed some minor bugs in the help-snippet:
  * The backslash in the regular expression for `SEARCH_OUTPUT_FILENAME_PATTERN` was not being properly escaped.
  * After using the snippet, the cursor is now placed at the beginning of the document, right after the commented header lines, rather than at the end of the document.

##### 0.2.1
* Fixed version-naming error in the CHANGELOG.md file.

### 0.2.0
* Fixed wrong default value in `INTEGRATOR_ERROR_TOLERANCE` snippet.
* Added missing explanations for `OUTPUT_DIRECTORY_PATH` and `OUTPUT_FILE_NAME` snippets.
* Added a snippet (accessible by typing `help`) to print a list with all the variables and default values.
* Added a CHANGELOG.md file.

### 0.1.0
* Initial release with support for 58 variables.
