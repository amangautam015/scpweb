# Assignment_2 ME405 (Post Midsem)

#### Language : Python-3

---

### Code Algorithm and Explanation

**Initialization of given data**

```
    P0byP9 = 0.5
    Pid = 0.95
    Pin = 0.98
    Pib = 0.92
    ec = 0.95
    et = 0.9
    Tt4  = 1500
    Effb  = 0.99
    GammaT = 1.3
    GammaC = 1.4
    Cpt = 1004
    Cpc = 1004
    Hpr = 42800000
    Effm = 0.96
    a0  = 340 #Speed of sound in Air as calculated from sqrt(GammaRT)
    T0 = 220 #Approxximately in K at 10km altitude #
    Td =1
    Tn =1.
    M = np.arange(.5,3.01,.5) #mach_no 0.3 to 5 at .5 step
    CompressorPRatio = np.arange(5,30,5) #Compressor presure ratio 5 to 30 at step of 5
```

<img src="https://raw.githubusercontent.com/amangautam015/scpweb/master/datainit.jpg"   height="200" />

---

**Calculations**

```
 Tc = pow(Pic,(GammaC-1)/(GammaC*ec))
 Tr = 1+(GammaC-1)*0.5*mach_no
 f = (Tlambda-Tc*Tr)/((Effb*Hpr)/(Cpc*T0)-Tlambda)
 Tt = 1 - Tr*(Tc-1)/(Tlambda*Effm*(1+f))
```

<img src="https://raw.githubusercontent.com/amangautam015/scpweb/master/data2.jpg"   height="200" />
<br>

```
Tb = Tlambda/(Tr*Tc)
Pit = pow(Tt,(GammaC/(et*(GammaC-1))))
Pir = pow(Tr,(1/((GammaC-1))))
Pt9byP9 = P0byP9 * Pib*Pic*Pid*Pin*Pir*Pit
Tt9byT0 = Tr*Td*Tn*Tc*Tb*Tt
M92 = (2/(GammaT-1))*(pow(Pt9byP9,(GammaT-1)/GammaT)-1)
```

<img src="https://raw.githubusercontent.com/amangautam015/scpweb/master/data4.jpg"   height="200" />
<br>

```
 T9byT0 = Tt9byT0/pow(Pt9byP9,(GammaT-1)/GammaT)
 V9bya0 = sqrt(Tt9byT0*M92)
```
<img src="https://raw.githubusercontent.com/amangautam015/scpweb/master/data3.jpg"   height="200" />
<br>

```
me=(a0*a0*((1+f)*pow(V9bya0,2)-mach_no*mach_no))/(2*Hpr*f) #Thermo Efficiency
mf=a0*((1+f)*V9bya0-mach_no+((1+f)*T9byT0*(1-P0byP9))/(V9bya0*a0)) #F/m0
```
<img src="https://raw.githubusercontent.com/amangautam015/scpweb/master/data5.jpg"   height="200" />
<br>

---

**Results (Graphs)**
<br>
<img src="https://raw.githubusercontent.com/amangautam015/scpweb/master/Figure_1.png"  />
<br>

---

**IDE Used**
`PyCharm JetBrains`

**Libraries**
1) numpy `pip install numpy`
2) Matplotlib `pip install matplotlib`
3) scipy `pip install scipy`

---
