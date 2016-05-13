# 2D-heat-transfer
This is a python code that can solve simple 2D heat transfer problems using finite element methods

The first step is getting the geometry of the 2D sample from the user. Supports only perfect quadrilaterals and hence the order of coordinates doesn't matter.
For example, a square with coordinates (0,0), (0,2), (2,2), (2,0) can be input as x1 = 0, x2 = 0, x3 = 2, x4 = 0, y1 = 0, y2 = 0, y3 = 2, y4 = 2. The program will sort it out to match the geometry.

The second step is to generate the mesh. User can choose between a coarse, normal and fine mesh depending on the accuracy desired. The mesh generated is shown as matrices and also the total number of elements is displayed.

Next step is to specify the type of element to be used for the analysis. Four node isoparametric element has been used here. The program calculates the shape functions and displays the derivatives of the shape functions. Depending on the 'k' value used the program then returns the k small stiffness matrices.

The program then creates the final stiffness matrix. To do this, the program first calculates x(s,t) and y(s,t), followed by the Jacobian matrix, its inverse and determinant
