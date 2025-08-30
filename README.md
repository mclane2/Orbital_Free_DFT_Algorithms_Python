# Orbital_Free_DFT_Python
This project provides an overview of some highlights from my Capstone Project thesis "Minimization of the Non-Interacting Kinetic Energy Functional" for the completion of my degree in Physics and Astrophysics at Trinity College Dublin. I received a first class honors (75%) for this project. Here I have uploaded a Jupyter notebook file that includes most of the important code, and two pdfs containing extracts from my thesis that explain the background physics and the numerical methods used.

## Description
At its foundation, this project is rooted in computational condensed matter physics, a field where researchers use computer simulations to understand how electrons behave inside materials. One of the most powerful tools for this is Density Functional Theory (DFT), which replaces the impossible task of tracking every detail of every electron with a simpler but accurate description based on the overall electron density. In this project, I worked on a specialized field of DFT called Orbital-Free DFT (OFDFT). This version of DFT has the potential to make simulations far faster, but it is also more challenging to get right. By testing it on the simplest possible case of a single electron trapped in a potential, I could validate whether the method reproduces exact results, and test how robust the algorithms are under different conditions.

The main goal of this project was to understand and implement OFDFT for a single electron system. Such a system has the unique property in DFT that the only important energy functional is the von Weizsacher (vW) functional. Since the vW functional is exact in the single electron case, an OFDFT minimization should reproduce the exact results of the Schrodinger equation. I wrote the code ```Minimization Algorithm.ipynb``` that achieves this on a one-dimensional real-space grid with boundary conditions that force the electron density to go to zero (an infinite well superimposed with another external potential). The code solves the Schrodinger equation first (using matrix diagonalization of the Hamiltonian) to act as a benchmark to assess the accuracy of the OFDFT minimization. 

This project required me to learn a lot about DFT, which was something I hadn't covered in my course modules. I created the document ```Background_Theory.pdf``` to explain how DFT and OFDFT work and how it applies to my project. 

Over the course of this project, I learned not only about DFT but also about some advanced numerical methods. I found that this particular type of non-linear numerical minimization was quite different to the kinds of problems I had solved previously. Despite being unfamiliar, the way it works is quite simple, so I created the document ```OFDFT_Algorithms.pdf``` to explain some of the methods. The literature specifically focused on the OFDFT minimization algorithm was sparse and spread out over the course of decades, so I wanted to summarise all the techniques here and clear up any confusions about them in a single document. 

## Installation
To see the minimization algorithm in Python, simply download ```Minimization Algorithm.ipynb``` and run it on anything that can open .ipynb files. The minimum requirements are Python 3.9+, numpy, scipy and matplotlib. All the required functions are defined within the notebook.

## Code Usage
- In section 1 of ```Minimization Algorithm.ipynb```, the necessary functions to run the code are defined.
- In section 2, you must select the external potential that will be solved. The uncommented gaussian potential usually converges successfully. You can test out the other commented potentials or define your own ones.
- In section 3, you must similarly define the initial guess density. If you define your own one, make sure that it runs through ```normalize_wavefunction``` and is then squared before saving the array.
- Section 4 is the Schrodinger equation solver, it should always compute the correct density for your inputted external potential.
- In section 5, I defined some more necessary functions for the minimization algorithm
- Section 6 is the minimization algorithm. It will produce a series of plots showing your chosen initial guess density iteratively approaching the solution to the schrodinger equation. Usually the first few iterations will always progress smoothly towards the target, but if you changed the initial guess or external potential, you will likely need to play around with the step sizes to avoid divergences. This can be done by changing the array "theta", or by adding more conditions to the Wolfe conditions to make sure the algorithm doesn't jump to an unstable density. If the algorithm is converging too early or not converging despite approaching the solution, you can adjust the convergence conditions ```tao``` and ```tau``` or the convergence if statements that terminate the loop.
- Section 7 calculates the energy associated with the converged density and compares it with the energy associated with the schrodinger equation density and with the energy eigenvalue.

## Repository Contents
- ```Minimization Algorithm.ipynb``` - the primary Jupyter notebook containing the Schrodinger equation solver, OFDFT minimization algorithm and plots
- ```Background_Theory.pdf``` - a self-contained summary of the necessary DFT and OFDFT needed to understand this project.
- ```OFDFT_Algorithms.pdf``` - an explanation and review/survey of OFDFT numerical minimization techniques used in the literature

## Suggestions for improvement
One of the main findings of this project was the instability of the vW functional in this setting, which is discussed in my thesis. If you change the initial guess and external potential in my code, you'll likely find that the algorithm usually becomes unstable before converging on the solution to Schrodinger equation. Any ways of automating the search for stable step sizes or automatically adjusting the convergence conditions for different potentials and initial guesses could help make the density more consistently converge on the target solution. 

## Contact
Email **Marc Lane** - lanem2@tcd.ie
