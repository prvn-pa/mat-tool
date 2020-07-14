---
marp: true
theme: default
paginate: true
footer: JMC Organized **'Skill Development Programme on Learning Assistance Tools'** | Day 02 | **Materials Science Simulation Tools**
backgroundColor: #C2FFD8
---
![bg opacity](img/vc.jpg)
Advanced Tools for Materials Science
===

### Dr. P. A. Praveen   
**Post Doctoral Fellow, IISER Tirupati**
##### ✉:`contact@prvn.info`

View this slide deck here: **bit.ly/2OnAzIu**

---
![bg opacity](img/vc.jpg)

## Outline of Talk ##

1. What is Materials Science?
2. Physical Theories
3. DFT: The Efficient Beast
4. Semiempirical Analysis: Poor man's Gold

---
![bg opacity](img/vc.jpg)

## What is Materials Science? ##

- Solid state / condensed matter physics
- Electronics, Optics, Magnetics & Thermodynamics
- Roots to chemistry
- Branches to biology
- Contributes to entire humanity

---
![bg opacity](img/vc.jpg)

## Materials Science Tetrahedron ##

![w:800](https://i.pinimg.com/originals/74/5b/39/745b39f43fe250ded54002910f092637.jpg)

Image from [DOI: 10.1038/nmat3367](https://doi.org/10.1038/nmat3367)

---
![bg opacity](img/vc.jpg)

## Experiments to study materials ##

* X-ray Diffraction - Crystalline structure
* FTIR/Raman - Molecular structure
* AFM,SEM,TEM - Surface or nano level properties
* Other specific methods

---
![bg opacity](img/vc.jpg)

## Theoretical Analysis ##

* Most of the materials properties arise due to valence electrons
* Schrödinger equation can be used to solve the electronic interaction in a atomic / molecular system
  
* ![](https://wikimedia.org/api/rest_v1/media/math/render/svg/0de8741a7d26ae98689c7b3339e97dfafea9fd26)

* But there is no direct way to solve Schrödinger's equation
* Numerical methods like Hartree-Fock, Density functional theory, semiempirical methods are used to solve the equation.

---
![bg opacity](img/vc.jpg)

## What are we gonna' see today? ##

- Geometry optimization and FTIR, Raman, UV-Vis Absorption, Fluorescence spectrum simulation of methane system
- Geometry optimization and nonlinear optical properties of ZnO nanoclusters

---
![bg opacity](img/vc.jpg)

## But wait! What is that Geometry Optimization? ##

![h:500](https://lh3.googleusercontent.com/proxy/9zJo4hvweZqFqxefUYJuSelpgxfSXRhntxx6tFEpGiyUXL0O4QRuhMMSqBNNn52kgxwcwa8jNjuNkC3adQ9UcOpYj2t82sf2K9TH0qGKqe2dflhPcM32)

Source: [http://cmt.dur.ac.uk/sjc/thesis_dlc/node37.html](http://cmt.dur.ac.uk/sjc/thesis_dlc/node37.html)

---
![bg opacity](img/vc.jpg)

## What happen when optimize a molecule?

![h:500](https://www.orcasoftware.de/tutorials/_images/opt.gif)

---
![bg opacity](img/vc.jpg)

## Demo: DFT for spectral simulations ##

**Molecular input preparation**

Requires: Marvin Sketch; Avogadro & Gabedit

---
![bg opacity](img/vc.jpg)

## Demo: Geometry Optimization ##

Requires: **ORCA**

```
! Opt TightSCF B3LYP/G
! PrintBasis 6-31G(d,p)
%geom
     	Calc_Hess true
        Recalc_Hess 10
 end #geom
%output
     print[p_mos] 1
 end #output
* xyzfile 0  1 methane.xyz
```

---
![bg opacity](img/vc.jpg)

## Demo: FTIR Spectrum ##

Requires: **ORCA**

```
! TightSCF B3LYP/G FREQ
! PrintBasis 6-31G(d,p)

%output
     print[p_mos] 1
 end #output
* xyzfile 0  1 geo.xyz
```

---
![bg opacity](img/vc.jpg)

## Demo: Raman Spectrum ##

Requires: **ORCA**

```
! TightSCF B3LYP/G NUMFREQ
! PrintBasis 6-31G(d,p)

%ELPROP
   POLAR 1
END

%output
     print[p_mos] 1
 end #output
* xyzfile 0  1 geo.xyz
```

---
![bg opacity](img/vc.jpg)

## Demo: UV & Fluorescence Spectrum ##

Requires: **ORCA**

```
! B3LYP/G TightSCF NMGrad RIJCOSX GRID6 GRIDX6 RI-SOMF(1X)
! PrintBasis 6-31G(d,p)

%tddft
      	nroots 5
end

%rr
   	states 1,2,3,4,5
        HessName "geo.hess"
        ASAInput true
end

* xyzfile 0  1 geo.xyz
```
---

![bg opacity](img/vc.jpg)

## Demo: Semiemprical Calculations

**Requires:** Avogadro, MOPAC

**Steps:**

1. Input file preparation
2. Geometry Optimization
3. Geometry verification
4. Polarizability calculation

---

![bg opacity](img/vc.jpg)

## Demo: ZnO Nanocluster

**Step: 01**

1. Draw the cluster using Avogadro
2. Preoptimize with UFF
3. Extract MOPAC Input
4. Change the commands in first line

```
LET AUX LARGE CHARGE=0 GNORM=1 PM7
```

---

![bg opacity](img/vc.jpg)

## Demo: ZnO Nanocluster

**Step: 02**

1. Do `FORCE` Calculation
2. Do `POLAR` Calculation
3. Optionally simulate `HOMO`, `LUMO` and E$_g$

```
FORCE: LET  AUX LARGE CHARGE=0 FORCE PM7
POLAR: LET  AUX LARGE CHARGE=0 POLAR PM7
```

---

![bg opacity](img/vc.jpg)

## References:

1. Computational Materials Science: An Introduction by June Lee
2. Tutorials: https://www.comats.xyz
3. Avogadro: https://avogadro.cc/
4. Gabedit: http://gabedit.sourceforge.net/
5. Orca: https://sites.google.com/site/orcainputlibrary/home
6. MOPAC: http://openmopac.net/MOPAC2016.html

---

![bg](img/thanks.jpg)
