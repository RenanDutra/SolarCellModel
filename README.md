# SolarCellModel
An algorithm to create a plot based on data from solarcell datasheet.

Indroduction:
A solar cell can be modeled using a simple circuit. This circuit has 4 components, a diode, 2 resistors and an current source. With this circuit, by kirchhoff's law we get the     following equation:

    I = Iph - I0*(e^((-q*(V+I*Rs))/(n*k*T0))-1) -((V+I*Rs)/(Rp))

On this equation, we have 4 unknowns, Rp, Rs, I0 and n. The main idea is to randomize this 4 values, choose a range for V, than iterate for every value of V, than compare the  results with the values from the datasheet (Isc, Voc, MPP,Impp and Vmpp) calculating than error. Finally we calculate tha mean error, if it's not aceptable, we choose new values and keep doing this until for x number of iterations. The results here will be translated to matlab when everything is over.

1st iteration:

The main question here is how to make the iterations, i'm probably going for machine learning first, so i need to:

   * Get data from Orcad scv export and open it with matplotlib (just trying to find out how thing work)
   * Take my solar cell equation, than choose the start values for my 4 variables and also the range for V(from 0 to some number)
   * Learn how machine learning works than create some initial model

2nd iteration

After trying the first iteration, i discovered that machine learning is not the best way to solve the problem, best option should be using matlab optimization tools or using a simple brute force, in this case, i will try brute forcing with P.O algorithm for the mpp calculation, than compare with the results from matlab. I will choose a step size for each variable, with this, i will have 4 loops in which i will calculate Isc, Voc and use P.O to calculate the mpp(this is realy cpu intensive)

    * Choose the step size for the iterations
    * Try not to blow up my PC with the P.O
