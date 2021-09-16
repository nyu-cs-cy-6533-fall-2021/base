# CS-GY 6533 A – Interactive Computer Graphics - Fall 2021

# General Rules

## Plagiarism note and late submissions

Copying code (either from other students or from external sources) is strictly prohibited! We will be using automatic anti-plagiarism tools, and any violation of this rule will lead to expulsion from the class. Late submissions will be penalized. See the syllabus for more information about late submissions. In case of severe illness or emergency, please notify the assistants and provide a relevant medical certificate.

## Provided Software

For this class, you will use the minimal framework available at the class github account. It compiles on Windows, Linux, and Mac OS X. Make sure to pull the more recent changes from the git repository as we might be updating the source code from time to time.

## Compiling the Sample Projects

In order to compile the provided project files for a given assignment on your machine, you need to do the following:

* Install CMAKE

* Clone the class repo with the --recursive option. NOTE: The recursive option is very important and it will not work without it.

* Create a directory called **build** in the assignment directory **TOPDIR/Assignment_X**, e.g. by typing in a terminal window:

```bash
cd TOPDIR/Assignment_X; mkdir build
```

* Create the necessary makefiles for compilation and place them inside the build directory, using the CMAKE GUI (windows), or the command line equivalent: 

```bash
cd build; cmake ../
```

* Compile and run the compiled executable by typing:

```bash
make; ./AssignmentX
```

If you run into problems, please contact us on Discord.

## What to Hand In

The delivery of the exercises is done using github classroom. The repository should follow the template provided, and it must contain:

* The source code, together with the necessary CMAKE project files, but excluding all compiled binaries/libraries. Specifically, do not include the build/ directory. The code must successfully compile on Linux operating system using GCC 9.3.0. Codes that don't successfully compile will receive a grade of 0%.

* A README.md file containing a description of what you've implemented and compilation
instructions, as well as explanations/comments on your results.

*  Screenshots of all your results with associated descriptions in the README file.

Note: It will generally not be necessary to use additional external software for your assignments. If you find that you need to use additional binaries / external libraries other than those provided by us, please first get approval by contacting us on Discord.

## Grading

The code will be evaluated on Linux. In order to receive a grade, your code **must** compile on Linux. If it does not compile on Linux, the exercise will receive a grade of 0%. 

Your submission will be graded according to the quality of your image results, and the correctness of the implemented algorithms. The submitted code must reproduce exactly the images included in your readme. 

To ensure fairness of your grade, you will be asked to briefly present your work to the teaching assistant. Each student will have 3-4 minutes to demo their submission and explain in some detail what has been implemented, report potential problems and how they tried to solve them, and point the assistants to the code locations where the various key points of the assignments have been implemented. If you cannot make it to the demo session (scheduled via Zoom), please schedule a separate meeting with the assistant in the week after the demo session.
