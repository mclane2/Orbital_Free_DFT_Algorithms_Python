# Orbital_Free_DFT_Python
This project provides an overview of some highlights from my Capstone Project thesis "Minimization of the Non-Interacting Kinetic Energy Functional" for the completion of my degree in Physics and Astrophysics at Trinity College Dublin. I recieved a first class honors for this project.

The main goal of this project was to understand and implement orbital-free density functional theory (OFDFT) for a single electron system. Such a system has the unique property in DFT that the only important energy functional is the von Weizsacher (vW) functional. Since the vW functional is exact in the single electron case, an OFDFT minimization should reproduce the exact results of the Schrodinger equation. I wrote the code "Minimization Algorithm.ipynb" that achieves this on a one-dimensional real-space grid with boundary conditions that force the electron density to go to zero (an infinite well superimposed with another external potential). The code solves the Schrodinger equation first (using matrix diagonalization of the Hamiltonian) to act as a benchmark to assess the accuracy of the OFDFT minimization. 

This project required me to learn a lot about DFT which was something I hadn't covered in my course modules. It took a lot of work. I created the document "Background_Theory" to attempt to explain how DFT and OFDFT work and how it applies to my project.

Over the course of this project, I learned not only about DFT but also about numerical methods. I found that this particular type of non-linear numerical minimization was quite different to the kinds of problems I had solved previously. Despite being unfamiliar, the way it works is quite simple, so I created the document "OFDFT_Algorithms" to explain some of the methods.

The two pdf documents are mostly extracted from my thesis





