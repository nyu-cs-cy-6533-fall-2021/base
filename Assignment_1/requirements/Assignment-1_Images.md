\documentclass[11pt]{article}
\usepackage{geometry}                % See geometry.pdf to learn the layout options. There are lots.
\geometry{letterpaper}                   % ... or a4paper or a5paper or ... 
%\geometry{landscape}                % Activate for for rotated page geometry
%\usepackage[parfill]{parskip}    % Activate to begin paragraphs with an empty line rather than an indent
\usepackage{graphicx}
\usepackage{amssymb}
\usepackage{epstopdf}
\usepackage[usenames,dvipsnames]{color}
\usepackage{hyperref}
\usepackage{url}
\hypersetup{colorlinks=true}
%\DeclareGraphicsRule{.tif}{png}{.png}{`convert #1 `dirname #1`/`basename #1 .tif`.png}
\renewcommand\familydefault{\sfdefault}
\newcommand{\todo}[1]{{\bf\textcolor{red}{TODO: #1}}}
\setlength{\topmargin}{0cm}
\setlength{\headheight}{0cm}
\setlength{\headsep}{1cm}
\setlength{\textheight}{7.7in}
\setlength{\textwidth}{6.5in}
\setlength{\oddsidemargin}{0cm}
\setlength{\evensidemargin}{0cm}
\setlength{\parindent}{0.25cm}
\setlength{\parskip}{0.1cm}

\usepackage{fancyhdr,graphicx,lastpage}% http://ctan.org/pkg/{fancyhdr,graphicx,lastpage}
\fancypagestyle{plain}{
  \fancyhf{}% Clear header/footer
  \fancyhead[L]{CS-GY 6533 A – Interactive Computer Graphics}% Right header
  \fancyhead[R]{\includegraphics[height=20pt]{tandon_long_black.png}}% Right header
  \fancyfoot[L]{Claudio Silva and Jonathas Costa}% Left footer
  \fancyfoot[R]{\thepage}% Right footer
}
\pagestyle{plain}% Set page style to plain.

\graphicspath{{figures/}{figures_lowres/}{pictures/}}

\begin{document}

\hspace{50pt}

\begin{center}

{\Huge \textbf{Assignment 1: Images}}\\
\vspace{10pt}
Handout date: 09/09/2020\\
Submission deadline: 09/23/2020, 11:59PM EST\\
Demo date: TBA, via Zoom appointments
\end{center}
%\vspace{0.5cm}

\noindent This assignment accounts for 15\% of your final grade. 

\section*{Goals}
\vspace{-3mm}
This assignment aims to get you familiar with C++ and some of the concepts and representation of images in digital form. As part of your work, you will implement a general image class in C++ and apply mathematical operations on  pictures from storage.

\subsection*{Portable PixMap (PPM), Portable GreyMap (PGM), Portable BitMap (PBM) File Formats}
\vspace{-3mm}
The image file format you will work with is the Portable PixMap PPM (also known as PGM or PBM) file format. For more information about the file format, see \href{http://paulbourke.net/dataformats/ppm/}{here}, and \href{https://people.cs.clemson.edu/~dhouse/courses/405/notes/ppm-files.pdf}{here}.

In this assignment, you must implement methods to handle PPM files of types: 
\begin{itemize}
\item P2 and P5: grayscale images in binary and ASCII representation, respectively
\item P3 and P6: color images (R, G, B) in binary and ASCII representation, respectively. 
\end{itemize}

\subsection*{Submission}
\vspace{-3mm}
\begin{enumerate}
\item Follow the link (to be sent by email) to create your repository at \url{https://classroom.github.com/classrooms/70291231-cs-cy-6533-fall-2020-section-01}.
\item Add a readme in pdf or markdown format as a report of what you did containing a screenshot for each task
\item Push the code into the repository before deadline and make sure your code builds on Linux OS.
\end{enumerate}

\subsection*{Tasks}
\vspace{-2mm}
We advise all non-private questions be posted on the class Discord channel, as reference for all students.
For other questions, please email us or join us on the office hours.
\vspace{-3mm}

\section{Mandatory Tasks}
\vspace{-4mm}
For each tasks below, add at least one image in the readme demonstrating the results. Although we provided test images (Mandrill and Tandon), you are encouraged to execute the following items on other images.

The code that you used for all tasks should be provided.
\vspace{-3mm}

\subsection{Image Class}
\vspace{-3mm}
Implement a general image class in C++. Your class must handle PPM files of different types (P2, P3, P5, and P6) and load from and store the picture data on external storage.

You must create a performance-optimized and memory friendly representation for the internal data (the pixels data)\footnote{\textbf{Hint:} Learn about contiguous memory allocation.}.

Here is an example of how the objects of your class should behave:

\scriptsize
\begin{verbatim}
#include <iostream>
#include <exception>

#include "MyImageClass.h"

int main(int argc, char* argv[]) {

    try {
        MyImageClass image1("path_to_image_on_disk/pic.ppm");
        
        // Another possible way to load it from the disk in the "C++ way"
        MyImageClass image2;
        ifstream imageFile1;
        // If the file is a PPM type 5 or 6 (binary)
        imageFile1.open("path_to_image_on_disk/pic.ppm", ios::in | ios::binary);
        if (imageFile1.is_open()) {
           imageFile1 >> image2;
           imageFile1.close();
        }

        // You can do this way
        image1.save("path_to_disk/changed_pic.ppm");

        //You also can do it in the "C++ way"
        ofstream imageFile;
        imageFile.open("path_to_disk/changed_pic.ppm");
        if (imageFile.is_open()) {
           imageFile << image1;
           imageFile.close();
        }
    } catch(exception& e) {
        std::cout << "Error: " << e.what() << std::endl;
    }

    return 0;
}
\end{verbatim}
\normalsize

A good introduction to C++'s exceptions can be found \href{http://www.cplusplus.com/doc/tutorial/exceptions/}{here}.

When projecting your image class remember, you must be able to create empty images or delete (reset) the content of an image.

\subsection{Operations on Images}
\vspace{-3mm}
Using \href{https://en.cppreference.com/w/cpp/language/operators}{C++'s operator overloading mechanism}, add the following operations to your image class:
\begin{itemize}
\item addition (also addition assignment), subtraction (also subtraction assignment), and multiplication by a scalar value,
\item array index operator (brackets operator).  
\end{itemize}

Here is an example of how the objects of your class should behavior:

\scriptsize
\begin{verbatim}
#include <iostream>
#include <exception>

#include "MyImageClass.h"

int main(int argc, char* argv[]) {

    try {
        MyImageClass image1("path_to_image_on_disk/pic.ppm");
        MyImageClass image2("path_to_image_on_disk/pic2.ppm");
        MyImageClass image3;

        // Add Image 1 and 2 and assign result to image 3
        image3 = image1 + image2;

        image3.save("path_to_disk/add_pic.ppm");

        // Addition assignment plus mirroring on X axis
        MyImageClass image4;
        image4 += image3;
        image4.mirrorX();

        image4.save("path_to_disk/mirror_pic.ppm");

    } catch(exception& e) {
        std::cout << "Error: " << e.what() << std::endl;
    }

    return 0;
}
\end{verbatim}
\normalsize

\begin{figure}[t]
  \centering
  \fbox{\includegraphics[width=0.99\linewidth]{MandrillColorAndTandonColor}}
%  \vspace*{-5mm}
  \caption{The result of adding the Mandrill image and the Tandon Color image together. What is happening with the colors in the resulting image?}
  \label{fig:adding}
  \vspace*{-3.5mm}  
\end{figure}

\begin{figure}[t]
  \centering
  \fbox{\includegraphics[width=0.4\linewidth]{MandrillColorMinusTandonColor}}
%  \vspace*{-5mm}
  \caption{The result of subtracting from the Mandrill image, the Tandon Color image.}
  \label{fig:minus}
  \vspace*{-3.5mm}  
\end{figure}

You must pay attention to the following issues:
\begin{itemize}
\item The addition of images can generate results greater than the maximum value of a pixel (in a PPM file, the maximum value is equal to 255). You must allow this behavior for the \texttt{add} operator 
(operator+). However, when using the addition assignment operator (operator+=), you must average the result of adding the two pixels values.
\item The subtracting operator can produce pixels with values less than zero (0). You must take care of this issue (hint: \texttt{std::clamp}).
\item The multiplication of pixels by a scalar can produce overflows and underflows of pixels values.
\end{itemize}

\subsection{Gamma Correction}
\vspace{-3mm}

Utilizing the previously implemented operators, implement a method to apply gamma correction given a gamma constant value.

\subsection{Alpha Compositing}
\vspace{-3mm}

Alpha Compositing is explained in section 3.4 of the textbook. Utilizing the previously implemented operators and equation 3.2 in section 3.4, implement alpha compositing.

\begin{figure}[t]
  \centering
  \fbox{\includegraphics[width=0.4\linewidth]{MandrillColorAndTandonColorApha50}}
%  \vspace*{-5mm}
  \caption{The result of applying alpha compositing to the Mandrill image (front picture) and the Tandon Color image (back picture) for an alpha value equals to 0.5.}
  \label{fig:alpha50}
  \vspace*{-3.5mm}  
\end{figure}

\begin{figure}[t]
  \centering
  \fbox{\includegraphics[width=0.4\linewidth]{MandrillColorAndTandonColorApha85}}
%  \vspace*{-5mm}
  \caption{The result of applying alpha compositing to the Mandrill image (front picture) and the Tandon Color image (back picture) for an alpha value equals to 0.85.}
  \label{fig:alpha85}
  \vspace*{-3.5mm}  
\end{figure}

\section*{Optional Tasks.}
\vspace{-3mm}
This task is optional and worth 1.5\% of the final grade. 

\subsection{Morphological Operators}

Read about Morphological Operators on Images (\href{https://www.cs.auckland.ac.nz/courses/compsci773s1c/lectures/ImageProcessing-html/topic4.htm}{link1}, \href{https://www.di.univr.it/documenti/OccorrenzaIns/matdid/matdid699113.pdf}{link2}, \href{https://www.researchgate.net/publication/272484795_Morphological_Operations_for_Image_Processing_Understanding_and_its_Applications}{link3}) and implement the dilatation and erosion operations.
Given an image (\textit{e.g.} \texttt{Mandrill.ppm}), apply the dilatation operation on it and save the result. Using the same original image, apply the erosion operation. Next, you must subtract from the result of the first operation (dilatation) the result of the second operation (erosion). What is the final result? Show it with pictures.

%\bibliographystyle{plain}
%\bibliography{bib.bib}
\end{document}  
