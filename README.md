# CS-GY 6533 A – Interactive Computer Graphics - Fall 2021

### Course Instructors
*Cláudio Silva (instructor)*

370 Jay Street, room 1153 

[csilva@nyu.edu](mailto:csilva@nyu.edu)

Office hours: Friday, 10a-12pm

### Lectures:
Thursdays, 2:00pm - 4:30pm
Rogers Hall, Rm 325

## Course Description

This course provides an introduction to the field of Computer Graphics. We will cover the basic mathematical concepts, such as 2D and 3D transformations, study the interaction of light with geometry to derive shading models, the representation of geometric data in the memory, and implement iterative rendering algorithms. We will investigate how these fundamental components are integrated into current graphics processors (GPUs) and study the corresponding programming APIs (OpenGL and GLM). This course will also include a brief introduction to C++. 

Students will experiment with modern graphics programming and build small demos in C++ and OpenGL. 

By the end of the course, the student must be able to: 

Explain and apply the fundamental mathematical concepts used in image synthesis algorithms 

* Implement a basic real-time rendering pipeline based on rasterization 
* Implement visual effects such as shadows and reflections on rasterization pipelines 
* Be able to model scenes using triangulated models 
* Develop simple graphics programs in C++ using OpenGL and GLSL 

## Readings 

*Textbook*:
Fundamentals of Computer Graphics, 4th Edition
December 18, 2015 by A K Peters/CRC Press
Textbook - 734 Pages - 541 Color
ISBN 9781482229394

Optional and recommended texts are:  
* OpenGL Programming Guide 9th Ed. (8th Ed. can also be used), Addison Wesley 
* Real Time Rendering 4th Ed., CRC Press 

## Grading 

This class will not have any written exams. All the grading will be based on assignments, quizzes, and class participation. We will check all assignments for plagiarism, and strictly enforce university rules. See the class syllabus for more info.

## Class Discord
To sign up click [here](https://discord.gg/PDK8DhE7P9).

### Acknowledgement: 
This course is based on the computer graphics course designed by Professor Daniele Panozzo (NYU). Jonathas Costa (formely of NYU VIDA Lab) was instrumental in shaping the offerings in 2019 and 2020. 

## Assignments

* [General Guidelines](General_Rules/General_Rules.pdf) [(latex)](General_Rules/General_Rules.tex)

* [Assignment 1: Images, Morphological Operators](Assignment_1/requirements/Assignment-1_Images.pdf) [(latex)](Assignment_1/requirements/Assignment-1_Images.tex)

* [Assignment 2: 2D Vector Graphics Editor](Assignment_2/requirements/Assignment-2_2D_Editor.pdf) [(latex)](Assignment_2/requirements/Assignment-2_2D_Editor.tex)

* [Assignment 3: 3D Scene Editor](Assignment_3/requirements/Assignment3_3D.pdf) [(latex)](Assignment_3/requirements/Assignment3_3D.tex)

* [Assignment 4: Shadows, Reflections, and Depth Maps](Assignment_4/requirements/Assignment4.pdf) [(latex)](Assignment_4/requirements/Assignment4.tex)

# Compilation Instructions

```bash
git clone --recursive https://github.com/nyu-cs-gy-6533-fall-2020/base # --recursive flag is necessary for dependencies
cd Assignment_N
mkdir build
cd build
cmake ../ # re-run cmake when you add/delete source files
make
```
You can substitute `cmake ../` with the following to make the program **run faster** (optimized code generation)
```bash
cmake -DCMAKE_BUILD_TYPE=Release ../ # use this cmake command instead of the previous linefor faster run
```

If you are looking for an IDE, I suggest to use [VSCode](https://code.visualstudio.com) or [CLion](https://www.jetbrains.com/clion/).
