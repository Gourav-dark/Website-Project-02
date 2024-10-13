-- User Roles
CREATE TABLE User_Roles (
    Id INT PRIMARY KEY IDENTITY(1,1),
    Role_Name VARCHAR(50) NOT NULL, -- e.g., Admin, Customer, Supplier
    Created_At DATETIME DEFAULT GETDATE(),
    Updated_At DATETIME NULL
);

-- Users
CREATE TABLE Users (
    Id INT PRIMARY KEY IDENTITY(1,1),
    Role_Id INT,
    Full_Name VARCHAR(100) NULL,
    Email VARCHAR(100) UNIQUE,
    Phone_Number VARCHAR(15) UNIQUE,
    Status VARCHAR(20) CHECK (Status IN ('inactive', 'active', 'blocked')) DEFAULT 'inactive',
    Phone_Verified_At DATETIME NULL,
    Email_Verified_At DATETIME NULL,
    Created_At DATETIME DEFAULT GETDATE(),
    Updated_At DATETIME NULL,
    FOREIGN KEY (Role_Id) REFERENCES User_Roles(Id)
);

-- Verification Codes
CREATE TABLE Verification_Codes (
    Id INT PRIMARY KEY IDENTITY(1,1),
    User_Id INT,
    Code VARCHAR(10),
    Verification_Type VARCHAR(20) CHECK (Verification_Type IN ('phone', 'email')),
    Status VARCHAR(20) CHECK (Status IN ('verified', 'not_verified')),
    Created_At DATETIME DEFAULT GETDATE(),
    Updated_At DATETIME NULL,
    FOREIGN KEY (User_Id) REFERENCES Users(Id)
);

-- Categories for Products
CREATE TABLE Categories (
    Id INT PRIMARY KEY IDENTITY(1,1),
    Category_Name VARCHAR(100) NOT NULL,
    Status VARCHAR(20) CHECK (Status IN ('active', 'inactive')) DEFAULT 'active',
    Created_At DATETIME DEFAULT GETDATE(),
    Updated_At DATETIME NULL
);

-- Products
CREATE TABLE Products (
    Id INT PRIMARY KEY IDENTITY(1,1),
    Name VARCHAR(100) NOT NULL,
    Description TEXT NULL,
    Price DECIMAL(10, 2) NOT NULL,
    Category_Id INT,
    Stock INT DEFAULT 0,
    Status VARCHAR(20) CHECK (Status IN ('active', 'inactive')) DEFAULT 'active',
    Created_At DATETIME DEFAULT GETDATE(),
    Updated_At DATETIME NULL,
    FOREIGN KEY (Category_Id) REFERENCES Categories(Id)
);

-- Product Images
CREATE TABLE Product_Images (
    Id INT PRIMARY KEY IDENTITY(1,1),
    Product_Id INT,
    Image_URL TEXT NOT NULL,
    Status VARCHAR(20) CHECK (Status IN ('active', 'inactive')) DEFAULT 'active',
    Created_At DATETIME DEFAULT GETDATE(),
    Updated_At DATETIME NULL,
    FOREIGN KEY (Product_Id) REFERENCES Products(Id)
);

-- Suppliers
CREATE TABLE Suppliers (
    Id INT PRIMARY KEY IDENTITY(1,1),
    Name VARCHAR(100) NOT NULL,
    Contact_Name VARCHAR(100) NULL,
    Email VARCHAR(100) UNIQUE,
    Phone_Number VARCHAR(15) UNIQUE,
    Address TEXT NOT NULL,
    City VARCHAR(100) NOT NULL,
    State VARCHAR(100) NOT NULL,
    Country VARCHAR(100) NOT NULL,
    Postal_Code VARCHAR(10) NOT NULL,
    Status VARCHAR(20) CHECK (Status IN ('active', 'inactive')) DEFAULT 'active',
    Created_At DATETIME DEFAULT GETDATE(),
    Updated_At DATETIME NULL
);

-- Product Suppliers Relationship
CREATE TABLE Product_Suppliers (
    Id INT PRIMARY KEY IDENTITY(1,1),
    Product_Id INT,
    Supplier_Id INT,
    Created_At DATETIME DEFAULT GETDATE(),
    Updated_At DATETIME NULL,
    FOREIGN KEY (Product_Id) REFERENCES Products(Id),
    FOREIGN KEY (Supplier_Id) REFERENCES Suppliers(Id)
);

