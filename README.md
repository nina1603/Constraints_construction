This repository contains tools for the obstacle detection using data from LIDaR point clouds and construction of inequality restrictions which is necessary for constraints minimization.

All the tools are concentrated in the Inequations() class. On the initialization stage it may take either the array of arrays of corners' coordinates for each figure or the number of obstacles to generate if we want to simulate the environment. It can also not take any argument at all and create a simple example environment.

When we're calling the instance of this class, the following process is performed: 
\begin{itemize}
    \item for each figure we obtain the line equations for each of its side. We save a line as a set of its coefficients in order to further pass it to the main function. The set looks as following:
    $$
    [(y_2 - y_1), -(x_2 - x_1), (x_2 y_1 - x_1 y_2)]
    $$
    \item after that, we turn equations into inequations by checking the half of the space in which the rest of the figure is contained. Note, this only works for the convex figures
    \item $get_figure_inequations()$ unites these inequations for all the figures \item and finally, these coefficients for each side of each figures are passed into $get\_constraints()$ function which takes the combination of them in the format of maximum of the minimums for each figure and returns the required function describing the area in which an agent can move.
\end{itemize} 
We can also visualize the results in order to check that we're doing everything correctly. For this purpose, $test_constraints()$ function samples the points and marks them whether they are in the permitted area or not. With the opportunity to see the contours of the obstacles one can easily assess if the method is actually working.
