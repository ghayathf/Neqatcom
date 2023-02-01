# Neqatcom
create table GP_Role
(
ID int GENERATED BY DEFAULT AS IDENTITY PRIMARY KEY,
Name VARCHAR2(20)
);

create table GP_UUser
(
ID int GENERATED BY DEFAULT AS IDENTITY PRIMARY KEY,
FirstName VARCHAR2(20),
LastName VARCHAR2(20),
Email VARCHAR2(20),
password VARCHAR2(20),
phoneNum Number,
Address VARCHAR2(20),
RoleID int,
CONSTRAINT GP_RoleID11_fk FOREIGN KEY (RoleID) REFERENCES GP_Role(ID),
Image_Path VARCHAR2(150)
);





CREATE TABLE GP_Loan
(
ID int GENERATED BY DEFAULT AS IDENTITY PRIMARY KEY,
NumOfProducts NUMBER,
Total NUMBER
);
create table GP_loanee
( NationalNumber Number primary key,
DateOfBirth DATE,
Salary NUMBER,
NumOfFamily NUMBER,
JobAddress VARCHAR2(35 CHAR),
CreditScore NUMBER,
userID int,
CONSTRAINT userID3_fk  FOREIGN KEY(userID) REFERENCES GP_UUser(ID)
);
create table GP_LoanLoanee
(ID int GENERATED BY DEFAULT AS IDENTITY PRIMARY KEY,
loanID int,
CONSTRAINT loanID3_fk  FOREIGN KEY(loanID) REFERENCES GP_Loan(ID),
NationalNumberFK number,
CONSTRAINT NationalNumber1_fk  FOREIGN KEY(NationalNumberFK) REFERENCES GP_loanee(NationalNumber),
status number,
BeginDate Date
);
create table GP_LCategory
(ID int GENERATED BY DEFAULT AS IDENTITY PRIMARY KEY,
Name VARCHAR2(20)
);
create table GP_lenderStore 
( commercialRegister Number primary key,
userID int,
CONSTRAINT userID4_fk  FOREIGN KEY(userID) REFERENCES GP_UUser(ID),
CategoryID number,
CONSTRAINT CategoryID1_fk  FOREIGN KEY(CategoryID) REFERENCES GP_LCategory(ID)
);
create table GP_PCategory
(ID int GENERATED BY DEFAULT AS IDENTITY PRIMARY KEY,
Name VARCHAR2(20)و
percentageSale number
);
create table GP_Product
(  
ID int GENERATED BY DEFAULT AS IDENTITY PRIMARY KEY,
ProductName VARCHAR2(35),
price Number,
availabilityProduct number,
MonthlyAmount number,
CategoryID number,
CONSTRAINT CategoryID2_fk  FOREIGN KEY(CategoryID) REFERENCES GP_PCategory(ID)
);
create table GP_ProductLoan
(ID int GENERATED BY DEFAULT AS IDENTITY PRIMARY KEY,
loanID int,
CONSTRAINT loanIDGP_fk  FOREIGN KEY(loanID) REFERENCES GP_Loan(ID),
ProductID number,
CONSTRAINT ProductIDGP_fk  FOREIGN KEY(ProductID) REFERENCES GP_Product(ID)
);
create table GP_ProductStore
(ID int GENERATED BY DEFAULT AS IDENTITY PRIMARY KEY,
LenderStoreID number,
CONSTRAINT LenderStoreID1_fk  FOREIGN KEY(LenderStoreID) REFERENCES GP_lenderStore(commercialRegister),
ProductID number,
CONSTRAINT ProductIDGP1_fk  FOREIGN KEY(ProductID) REFERENCES GP_Product(ID)
);