-- Carts
CREATE TABLE Carts (
    Id INT PRIMARY KEY IDENTITY(1,1),
    User_Id INT,
    Created_At DATETIME DEFAULT GETDATE(),
    Updated_At DATETIME NULL,
    FOREIGN KEY (User_Id) REFERENCES Users(Id)
);

-- Cart Items
CREATE TABLE Cart_Items (
    Id INT PRIMARY KEY IDENTITY(1,1),
    Cart_Id INT,
    Product_Id INT,
    Quantity INT NOT NULL,
    Created_At DATETIME DEFAULT GETDATE(),
    Updated_At DATETIME NULL,
    FOREIGN KEY (Cart_Id) REFERENCES Carts(Id),
    FOREIGN KEY (Product_Id) REFERENCES Products(Id)
);

-- Orders
CREATE TABLE Orders (
    Id INT PRIMARY KEY IDENTITY(1,1),
    User_Id INT,
    Total_Amount DECIMAL(10, 2),
    Discount_Amount DECIMAL(10, 2),
    Payment_Mode VARCHAR(30) CHECK (Payment_Mode IN ('net banking', 'UPI', 'COD', 'Debit/Credit Card')),
    Payment_Status VARCHAR(20) CHECK (Payment_Status IN ('paid', 'not paid')),
    Status VARCHAR(20) CHECK (Status IN ('placed', 'accepted', 'shipped', 'delivered', 'cancelled')),
    Created_At DATETIME DEFAULT GETDATE(),
    Updated_At DATETIME NULL,
    FOREIGN KEY (User_Id) REFERENCES Users(Id)
);

-- Order Items
CREATE TABLE Order_Items (
    Id INT PRIMARY KEY IDENTITY(1,1),
    Order_Id INT,
    Product_Id INT,
    Quantity INT NOT NULL,
    Price DECIMAL(10, 2) NOT NULL,
    Created_At DATETIME DEFAULT GETDATE(),
    Updated_At DATETIME NULL,
    FOREIGN KEY (Order_Id) REFERENCES Orders(Id),
    FOREIGN KEY (Product_Id) REFERENCES Products(Id)
);

-- Addresses
CREATE TABLE Addresses (
    Id INT PRIMARY KEY IDENTITY(1,1),
    User_Id INT,
    Address TEXT NOT NULL,
    Locality VARCHAR(100),
    City VARCHAR(100),
    State VARCHAR(100),
    Country VARCHAR(100),
    Postal_Code VARCHAR(10),
    Created_At DATETIME DEFAULT GETDATE(),
    Updated_At DATETIME NULL,
    FOREIGN KEY (User_Id) REFERENCES Users(Id)
);

-- Payment Transactions
CREATE TABLE Payment_Transactions (
    Id INT PRIMARY KEY IDENTITY(1,1),
    Order_Id INT,
    Amount DECIMAL(10, 2),
    Payment_Mode VARCHAR(30) CHECK (Payment_Mode IN ('net banking', 'UPI', 'COD', 'Debit/Credit Card')),
    Payment_Response TEXT,
    Payment_Status VARCHAR(20) CHECK (Payment_Status IN ('success', 'failed')),
    Created_At DATETIME DEFAULT GETDATE(),
    Updated_At DATETIME NULL,
    FOREIGN KEY (Order_Id) REFERENCES Orders(Id)
);

-- Discounts and Offers
CREATE TABLE Offers (
    Id INT PRIMARY KEY IDENTITY(1,1),
    Coupon_Code VARCHAR(20) UNIQUE,
    Discount_Type VARCHAR(20) CHECK (Discount_Type IN ('fixed', 'percentage')),
    Discount_Value DECIMAL(10, 2),
    Max_Discount_Amount DECIMAL(10, 2),
    Start_Date DATE,
    End_Date DATE,
    Description TEXT,
    Status VARCHAR(20) CHECK (Status IN ('active', 'inactive')),
    Created_At DATETIME DEFAULT GETDATE(),
    Updated_At DATETIME NULL
);

-- Order Discounts
CREATE TABLE Order_Discounts (
    Id INT PRIMARY KEY IDENTITY(1,1),
    Order_Id INT,
    Offer_Id INT,
    Created_At DATETIME DEFAULT GETDATE(),
    Updated_At DATETIME NULL,
    FOREIGN KEY (Order_Id) REFERENCES Orders(Id),
    FOREIGN KEY (Offer_Id) REFERENCES Offers(Id)
);
