---
title: "R Data Analytics for Excel Users: Part 1"
date: 2023-11-11T11:18:24+06:00
draft: false
tags:
- Tutorials
- Data-Analytics
- R-programming
- Excel
---
When I was young, I used to think excel to be a jail made of white bricks and black bars and tried to avoid it at any cost. I grew little old and come to know Excel indeed is a jail. But it is a jail that one can use to imprison almost anything that they are afraid of. I imprisoned my academic results and planned how to improve with Excel. I used it for valuation of publicly traded company shares, my monthly family budget. Almost every report for my office. 

Now in this tutorial I'm trying to understand R programming using my experience with R. 

Let's begin our discussion with data formats in R.


### Excel Data formats

![Excel Data Formats](https://i.imgur.com/EEoLkQT.png)


<br>

If we type in any value to an Excel cell and then press `Cntrl + 1` we will get the "Format Cells" window and it will indicate the data format for the cell.

### Frequently Used R Data Types


```{r}
# Numeric (Numbers):
A2 = 132.00
class(A2)

# Character (text):
A3 = as.Date("2023-10-23")
class(A3)

# Time:
A4 = as.POSIXct("14:30:00", format = "%H:%M:%S")
class(A4)

# Character (text):
A5 = "Tarif"
class(A5)


# True or False Boolean (Logical):
A6 = TRUE
class(A6)


```


### Excel Data Structure: Named Ranges (Singe Column)

We can create named ranges in Excel. Its a very simple data structure. By this we can add a name to any specific cell or a range of cells. For this example we are going to see a single-column named range.

![Excel-Named-Ranges](https://i.imgur.com/UE9T8HO.png)

<br>
We can see that A1 to A7 cells are named as EmployeeSalary.

Now if we want to check the total of EmployeeSalary. We can use the SUM() function like `SUM(EmployeeSalary)` in any of the blank cell and get the result. In the same way we can use `COUNT(EmployeeSalary)`, `MAX(EmployeeSalary)`, `MIN(EmployeeSalary)` etc.



![Applying-Functions-On-Named-Ranges](https://i.imgur.com/ROidN75.png)

### Vector in R

We are saving the same data as a vector in R. 

A vector is a one-dimensional data structure. One-dimensional means it can be thought as a single column or single row but not both. So it's perfect for the named range we created in Excel.

```{r}
EmployeeSalary = c(20000,30000,40000,25000,35000,75000,150000)

mean(EmployeeSalary)

max(EmployeeSalary)

min(EmployeeSalary)
```

We can see that we got the exact same result almost in an identically similar way in R and Excel.
<br>

### Matrix in Excel and R
Matrix is a two-dimensional data structure. Two-dimensional means it has a row and a column. It can hold elements of the same data type.

We can create matrix with three rows and three colums in excel like this, and give it a name (via named range feature):


![Matrix_A](https://i.imgur.com/LshgQDC.png)

<br>


This is another matrix:

![Matrix_B](https://i.imgur.com/heSPTCH.png)

<br>

Now we can simply subtract Matrix_A from Matrix_B and get the following result:

![Matrix Substraction in Excel](https://i.imgur.com/k4Bw51u.png)

<br>

Now we are going to do the same thing using R. First let's create Matrix_A:

```{r}
# Create a 3x3 matrix with the given values
Matrix_A = matrix(c(20, 10, 15, 21, 11, 16, 22, 12, 17), nrow = 3, byrow = TRUE)

# Print the matrix
print(Matrix_A)

View((Matrix_A))

# Create a 3x3 matrix with the given values
Matrix_B = matrix(c(25, 15, 20, 26, 16, 21, 27, 17, 22), nrow = 3, byrow = TRUE)

# Print the matrix
print(Matrix_B)

```

If we see the code to create a matrix carefully, we can see the matrix function is just re-arranging a vector `c(25, 15, 20, 26, 16, 21, 27, 17, 22)` in rows and columns with these `nrow = 3, byrow = TRUE` commands.

<br>

Now let's subtract Matrix_A from Matrix_B

```{r}
# Perform matrix subtraction
Result_Matrix = Matrix_B - Matrix_A

# Print the result
View(Result_Matrix)
```

Here again we can see that the process of R is almost identical to that of Excel.

### Excel Tables and R Data Frames

First let's look at this table for number of courses some faculty members taken in 2023.

![Courses_By_Faculty](https://i.imgur.com/ckgxVtB.png)

<br>

We can store the same data with a Data Frame in R.

```{r}
# Create the data frame "Courses_By_Faculty"
Courses_By_Faculty = data.frame(
  FacultyID = c(1001, 1002, 1003, 1004, 1005),
  FacultyName = c("Farzana Lalarukh", "Enamul Huda", "Jakiul Alam Chowdhury", "Sajib Hosen", "Mahmub Uddin Chowdhury"),
  Designation = c("Associate Professor", "Asst. Professor", "Professor", "Asst. Professor", "Professor"),
  Courses_2023 = c(3, 4, 5, 7, 2)
  
)

# Print the data frame
print(Courses_By_Faculty)
```

Again, if we look into the codes to create data frame we can see **just like matrices, vectors are the building blocks for data frames.**

Let's create some simple matrix:
```{r}
# Matrix by Row
matrix_By_Row = matrix(c(1:9), nrow = 3, byrow =TRUE)
print(matrix_By_Row)

# Matrix by Column
matrix_By_Column = matrix(c(1:9), nrow = 3, byrow =FALSE)
print(matrix_By_Column)

```
### (To be continued)

