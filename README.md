# 2D-heat-transfer
This is a python code that can solve simple 2D heat transfer problems using finite element methods. The program stops after finding the global stiffness matrix due to time constraints. This was done as part of my finite element analysis course project and hence steps to calculate the temperature gradient haven't been implemented yet (since that wasn't necessary for the project). I will try to do that soon.

The first step is getting the geometry of the 2D sample from the user. Supports only perfect quadrilaterals and hence the order of coordinates doesn't matter.
For example, a square with coordinates (0,0), (0,2), (2,2), (2,0) can be input as x1 = 0, x2 = 0, x3 = 2, x4 = 0, y1 = 0, y2 = 0, y3 = 2, y4 = 2. The program will sort it out to match the geometry.

The second step is to generate the mesh. User can choose between a coarse, normal and fine mesh depending on the accuracy desired. The mesh generated is shown as matrices and also the total number of elements is displayed.

Next step is to specify the type of element to be used for the analysis. Four node isoparametric element has been used here. The program calculates the shape functions and displays the derivatives of the shape functions. Depending on the 'k' value used the program then returns the k small stiffness matrices.

The program then creates the final stiffness matrix. To do this, the program first calculates x(s,t) and y(s,t), followed by the Jacobian matrix, its inverse and determinant, the 'B' matrix and transpose of 'B' matrix.

Finally, depending on the type of element used, the stiffness matrix is calculated by integrating the corresponding equation. The math used here is complex to explain but people with a finite element background can easily understand the calculations. The values of J, J inversen J determinant, B, B transpose and k small matrices calculated in the previous steps are substituted in the stiffness matrix equation to calculate Ke (K matrix for that particular element). Depending on the mesh type chosen and the number of elements that come with it, an equal number of K matrices are generated. These are called element stiffness matrices. The next step is to split the row and column values of these element stiffness matrices and to add them to the right position in the global stiffnesss matrix. This program does this by splicing the individial element stiffness matrices into row and column elements and creating a row stiffness and column stiffness matrix from these values. Then based on the row index and column index values (these determine which value goes where in the global stiffness matrix), the final global stiffness matrix is assembled.

The program incorporates code to get the temperature boundary conditions from the user but the program stops before that. Calculating the global stiffness matrix is the final output of this program.
