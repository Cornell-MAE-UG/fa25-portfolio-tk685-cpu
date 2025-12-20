---
layout: project
title: Thermodynamic Analysis of the IFHX (Heat Exchanger Device) 
description: For ENGRD 2210 homework
technologies: [NA]
image: 
- /assets/images/activethermalcontrolsystemarchitecture.jpg
---
**<u>1. Background Information</u>**

**1.0. What is the ISS, and why do we need thermal control?**

The International Space Station (ISS) is a permanently crewed orbital laboratory in low Earth orbit, typically around 370–460 km above Earth. It’s used for research in microgravity, testing new space technologies, Earth observation, and learning how humans and systems perform during long-duration missions. 

Because the ISS is basically a giant collection of powered systems (life support, computers, experiments, communications, etc.), it constantly produces waste heat. NASA describes that most of the station’s systems generate waste heat, and that this heat has to be moved away to maintain thermal control and keep equipment within acceptable temperature limits. If that heat is not managed, components can overheat or go out of their certified operating range, which can affect performance and safety. 

**1.1. How does the ISS control heat?**

![Design of my choice]({{ "/assets/images/activethermalcontrolsystemarchitecture.jpg" | relative_url }}){: .inline-image-r style="width: 400px"}

The ISS uses both passive and active thermal control. Passive thermal control is basically the set of approaches that help manage temperatures without powered fluid systems, such as insulation/MLI, surface coatings, and heat pipes (and other passive hardware depending on context).  

However, when the external environment and the station’s internal heat loads exceed what passive methods can handle, the ISS relies on an Active Thermal Control System (ATCS). NASA describes the ATCS as using mechanically pumped fluids in closed-loop circuits to do three jobs: collect heat, transport heat, and reject heat. 

On the U.S. On-Orbit Segment, waste heat is removed mainly through cold plates and heat exchangers, which are ultimately cooled by external ammonia loops. The warmed ammonia then flows through large external radiators, where heat is rejected by thermal radiation to space, cooling the ammonia as it passes through the radiator panels. 

As shown in Figure 1, the ISS ATCS architecture includes the Internal Active Thermal Control System (IATCS), the External Active Thermal Control System (EATCS), the Photovoltaic Thermal Control System (PVTCS), and the Early External Active Thermal Control System (EEATCS). The internal system circulates water through pressurized modules to pick up heat from equipment and experiments, and then transfers that heat through interface heat exchangers to the external ammonia loops. NASA notes that, at assembly complete, there are nine separate ITCS water loops across the U.S. and International Partner pressurized modules. 

**1.2. Interface Heat Exchanger (IFHX) and why it matters**

A good example of why the IFHX is important happened during ISS Expedition 38 in December 2013. NASA documentation describes a situation where an issue involving a flow control valve in a pump module and subsequent thermal-control configuration choices led to the water temperature dropping close to freezing in the Columbus module’s moderate temperature loop heat exchanger path.  

NASA’s case study explains the main concern clearly: if water in the IFHX freezes, the expansion could damage or rupture the barrier between the internal water loop and the external ammonia loop. A rupture could allow ammonia to enter the crewed interior, which NASA describes as potentially leading to loss of crew/loss of vehicles in the worst case. 

Because the IFHX is literally the interface between internal heat pickup and external heat rejection, it ends up being a critical point where thermal performance and safety meet. So, in this portfolio, the analysis will focus specifically on the Interface Heat Exchanger (IFHX) as the device of interest: the heat exchanger hardware that transfers waste heat from the ISS internal water-cooling loops to the external ammonia loops before that heat is rejected by the external radiators. 

**<u>2. Analysis Setup</u>**

**2.0. Setup**

![Design of my choice]({{ "/assets/images/interfaceheatexchanger.jpg" | relative_url }}){: .inline-image-r style="width: 400px"}

For the thermodynamic analysis portion of this portfolio, I am treating the Interface Heat Exchanger (IFHX) as the “device.” More specifically, I am analyzing one IFHX core as a two-stream, steady-flow heat exchanger:
- Hot side: one internal ITCS water loop (I will use the Moderate Temperature Loop, MTL, as the example case)
- Cold side: the external EATCS ammonia loop

This approach is slightly simplified compared to reality. In the full ISS architecture, there are multiple internal loops (including MTL and LTL) and multiple IFHX units on each external loop, plus active control elements that regulate ammonia temperature. Here, I am doing a single “snapshot” device analysis of one IFHX under a representative operating condition so I can apply the heat exchanger thermodynamics we learned (steady-flow energy balance + heat exchanger performance).

**2.1. Device definition + control volume**

Control volume: the IFHX core (both fluid streams inside the exchanger). We treat the IFHX as a steady-flow control volume, with one water stream and one ammonia stream exchanging heat through the walls (no mixing).

