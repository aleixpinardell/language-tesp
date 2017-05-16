### 0.6.0
* Added support for defining the values of a parameter to be normally-distributed, through the use of `normrnd(mean,stddev)`. These parameters are not used as optimization variables; instead, their value is determine pseudo-randomly when the files for each optimization case are generated. The number of files to be generated per each optimization case is specified through the keyword `#POPULATION`. When the value of at least one variable is specified to be normally-distributed and the variable `INPUT_FILES_NAMING_PATTERN` is not specified, the input files are named from 1 to the number specified by `#POPULATION` with constant width, e.g. if the population is 100, then "001", "002", ... "100".

### 0.5.0
* Added support for settings specific to the DSST propagator.
* Added output options for the DSST propagator.
* Added support for outputting the propagation time, which, in contrast with the computation time, does not include the time required to set up the model, and only accounts for the time that was required for integrating the equations of motion from the initial to the final epoch.
* Added support for providing custom space weather files to be used by the NRLMSISE00 atmosphere model during propagation.
* Addition of the #ATTACH keyword in TESPVAR files to match the values of two or more variables one-to-one. For instance, the following code generates 4 TESPIN files (namely 0-200, 0-300, 5-200 and 5-300):
```
INITIAL_INCLINATION  [0 5]
INITIAL_PERIGEE_ALTITUDE  [200 300]
```
while the following code will only generate 2 TESPIN files (namely 0-200 and 5-300):
```
INITIAL_INCLINATION  [0 5]
INITIAL_PERIGEE_ALTITUDE  [200 300]
#ATTACH INITIAL_INCLINATION INITIAL_PERIGEE_ALTITUDE
```
* Support for user-defined variables to which a set of values for several parameters can be defined to each case. For instance, the following syntax is now valid:
```
  $propagatorSettings {
    'cowell' {
      PROPAGATOR_NAME  COWELL
      INTEGRATOR_NAME  RK78
      INTEGRATOR_ERROR_TOLERANCE  1.0e-9
      PRELOAD_CELESTIAL_BODIES_DATA  YES
    }
    'dsst' {
      PROPAGATOR_NAME  DSST
      INTEGRATOR_NAME  RK4
      INTEGRATOR_FIXED_STEPSIZE  '1 d'
      PRELOAD_CELESTIAL_BODIES_DATA  NO
    }
  }

  INPUT_FILES_DIRECTORY_TREE  sprintf('%s',$propagatorSettings)
```
In this example, all the files generated in the directory "cowell" will contain the first group of lines of code, while the files generated in the "dsst" directory will contain the four lines in the second group of code.

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
