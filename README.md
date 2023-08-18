# airfoil-Lift

This project estimates the lift force per unit wingspan acting on an airfoil (NACA 23012 12%)[^1] using the Bernoulli principle.
![NACA 23012 12%](naca23012%20(1).gif) 

## Model
For this project, the Bernoulli principle is being used to determine the lift force. The principle states that the difference in the velocity of fluid flowing over the upper and lower surfaces of the airfoil generates a pressure difference between the two surfaces. As a result, the airfoil experiences lift.  

The lift force per unit wingspan (span) of the airfoil can be estimated using the following equation:

Lift per unit span = 0.5  * air_density * velocity^2 * lift_coefficient * chord_length

= dynamic_pressure * lift_coefficient * chord_length

where dynamic pressure = 0.5 * air_density * velocity^2; It is a measure of the force exerted by a fluid due to its motion on a surface. 
Wingspan is the length of the lateral extent of the airfoil.

## Parameters
The estimation of lift per unit wingspan requires the direct/indirect consideration of several factors such as,
1. **Lift coefficient**: This is a dimensionless quantity which is representative of the aerodynamical parameters of the airfoil. It is generally estimated experimentally for specific airfoils in wind tunnels. In this project, non-uniform empirical data has been obtained[^2]. The values for lift coefficient chosen are for the above mentioned airfoil, for a fixed angle of attack (zero degrees), fixed Mach number and varying values of the Reynolds Number(Re).
2. **Chord length**: It represents the horizontal length of the cross section of the airfoil. For this particular airfoil, the value is taken to be 0.1m taking into account the parameters chosen while obtaining the empirical data for the lift coefficient.
3. **Air density**: The density of air decreases with increase in elevation from sea level (altitude). Here, the air density is being computed using the corresponding values of ambient temperature and pressure for the chosen altitude obtained from the International Standard Atmosphere (ISA) data.
4. **Velocity**: It refers to the relative velocity of the airfoil with respect to the wind speed. It is also known as true airspeed (TAS). TAS is measured using an instrument called Pitot tube. The change in the liquid column height inside the Pitot tube is used to measure the TAS.

   TAS = sqrt(2 * g * (magnitude of change in liquid column height) * liquid_density / air_density)
6. **Liquid column height change**: This is the change in the level of top of the liquid in the column in the Pitot tube. The level of the liquid changes with changing TAS.
7. **Reynolds Number**: It is used to characterise the type of flow of a fluid over a surface. The value of Reynolds number may indicate if a flow regime is laminar or turbulent or a transition between the two. This gives information about the behaviour of streamlines in the flow. The empirical data obtained[^2] points to the variation of the lift coefficient for various values of Reynolds number. It is calculated as follows:
   Reynolds number = air_density * TAS * chord_length / dynamic viscosity
8. **Dynamic viscosity**: It is a quantitity used to characterise the resistance to flow of a fluid under an applied force. It is mathematically expressed as,
   
   Dynamic viscosity (mu) = Shear stress / Shear rate
   
   where shear stress is the force applied on the fluid per unit area and shear rate is the velocity gradient of fluid          perpendicular to the fluid flow direction. For the sake of simplicity, this velocity gradient has been considered to be a    constant value. However, the dependence of dynamic viscosity on ambient temperature has been taken into account since the    former depends strongly on temperature. The Sutherland model has been used to calculate dynamic viscosity.

   Dynamic viscosity (mu) = mu_ref * (T_ref + S) / (T + S) * (T/T_ref)^1.5
   
   where mu_ref is the dynamic viscosity at the reference temperature (T_ref = 273.15 K) and
   S is the Sutherland constant determined experimentally for various gases


## Conditions

Elevation of airfoil above sea level = 10 m    

Ambient Temperature (ISA)            = 281.65 K   

Ambient Pressure (ISA)               = 88375.17 N/m^-2

Liquid density in Pitot tube column  = 1000 kg*m^-3

Angle of attack                      = 0 degrees

## Inputs
The inputs and their ranges are:
-	`ambientTemperature`:
-	`ambientPressure`   :
-	`chordLength`       :
-	`deltaColumnHeight` :

The empirical data[^2]  

## Outputs


[^1]: https://m-selig.ae.illinois.edu/ads/afplots/naca23012.gif
[^2]: http://airfoiltools.com/airfoil/details?airfoil=naca23012-il