Two inlets, two outlets:
$$
\begin{aligned}
\text{Water (MTL):}\quad & \dot{m}_w,\; T_{w,\text{in}},\; T_{w,\text{out}} \\
\text{Ammonia:}\quad & \dot{m}_a,\; T_{a,\text{in}},\; T_{a,\text{out}}
\end{aligned}
$$

Heat transfer sign convention:
$$
\dot{Q}_{HX} > 0 \;\;\Rightarrow\;\; \text{heat flows from water to ammonia.}
$$

**2.2. What I call “inlet” vs “outlet”**

For the water loop, the IFHX is where the internal coolant gets cooled before going back to equipment:

$$
\begin{aligned}
T_{w,in} &: \text{warmer “return” water entering the IFHX from equipment} \\
T_{w,out} &: \text{cooled “supply” water leaving the IFHX back to equipment}
\end{aligned}
$$

For the **ammonia loop**, ammonia enters colder and leaves warmer:

$$
\begin{aligned}
T_{a,in} &: \text{colder ammonia entering the IFHX} \\
T_{a,out} &: \text{warmer ammonia leaving the IFHX}
\end{aligned}
$$

So we expect:

$$
\begin{aligned}
T_{w,in} &> T_{w,out} \\
T_{a,out} &> T_{a,in}
\end{aligned}
$$

**2.3. Assumptions**

I’m using standard heat exchanger / steady-flow device assumptions:
1. Steady state / steady flow
2. No shaft work: $\dot{W}_s = 0$
3. Negligible kinetic and potential energy changes
4. Externally well insulated heat exchanger: negligible heat leak to surroundings
5. Single-phase, constant

**<mark>3. Thermodynamic Analysis <mark>**

**3.0. Mass Balance**

No mixing or accumulation in the IFHX, so each stream’s mass flow rate is conserved:

$$
\begin{aligned}
\dot{m}_{w,in} &= \dot{m}_{w,out} = \dot{m}_w \\
\dot{m}_{a,in} &= \dot{m}_{a,out} = \dot{m}_a
\end{aligned}
$$

**3.1 Steady-flow energy equation**

The general steady-flow energy balance for the control volume is:

$$
\begin{aligned}
\dot{Q} - \dot{W}_s 
+ \sum_{\text{in}} \dot{m}\left(h + \frac{V^2}{2} + gz\right)
&=
\sum_{\text{out}} \dot{m}\left(h + \frac{V^2}{2} + gz\right)
\end{aligned}
$$

For the IFHX, we assume

$$
\dot{W}_s = 0
$$

and we neglect kinetic/potential energy changes and heat loss to the surroundings. Under these assumptions, the heat transferred from water to ammonia satisfies:

$$
\begin{aligned}
\dot{Q}_{HX} &= \dot{m}_w\left(h_{w,in} - h_{w,out}\right) \\
\dot{Q}_{HX} &= \dot{m}_a\left(h_{a,out} - h_{a,in}\right)
\end{aligned}
$$

So the core equality is:

$$
\dot{m}_w\left(h_{w,in} - h_{w,out}\right)
=
\dot{m}_a\left(h_{a,out} - h_{a,in}\right)
$$

If we assume constant specific heats (single-phase, first-pass model):

$$
\dot{Q}_{HX}
=
\dot{m}_w c_{p,w}\left(T_{w,in} - T_{w,out}\right)
=
\dot{m}_a c_{p,a}\left(T_{a,out} - T_{a,in}\right)
$$

**3.3 Efficiency**

In heat exchanger analysis, the standard performance metric is the effectiveness:

$$
\varepsilon = \frac{\dot{Q}_{HX}}{\dot{Q}_{\max}}
$$

where the maximum possible heat transfer is

$$
\dot{Q}_{\max} = C_{\min}\left(T_{w,in} - T_{a,in}\right).
$$

Define heat capacity rates:

$$
\begin{aligned}
C_w &= \dot{m}_w c_{p,w} \\
C_a &= \dot{m}_a c_{p,a} \\
C_{\min} &= \min\left(C_w,\, C_a\right)
\end{aligned}
$$

So the effectiveness becomes:

$$
\boxed{
\varepsilon
=
\frac{\dot{Q}_{HX}}
{C_{\min}\left(T_{w,in} - T_{a,in}\right)}
}
$$

**<mark>4. Plug in numbers (example MTL IFHX operating point) <mark>**

**4.1 Given / chosen data**

For a representative operating point:

- Heat transfer rate: $\dot{Q}_{HX} = 12\ \text{kW}$  
- Water mass flow: $\dot{m}_w = 1{,}361\ \text{kg/hr}$  
- Ammonia mass flow: $\dot{m}_a = 8{,}200\ \text{lb/hr}$  
- Water outlet (cooled supply): $T_{w,out} = 17^\circ\text{C}$  
- Ammonia inlet: $T_{a,in} = 2.8^\circ\text{C}$  
- $c_{p,w} = 4.18\ \text{kJ/kg}\cdot\text{K}$ (liquid water, approx.)  
- $c_{p,a} \approx 4.6\ \text{kJ/kg}\cdot\text{K}$ (liquid ammonia, approx.)

