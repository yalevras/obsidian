# MONTH 1 — Linear Algebra & Math Fluency (Weeks 1–4)
## Week 1 — Vectors, matrices, intuition
**Study**
- MIT OCW **18.06**
    - Lectures 1–3
- Read:
    - _Linear Algebra and Its Applications_ (Strang)    
        - Ch. 1–2 (skip proofs)
**Do**
- NumPy matrix multiplication
- Visualize vectors, projections
**Deliverable**
- Python script: matrix multiply + geometric interpretation
## Week 2 — Eigenvalues = stability
**Study**
- 18.06 Lectures 21–23
- YouTube: “Eigenvalues explained visually” (3Blue1Brown)
**Read**
- Strang Ch. 5 (conceptual only)
**Do**
- Compute eigenvalues of 2×2 systems
- Relate sign → stability
**Deliverable**
- Plot stable vs unstable systems
## Week 3 — Calculus refresh (ODE intuition)
**Study**
- MIT OCW **18.03**
    - Lectures 1–4
**Read**
- _Advanced Engineering Mathematics_ (Kreyszig)
    - Ch. 1 (selected)
**Do**
- Solve first-order ODEs numerically
**Deliverable**
- Simulate exponential decay & growth
## Week 4 — Systems of ODEs
**Study**
- 18.03 Lectures 10–12
**Do**
- Convert ODEs → state-space
- Simulate coupled systems
**Deliverable**
- 2-state system simulation
# MONTH 2 — Signals & Systems (Weeks 5–8)
## Week 5 — LTI systems
**Study**
- MIT OCW **6.003**
    - Lectures 1–3
**Read**
- Oppenheim & Willsky
    - Ch. 1–2
**Do**
- Identify LTI vs non-LTI examples
## Week 6 — Convolution & impulse response
**Study**
- 6.003 Lectures 4–6
**Do**
- Implement convolution from scratch
- Step response simulation
**Deliverable**
- Convolution demo (time-domain)
## Week 7 — Frequency intuition
**Study**
- 6.003 Lectures 8–10
- 3Blue1Brown Fourier video
**Do**
- FFT of signals
- Low-pass vs high-pass behavior
## Week 8 — Filtering project
**Project**
- Noisy signal → filtered output
**Deliverable**
- Plots + explanation (why it works)
# MONTH 3 — Classical Control (Weeks 9–12)
## Week 9 — Feedback basics
**Study**
- Brian Douglas (YouTube): Feedback intro
- MIT **6.302** Lectures 1–2
**Do**
- Block diagram reduction
## Week 10 — PID control
**Study**
- Brian Douglas PID playlist
**Do**
- Tune PID on mass–spring–damper
**Deliverable**
- Stable vs unstable PID plots
## Week 11 — Stability intuition
**Study**
- 6.302 Lectures 5–6
**Do**
- Step response analysis
## Week 12 — Control mini-project
**Project**
- PID-controlled inverted pendulum (2D)
**Deliverable**
- Simulation + README
# MONTH 4 — State Space & Robotics (Weeks 13–16)
## Week 13 — State-space models
**Study**
- MIT **Underactuated Robotics**
    - Lectures 1–2
**Do**
- Write state equations
## Week 14 — Linearization
**Study**
- Underactuated Robotics Lectures 3–4
**Do**
- Jacobian computation
- Linearize nonlinear system
## Week 15 — Robotics dynamics
**Study**
- Spong, Hutchinson, Vidyasagar  
    _Robot Modeling and Control_
    - Ch. 3 (skim)
**Do**
- 2-link arm simulation
## Week 16 — Robotics control project
**Project**
- Stabilize robot joint angles
**Deliverable**
- Plots + control explanation
# MONTH 5 — Machine Learning (Weeks 17–20)
## Week 17 — Regression & optimization
**Study**
- Andrew Ng ML Lectures 1–3
**Do**
- Linear regression from scratch
## Week 18 — Classification
**Study**
- Andrew Ng Lectures 4–6
**Do**
- Logistic regression (NumPy only)
## Week 19 — Bias–variance
**Study**
- MIT **6.036** Lectures 7–9
**Do**
- Overfitting experiment
## Week 20 — ML mini-project
**Project**
- Binary classifier with evaluation
# MONTH 6 — Vision + Systems (Weeks 21–24)
## Week 21 — Image processing basics
**Study**
- Stanford **CS231n** Lectures 1–2
**Do**
- Convolution on images
## Week 22 — Features & PCA
**Study**
- CS231n Lectures 3–4
**Do**
- PCA on image dataset
## Week 23 — Distributed systems basics
**Study**
- MIT **6.824** Lectures 1–2
**Read**
- _Designing Data-Intensive Applications_
    - Ch. 1
