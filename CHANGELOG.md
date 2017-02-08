### 0.3.0
* Changed the supported file extension from "orbinp" to "tespin" for input files.
* Added support for files with extension "tespvar", which can be provided to MATLAB's TESP package to quickly generate a set of "orbinp" files.

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