Convert flow rates:

$$
\begin{aligned}
\dot m_w &= \frac{1361}{3600} \\
&= 0.378\ \text{kg/s}
\end{aligned}
$$

$$
\begin{aligned}
\dot m_a 
&= 8200\ \frac{\text{lb}}{\text{hr}}
\left(\frac{0.4536\ \text{kg}}{1\ \text{lb}}\right)
\left(\frac{1\ \text{hr}}{3600\ \text{s}}\right) \\
&= 1.033\ \text{kg/s}
\end{aligned}
$$

**4.2 Solve for the water inlet temperature $T_{w,in}$**

Start from:

$$
\begin{aligned}
\dot Q_{HX} &= \dot m_w c_{p,w}\left(T_{w,in} - T_{w,out}\right)
\end{aligned}
$$

Solve for the temperature drop on the water side:

$$
\begin{aligned}
T_{w,in} - T_{w,out}
&= \frac{\dot Q_{HX}}{\dot m_w c_{p,w}} \\
&= \frac{12}{(0.378)(4.18)} \\
&= 7.59\ \text{K}
\end{aligned}
$$

So:

$$
\begin{aligned}
T_{w,in}
&= T_{w,out} + 7.59 \\
&= 17 + 7.59 \\
&= 24.6^\circ\text{C}
\end{aligned}
$$

**4.3 Solve for the ammonia outlet temperature $T_{a,out}$**

First compute the ammonia enthalpy rise per kg:

$$
\begin{aligned}
\Delta h_a 
&= \frac{\dot Q_{HX}}{\dot m_a} \\
&= \frac{12}{1.033} \\
&= 11.6\ \text{kJ/kg}
\end{aligned}
$$

Approximate the ammonia temperature rise using $c_{p,a}$:

$$
\begin{aligned}
T_{a,out} - T_{a,in}
&\approx \frac{\Delta h_a}{c_{p,a}} \\
&= \frac{11.6}{4.6} \\
&= 2.52\ \text{K}
\end{aligned}
$$

So:

$$
\begin{aligned}
T_{a,out}
&= T_{a,in} + 2.52 \\
&= 2.8 + 2.52 \\
&= 5.3^\circ\text{C}
\end{aligned}
$$

**4.4 Efficiency**

Compute heat capacity rates:

$$
\begin{aligned}
C_w &= \dot{m}_w c_{p,w} \\
&= (0.378)(4.18) \\
&= 1.58\ \text{kW/K}
\end{aligned}
$$

$$
\begin{aligned}
C_a &= \dot{m}_a c_{p,a} \\
&= (1.033)(4.6) \\
&= 4.75\ \text{kW/K}
\end{aligned}
$$

So:

$$
\begin{aligned}
C_{\min} &= \min(C_w, C_a) \\
&= 1.58\ \text{kW/K}
\end{aligned}
$$

Compute maximum possible heat transfer:

$$
\begin{aligned}
\dot{Q}_{\max}
&= C_{\min}\left(T_{w,in} - T_{a,in}\right) \\
&= (1.58)\left(24.6 - 2.8\right) \\
&= (1.58)(21.8) \\
&= 34.4\ \text{kW}
\end{aligned}
$$

Finally, effectiveness:

$$
\begin{aligned}
\varepsilon
&= \frac{\dot{Q}_{HX}}{\dot{Q}_{\max}} \\
&= \frac{12}{34.4} \\
&= 0.349 \\
&\approx 0.35
\end{aligned}
$$


**5. Conclusion**

In this portfolio, the Interface Heat Exchanger (IFHX) was modeled as a steady-flow, two-stream heat exchanger that transfers waste heat from the ISS internal MTL water loop to the external ammonia loop. Using a representative operating point of $\dot{Q}{HX}=12\ \text{kW}$, the energy balance predicts that the water stream cools from $T{w,in}=24.6^\circ\text{C}$ to $T_{w,out}=17^\circ\text{C}$, while the ammonia warms from $T_{a,in}=2.8^\circ\text{C}$ to $T_{a,out}\approx 5.3^\circ\text{C}$, which matches the expected direction of heat transfer and gives physically reasonable temperature changes for multi-kilowatt heat removal. To summarize IFHX performance with a single “efficiency-like” metric, I used the heat exchanger effectiveness definition $\varepsilon=\dfrac{\dot{Q}{HX}}{\dot{Q}{\max}}=\dfrac{\dot{Q}{HX}}{C{\min}\left(T_{w,in}-T_{a,in}\right)}$, and the result $\varepsilon\approx 0.35$ shows that under these inlet conditions and flow rates, the IFHX achieves about 35% of the theoretical maximum heat transfer possible, highlighting how the device performance is limited mainly by the smaller heat capacity rate stream and by the available temperature difference between the internal water and external ammonia.