## Week 24 — Compilers / interpreters
**Read**
- _Crafting Interpreters_
    - Ch. 1–6
**Do**
- Tiny expression interpreter
# MONTH 7 — Capstone + Review (Weeks 25–28)
## Weeks 25–27 — Capstone project
Pick ONE:
- Robot + vision system
- Distributed ML pipeline
- Neuro signal filtering system
**Requirements**
- control OR ML
- real plots
- written explanation
## Week 28 — Final polish
- Review weak spots
- Summarize notes
- Prepare “cheat sheets” for:
    - control
    - ML
    - systems

# TIER 1: Highest-Value Extra Weeks (Do These First)
### ➕ Weeks A1–A2 — Control mastery buffer (VERY HIGH VALUE)
**Why**  
ECE470 + MIE505 are still your riskiest courses even after prep.
**What to do**
- Re-do control problems _without notes_
- Design controllers for:
    - unstable systems
    - noisy measurements
- Compare:
    - PID vs state-feedback
**Resources**
- Brian Douglas (advanced PID tuning)
- MIT Underactuated Robotics (Lectures 5–7)
**Courses helped**
- ECE470
- MIE505
- ECE441
**Risk reduced**  
Failing or barely passing robotics/control-heavy courses
### ➕ Weeks A3–A4 — Numerical methods for engineers
**Why**  
Almost all your courses _assume_ you can solve things numerically.
**Topics**
- Euler vs Runge–Kutta
- stability of numerical solvers
- discretization errors
**Resources**
- MIT OCW **18.330** (selected)
- _Numerical Recipes_ (skim)
**Courses helped**
- ECE470
- CSC420
- ECE421
- ECE462
**Risk reduced**  
Silent bugs and wrong simulations
# TIER 2: Strong Resume + Course Synergy
### ➕ Weeks B1–B2 — Sensor fusion & estimation
**Why**  
This ties robotics + signals + ML together.
**Topics**
- Kalman filter (intuition only)
- noisy measurements
- estimation vs control
**Resources**
- MIT **6.832 Underactuated Robotics** (Kalman intro)
- Welch & Bishop Kalman Filter tutorial
**Courses helped**
- ECE470
- MIE505
- ECE441
- CSC420
**Risk reduced**  
Confusion between sensing and control
### ➕ Weeks B3–B4 — Advanced ML intuition
**Why**  
ECE421 goes fast; intuition saves time.
**Topics**
- regularization
- cross-validation
- feature engineering
**Resources**
- MIT **6.036** advanced lectures
- ISLR (Introduction to Statistical Learning)
**Courses helped**
- ECE421
- CSC420
- APS360
**Risk reduced**  
Overfitting and poor model choices
# TIER 3: Systems Depth (Optional but Powerful)
### ➕ Weeks C1–C2 — Distributed systems practice
**Why**  
ECE419 rewards real-world intuition.
**Topics**
- consensus failures
- clock skew
- fault tolerance
**Resources**
- MIT **6.824** Labs (read, don’t implement all)
- _Designing Data-Intensive Applications_ Ch. 8–9
**Courses helped**
- ECE419
- OS interviews
- Real-world systems work
**Risk reduced**  
Abstract systems confusion
### ➕ Weeks C3–C4 — Low-level performance thinking
**Why**  
Helps OS, compilers, and systems debugging.
**Topics**
- caching
- memory layout
- branch prediction (intuition)
**Resources**
- CS:APP (Computer Systems: A Programmer’s Perspective)
- Matt Godbolt talks (Compiler Explorer)
**Courses helped**
- ECE467
- ECE419
- ECE344
**Risk reduced**  
Hard-to-debug performance issues