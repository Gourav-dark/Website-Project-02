USE [InstaFoodDb]
GO
/****** Object:  Table [dbo].[CartItems]    Script Date: 04-10-2024 20:31:47 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[CartItems](
	[CustomerId] [nvarchar](10) NOT NULL,
	[ProductId] [int] NOT NULL,
	[Quantity] [int] NOT NULL,
 CONSTRAINT [PK_CartItems] PRIMARY KEY CLUSTERED 
(
	[CustomerId] ASC,
	[ProductId] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[DeliveryAddresses]    Script Date: 04-10-2024 20:31:47 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[DeliveryAddresses](
	[Id] [int] IDENTITY(1,1) NOT NULL,
	[Phone] [nvarchar](10) NOT NULL,
	[Street] [nvarchar](max) NULL,
	[LandMark] [nvarchar](max) NULL,
	[City] [nvarchar](50) NULL,
	[State] [nvarchar](50) NULL,
	[PostalCode] [nvarchar](10) NULL,
	[CustomerId] [nvarchar](10) NOT NULL,
 CONSTRAINT [PK_DeliveryAddresses] PRIMARY KEY CLUSTERED 
(
	[Id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY] TEXTIMAGE_ON [PRIMARY]
GO
/****** Object:  Table [dbo].[OrderDetails]    Script Date: 04-10-2024 20:31:47 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[OrderDetails](
	[OrderId] [nvarchar](10) NOT NULL,
	[ProductId] [int] NOT NULL,
	[Quantity] [int] NOT NULL,
 CONSTRAINT [PK_OrderDetails] PRIMARY KEY CLUSTERED 
(
	[OrderId] ASC,
	[ProductId] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Orders]    Script Date: 04-10-2024 20:31:47 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Orders](
	[OrderId] [nvarchar](10) NOT NULL,
	[CustomerId] [nvarchar](10) NOT NULL,
	[OrderDate] [date] NOT NULL,
	[OrderTime] [time](7) NOT NULL,
	[TotalCost] [real] NOT NULL,
	[OrderStatusId] [int] NOT NULL,
 CONSTRAINT [PK_Orders] PRIMARY KEY CLUSTERED 
(
	[OrderId] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[OrderStatus]    Script Date: 04-10-2024 20:31:47 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[OrderStatus](
	[OrderStatusId] [int] IDENTITY(1,1) NOT NULL,
	[Status] [nvarchar](max) NOT NULL,
 CONSTRAINT [PK_OrderStatus] PRIMARY KEY CLUSTERED 
(
	[OrderStatusId] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY] TEXTIMAGE_ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Products]    Script Date: 04-10-2024 20:31:47 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Products](
	[ProductId] [int] IDENTITY(1,1) NOT NULL,
	[ProductName] [nvarchar](200) NOT NULL,
	[ProductDescription] [nvarchar](max) NULL,
	[UnitPrice] [real] NOT NULL,
	[ProductPicture] [nvarchar](max) NULL,
	[IsAvailable] [bit] NOT NULL,
	[NonVeg] [bit] NOT NULL,
 CONSTRAINT [PK_Products] PRIMARY KEY CLUSTERED 
(
	[ProductId] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY] TEXTIMAGE_ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Users]    Script Date: 04-10-2024 20:31:47 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Users](
	[UserId] [nvarchar](10) NOT NULL,
	[Name] [nvarchar](100) NOT NULL,
	[Email] [nvarchar](100) NOT NULL,
	[Password] [nvarchar](max) NOT NULL,
	[Role] [nvarchar](10) NOT NULL,
 CONSTRAINT [PK_Users] PRIMARY KEY CLUSTERED 
(
	[UserId] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY] TEXTIMAGE_ON [PRIMARY]
GO
INSERT [dbo].[CartItems] ([CustomerId], [ProductId], [Quantity]) VALUES (N'3b21dce7', 1018, 3)
GO
SET IDENTITY_INSERT [dbo].[DeliveryAddresses] ON 
GO
INSERT [dbo].[DeliveryAddresses] ([Id], [Phone], [Street], [LandMark], [City], [State], [PostalCode], [CustomerId]) VALUES (1, N'8945435653', N'Street', N'Land', N'City2', N'State', N'763498', N'4c5bf725')
GO
INSERT [dbo].[DeliveryAddresses] ([Id], [Phone], [Street], [LandMark], [City], [State], [PostalCode], [CustomerId]) VALUES (2, N'9873443434', N'Street', N'Hotel', N'Pune', N'MP', N'876536', N'10831125')
GO
INSERT [dbo].[DeliveryAddresses] ([Id], [Phone], [Street], [LandMark], [City], [State], [PostalCode], [CustomerId]) VALUES (3, N'9873443434', N'Magacity Road', N'Taj Hotel', N'Kolkata', N'West Bengal', N'700052', N'3b21dce7')
GO
SET IDENTITY_INSERT [dbo].[DeliveryAddresses] OFF
GO
INSERT [dbo].[OrderDetails] ([OrderId], [ProductId], [Quantity]) VALUES (N'029aa498', 1014, 5)
GO
INSERT [dbo].[OrderDetails] ([OrderId], [ProductId], [Quantity]) VALUES (N'029aa498', 1024, 3)
GO
INSERT [dbo].[OrderDetails] ([OrderId], [ProductId], [Quantity]) VALUES (N'105dc942', 1011, 5)
GO
INSERT [dbo].[OrderDetails] ([OrderId], [ProductId], [Quantity]) VALUES (N'105dc942', 1015, 1)
GO
INSERT [dbo].[OrderDetails] ([OrderId], [ProductId], [Quantity]) VALUES (N'105dc942', 1017, 6)
GO
INSERT [dbo].[OrderDetails] ([OrderId], [ProductId], [Quantity]) VALUES (N'105dc942', 1018, 7)
GO
INSERT [dbo].[OrderDetails] ([OrderId], [ProductId], [Quantity]) VALUES (N'21968202', 1017, 3)
GO
INSERT [dbo].[OrderDetails] ([OrderId], [ProductId], [Quantity]) VALUES (N'229077d7', 1014, 3)
GO
INSERT [dbo].[OrderDetails] ([OrderId], [ProductId], [Quantity]) VALUES (N'229077d7', 1017, 3)
GO
INSERT [dbo].[OrderDetails] ([OrderId], [ProductId], [Quantity]) VALUES (N'229077d7', 1018, 3)
GO
INSERT [dbo].[OrderDetails] ([OrderId], [ProductId], [Quantity]) VALUES (N'229077d7', 1020, 3)
GO
INSERT [dbo].[OrderDetails] ([OrderId], [ProductId], [Quantity]) VALUES (N'229077d7', 1024, 1)
GO
INSERT [dbo].[OrderDetails] ([OrderId], [ProductId], [Quantity]) VALUES (N'274e3b73', 1018, 2)
GO
INSERT [dbo].[OrderDetails] ([OrderId], [ProductId], [Quantity]) VALUES (N'274e3b73', 1019, 3)
GO
INSERT [dbo].[OrderDetails] ([OrderId], [ProductId], [Quantity]) VALUES (N'48b3adb5', 1019, 3)
GO
INSERT [dbo].[OrderDetails] ([OrderId], [ProductId], [Quantity]) VALUES (N'5d6a5892', 1011, 2)
GO
INSERT [dbo].[OrderDetails] ([OrderId], [ProductId], [Quantity]) VALUES (N'5d6a5892', 1012, 3)
GO
INSERT [dbo].[OrderDetails] ([OrderId], [ProductId], [Quantity]) VALUES (N'6c4fcebd', 1022, 3)
GO
INSERT [dbo].[OrderDetails] ([OrderId], [ProductId], [Quantity]) VALUES (N'809764a1', 1014, 3)
GO
INSERT [dbo].[OrderDetails] ([OrderId], [ProductId], [Quantity]) VALUES (N'809764a1', 1017, 1)
GO
INSERT [dbo].[OrderDetails] ([OrderId], [ProductId], [Quantity]) VALUES (N'95556999', 1012, 1)
GO
INSERT [dbo].[OrderDetails] ([OrderId], [ProductId], [Quantity]) VALUES (N'95556999', 1013, 1)
GO
INSERT [dbo].[OrderDetails] ([OrderId], [ProductId], [Quantity]) VALUES (N'a313fb29', 1012, 2)
GO
INSERT [dbo].[OrderDetails] ([OrderId], [ProductId], [Quantity]) VALUES (N'a313fb29', 1015, 2)
GO
INSERT [dbo].[OrderDetails] ([OrderId], [ProductId], [Quantity]) VALUES (N'a313fb29', 1017, 3)
GO
INSERT [dbo].[OrderDetails] ([OrderId], [ProductId], [Quantity]) VALUES (N'a313fb29', 1020, 6)
GO
INSERT [dbo].[OrderDetails] ([OrderId], [ProductId], [Quantity]) VALUES (N'b744d857', 1017, 3)
GO
INSERT [dbo].[OrderDetails] ([OrderId], [ProductId], [Quantity]) VALUES (N'b744d857', 1019, 2)
GO
INSERT [dbo].[OrderDetails] ([OrderId], [ProductId], [Quantity]) VALUES (N'c3dae223', 1017, 2)
GO
INSERT [dbo].[OrderDetails] ([OrderId], [ProductId], [Quantity]) VALUES (N'c3dae223', 1019, 3)
GO
INSERT [dbo].[OrderDetails] ([OrderId], [ProductId], [Quantity]) VALUES (N'e1d55dfc', 1018, 1)
GO
INSERT [dbo].[Orders] ([OrderId], [CustomerId], [OrderDate], [OrderTime], [TotalCost], [OrderStatusId]) VALUES (N'029aa498', N'3b21dce7', CAST(N'2024-09-12' AS Date), CAST(N'19:37:27.3412324' AS Time), 1525, 2)
GO
INSERT [dbo].[Orders] ([OrderId], [CustomerId], [OrderDate], [OrderTime], [TotalCost], [OrderStatusId]) VALUES (N'105dc942', N'3b21dce7', CAST(N'2024-09-10' AS Date), CAST(N'12:02:07.2955623' AS Time), 3860, 1)
GO
INSERT [dbo].[Orders] ([OrderId], [CustomerId], [OrderDate], [OrderTime], [TotalCost], [OrderStatusId]) VALUES (N'21968202', N'10831125', CAST(N'2024-09-18' AS Date), CAST(N'10:50:02.5592958' AS Time), 450, 2)
GO
INSERT [dbo].[Orders] ([OrderId], [CustomerId], [OrderDate], [OrderTime], [TotalCost], [OrderStatusId]) VALUES (N'229077d7', N'4c5bf725', CAST(N'2024-09-16' AS Date), CAST(N'22:36:50.7179505' AS Time), 2125, 1)
GO
INSERT [dbo].[Orders] ([OrderId], [CustomerId], [OrderDate], [OrderTime], [TotalCost], [OrderStatusId]) VALUES (N'274e3b73', N'4c5bf725', CAST(N'2024-09-17' AS Date), CAST(N'09:15:06.9071222' AS Time), 890, 1)
GO
INSERT [dbo].[Orders] ([OrderId], [CustomerId], [OrderDate], [OrderTime], [TotalCost], [OrderStatusId]) VALUES (N'48b3adb5', N'3b21dce7', CAST(N'2024-09-11' AS Date), CAST(N'10:54:53.0392424' AS Time), 450, 3)
GO
INSERT [dbo].[Orders] ([OrderId], [CustomerId], [OrderDate], [OrderTime], [TotalCost], [OrderStatusId]) VALUES (N'5d6a5892', N'10831125', CAST(N'2024-09-10' AS Date), CAST(N'10:41:36.2967449' AS Time), 1040, 4)
GO
INSERT [dbo].[Orders] ([OrderId], [CustomerId], [OrderDate], [OrderTime], [TotalCost], [OrderStatusId]) VALUES (N'6c4fcebd', N'4c5bf725', CAST(N'2024-09-17' AS Date), CAST(N'09:27:20.7214849' AS Time), 450, 2)
GO
INSERT [dbo].[Orders] ([OrderId], [CustomerId], [OrderDate], [OrderTime], [TotalCost], [OrderStatusId]) VALUES (N'809764a1', N'10831125', CAST(N'2024-09-11' AS Date), CAST(N'16:03:31.0077492' AS Time), 750, 6)
GO
INSERT [dbo].[Orders] ([OrderId], [CustomerId], [OrderDate], [OrderTime], [TotalCost], [OrderStatusId]) VALUES (N'95556999', N'10831125', CAST(N'2024-09-09' AS Date), CAST(N'22:59:50.1143200' AS Time), 330, 1)
GO
INSERT [dbo].[Orders] ([OrderId], [CustomerId], [OrderDate], [OrderTime], [TotalCost], [OrderStatusId]) VALUES (N'a313fb29', N'4c5bf725', CAST(N'2024-09-10' AS Date), CAST(N'00:55:54.2367236' AS Time), 1630, 1)
GO
INSERT [dbo].[Orders] ([OrderId], [CustomerId], [OrderDate], [OrderTime], [TotalCost], [OrderStatusId]) VALUES (N'b744d857', N'3b21dce7', CAST(N'2024-09-16' AS Date), CAST(N'21:50:32.3781406' AS Time), 750, 2)
GO
INSERT [dbo].[Orders] ([OrderId], [CustomerId], [OrderDate], [OrderTime], [TotalCost], [OrderStatusId]) VALUES (N'c3dae223', N'10831125', CAST(N'2024-09-16' AS Date), CAST(N'17:14:43.8147783' AS Time), 750, 5)
GO
INSERT [dbo].[Orders] ([OrderId], [CustomerId], [OrderDate], [OrderTime], [TotalCost], [OrderStatusId]) VALUES (N'e1d55dfc', N'4c5bf725', CAST(N'2024-09-17' AS Date), CAST(N'18:43:19.7148074' AS Time), 220, 1)
GO
SET IDENTITY_INSERT [dbo].[OrderStatus] ON 
GO
INSERT [dbo].[OrderStatus] ([OrderStatusId], [Status]) VALUES (1, N'Placed')
GO
INSERT [dbo].[OrderStatus] ([OrderStatusId], [Status]) VALUES (2, N'Accepted and Preparing')
GO
INSERT [dbo].[OrderStatus] ([OrderStatusId], [Status]) VALUES (3, N'Declined')
GO
INSERT [dbo].[OrderStatus] ([OrderStatusId], [Status]) VALUES (4, N'Cancelled')
GO
INSERT [dbo].[OrderStatus] ([OrderStatusId], [Status]) VALUES (5, N'Out for Delivery')
GO
INSERT [dbo].[OrderStatus] ([OrderStatusId], [Status]) VALUES (6, N'Delivered')
GO
SET IDENTITY_INSERT [dbo].[OrderStatus] OFF
GO
SET IDENTITY_INSERT [dbo].[Products] ON 
GO
INSERT [dbo].[Products] ([ProductId], [ProductName], [ProductDescription], [UnitPrice], [ProductPicture], [IsAvailable], [NonVeg]) VALUES (1011, N'Rogan Josh', N'A Kashmiri meal is incomplete without rogan josh. Made out of lamb, this aromatic dish is basically of Persian origin and is as delicious as its name.', 250, N'https://www.fabhotels.com/blog/wp-content/uploads/2016/11/Rogan-Josh-1.jpg', 1, 0)
GO
INSERT [dbo].[Products] ([ProductId], [ProductName], [ProductDescription], [UnitPrice], [ProductPicture], [IsAvailable], [NonVeg]) VALUES (1012, N'Makki-Roti and Sarso ka Saag', N'Who doesn’t love makke ki roti and sarso ka saag? Come winters and kitchens of Punjab are filled with the aroma of mustard.', 180, N'https://www.fabhotels.com/blog/wp-content/uploads/2024/01/8ce8cf5a-makki-roti-and-sarso-ka-saag.jpg:cf-webp:w-848:h-551', 1, 0)
GO
INSERT [dbo].[Products] ([ProductId], [ProductName], [ProductDescription], [UnitPrice], [ProductPicture], [IsAvailable], [NonVeg]) VALUES (1013, N'Chaach or Buttermilk', N'Chaach is a common drink consumed in almost every home in northern and central part of India.', 150, N'https://www.fabhotels.com/blog/wp-content/uploads/2024/01/66935255-chaach-or-buttermilk.jpg', 0, 0)
GO
INSERT [dbo].[Products] ([ProductId], [ProductName], [ProductDescription], [UnitPrice], [ProductPicture], [IsAvailable], [NonVeg]) VALUES (1014, N'Dal-Baati-Churma', N'This dish is a staple diet in Rajasthan. Land anywhere in the state – Udaipur, Jaipur, Jodhpur, Bikaner, you will find people having it.', 200, N'https://www.fabhotels.com/blog/wp-content/uploads/2016/11/Daal-baati-768x489-1.jpg', 1, 0)
GO
INSERT [dbo].[Products] ([ProductId], [ProductName], [ProductDescription], [UnitPrice], [ProductPicture], [IsAvailable], [NonVeg]) VALUES (1015, N'Sidu', N'A speciality from Kullu, Himachal Pradesh, Sidu is a kind of bread mostly eaten with dal or chutney.', 170, N'https://www.fabhotels.com/blog/wp-content/uploads/2016/11/hp2.jpg', 1, 0)
GO
INSERT [dbo].[Products] ([ProductId], [ProductName], [ProductDescription], [UnitPrice], [ProductPicture], [IsAvailable], [NonVeg]) VALUES (1016, N'Jhangora Kheer', N'Millets or jhangora ki kheer is a popular sweet dish in any Garhwal (in Uttarkhand) household. Its preparation is similar to the regular rice pudding except the rice is replaced by jhangora.', 160, N'https://www.fabhotels.com/blog/wp-content/uploads/2024/01/5765d049-kheer-min.jpg', 1, 0)
GO
INSERT [dbo].[Products] ([ProductId], [ProductName], [ProductDescription], [UnitPrice], [ProductPicture], [IsAvailable], [NonVeg]) VALUES (1017, N'Aloo Kachori', N'A common breakfast for North Indians especially in the state of Uttar Pradesh, aloo kachori is simply plain flour dough stuffed with lentils or potatoes with curry comprising tomatoes and potatoes.', 150, N'https://www.fabhotels.com/blog/wp-content/uploads/2016/11/KACHORI-2.jpg', 0, 0)
GO
INSERT [dbo].[Products] ([ProductId], [ProductName], [ProductDescription], [UnitPrice], [ProductPicture], [IsAvailable], [NonVeg]) VALUES (1018, N'Bhopali Kebab', N'Bhopali kebabs is a traditional recipe made out of mutton or beef. As the name goes, it’s a dish from Bhopal and hugely popular in Madhya Pradesh.', 220, N'https://www.fabhotels.com/blog/wp-content/uploads/2024/01/3d2d864d-bhopal-kebabs.jpg', 1, 0)
GO
INSERT [dbo].[Products] ([ProductId], [ProductName], [ProductDescription], [UnitPrice], [ProductPicture], [IsAvailable], [NonVeg]) VALUES (1019, N'Bafauri', N'A wonderful alternative to the oily pakoras India is used to having, bafauri is made from chickpeas but instead of frying, it is steamed.', 150, N'https://www.fabhotels.com/blog/wp-content/uploads/2016/11/Bafauri-1.jpg', 1, 0)
GO
INSERT [dbo].[Products] ([ProductId], [ProductName], [ProductDescription], [UnitPrice], [ProductPicture], [IsAvailable], [NonVeg]) VALUES (1020, N'Dosa', N'The light meal from South India that is eaten everywhere in India. Yes, we are talking about the every loved Dosa. Have it plain or with potato, it never seems to disappoint anyone.', 80, N'https://www.fabhotels.com/blog/wp-content/uploads/2016/11/dosa-1.jpg', 0, 0)
GO
INSERT [dbo].[Products] ([ProductId], [ProductName], [ProductDescription], [UnitPrice], [ProductPicture], [IsAvailable], [NonVeg]) VALUES (1021, N'Momos', N'How can we ever forget to add Momos in the list? Originally from Nepal, this dish is available at every corner of the street in the country and is loved by all of us.', 100, N'https://www.fabhotels.com/blog/wp-content/uploads/2020/01/Dumpling-food.jpg', 1, 0)
GO
INSERT [dbo].[Products] ([ProductId], [ProductName], [ProductDescription], [UnitPrice], [ProductPicture], [IsAvailable], [NonVeg]) VALUES (1022, N'Gajar ka Halwa', N'A highly popular dessert in the whole of country, Gajar ka halwa is basically grated carrots, milk, sugar and dry fruits. ', 150, N'https://www.fabhotels.com/blog/wp-content/uploads/2016/11/Gajar-ka-Halwa-1.jpg', 0, 0)
GO
INSERT [dbo].[Products] ([ProductId], [ProductName], [ProductDescription], [UnitPrice], [ProductPicture], [IsAvailable], [NonVeg]) VALUES (1024, N'Chicken Briyani', N'Chicken Briyani', 175, N'https://media.istockphoto.com/id/1333127665/photo/chicken-biryani-spicy-indian-malabar-biryani-hyderabadi-biryani-dum-biriyani-pulao-golden.jpg?s=612x612&w=0&k=20&c=63UXYPOISm8nJ8SNK79dDm0w1gY6jXzYQP0heL6fnOg=', 1, 0)
GO
INSERT [dbo].[Products] ([ProductId], [ProductName], [ProductDescription], [UnitPrice], [ProductPicture], [IsAvailable], [NonVeg]) VALUES (1029, N'Paratha', N'Paratha is another style of unleavened, whole-wheat flatbread and a quintessential Indian food. Thicker and more substantial than naan or chapati, paratha is prepared by coating the dough with ghee (a type of clarified butter) or oil and folding repeatedly, similar to making puff pastry, using a lamination technique.', 120, N'https://res.cloudinary.com/hz3gmuqw6/image/upload/c_fill,q_60,w_750,f_auto/3-paratha-canva-phpCTUMcP', 1, 0)
GO
INSERT [dbo].[Products] ([ProductId], [ProductName], [ProductDescription], [UnitPrice], [ProductPicture], [IsAvailable], [NonVeg]) VALUES (1030, N'Matar Kulcha', N'Another favorite street food from North India is matar kulcha. This simple snack consists of a soft flatbread served with spiced white pea gravy and is one of the most famous street foods in Delhi.', 200, N'https://res.cloudinary.com/hz3gmuqw6/image/upload/c_fill,q_60,w_750,f_auto/11-matar-kulcha-canva-phpiqTrzB', 1, 0)
GO
INSERT [dbo].[Products] ([ProductId], [ProductName], [ProductDescription], [UnitPrice], [ProductPicture], [IsAvailable], [NonVeg]) VALUES (1031, N'Kathi Rolls', N'Originally from Kolkata in the West Bengal state of India, kathi rolls began as a skewer-roasted kebab wrapped in paratha bread.', 250, N'https://res.cloudinary.com/hz3gmuqw6/image/upload/c_fill,q_60,w_750,f_auto/15-kathi-rolls-canva-phpE9mepi', 1, 0)
GO
INSERT [dbo].[Products] ([ProductId], [ProductName], [ProductDescription], [UnitPrice], [ProductPicture], [IsAvailable], [NonVeg]) VALUES (1032, N'Chicken 65', N'The spicy, deep-fried chicken dish appeared on the menu of the Buhari Hotel in the state of Tamil Nadu. ', 200, N'https://res.cloudinary.com/hz3gmuqw6/image/upload/c_fill,q_60,w_750,f_auto/19-chicken-65-canva-phpV0OB8z', 1, 0)
GO
INSERT [dbo].[Products] ([ProductId], [ProductName], [ProductDescription], [UnitPrice], [ProductPicture], [IsAvailable], [NonVeg]) VALUES (1033, N'Tandoori', N'An iconic food from India, dishes labeled tandoori are typically breads or meats that have been seasoned and cooked at high temperatures in a tandoor oven. Tandoori chicken is probably the most well-known dish of this style.', 350, N'https://res.cloudinary.com/hz3gmuqw6/image/upload/c_fill,q_60,w_750,f_auto/23-tandoor-canva-phpRi8NmQ', 1, 0)
GO
INSERT [dbo].[Products] ([ProductId], [ProductName], [ProductDescription], [UnitPrice], [ProductPicture], [IsAvailable], [NonVeg]) VALUES (1034, N'Kebab, Turkey', N'A dish popular across the Middle East, Kebabs are originally from Turkey. They consist of ground meat or seafood, fruits, and vegetables in some cases and are cooked on a skewer with a big fire underneath, just like a barbeque on the grill.', 300, N'https://www.holidify.com/images/cmsuploads/compressed/bacon-kebabs-13-2_20181227133457.jpg', 1, 0)
GO
SET IDENTITY_INSERT [dbo].[Products] OFF
GO
INSERT [dbo].[Users] ([UserId], [Name], [Email], [Password], [Role]) VALUES (N'10831125', N'Aman', N'aman@gmail.com', N'123455', N'Customer')
GO
INSERT [dbo].[Users] ([UserId], [Name], [Email], [Password], [Role]) VALUES (N'197e8f9f', N'Admin', N'admin@gmail.com', N'123455', N'Admin')
GO
INSERT [dbo].[Users] ([UserId], [Name], [Email], [Password], [Role]) VALUES (N'3b21dce7', N'Sachin Sharma', N'sachin@gmail.com', N'12345', N'Customer')
GO
INSERT [dbo].[Users] ([UserId], [Name], [Email], [Password], [Role]) VALUES (N'4c5bf725', N'Rohan', N'abc@gmail.com', N'12345', N'Customer')
GO
INSERT [dbo].[Users] ([UserId], [Name], [Email], [Password], [Role]) VALUES (N'a9f336b0', N'Admin2', N'admin2@gmail.com', N'12345', N'Admin')
GO
INSERT [dbo].[Users] ([UserId], [Name], [Email], [Password], [Role]) VALUES (N'ee233f66', N'Rohan', N'abcd@gmail.com', N'123456', N'Customer')
GO
ALTER TABLE [dbo].[Orders] ADD  DEFAULT ((1)) FOR [OrderStatusId]
GO
ALTER TABLE [dbo].[Products] ADD  DEFAULT (CONVERT([bit],(1))) FOR [IsAvailable]
GO
ALTER TABLE [dbo].[Products] ADD  DEFAULT (CONVERT([bit],(0))) FOR [NonVeg]
GO
ALTER TABLE [dbo].[Users] ADD  DEFAULT (N'Customer') FOR [Role]
GO
ALTER TABLE [dbo].[CartItems]  WITH CHECK ADD  CONSTRAINT [FK_CartItems_Products_ProductId] FOREIGN KEY([ProductId])
REFERENCES [dbo].[Products] ([ProductId])
ON DELETE CASCADE
GO
ALTER TABLE [dbo].[CartItems] CHECK CONSTRAINT [FK_CartItems_Products_ProductId]
GO
ALTER TABLE [dbo].[CartItems]  WITH CHECK ADD  CONSTRAINT [FK_CartItems_Users_CustomerId] FOREIGN KEY([CustomerId])
REFERENCES [dbo].[Users] ([UserId])
ON DELETE CASCADE
GO
ALTER TABLE [dbo].[CartItems] CHECK CONSTRAINT [FK_CartItems_Users_CustomerId]
GO
ALTER TABLE [dbo].[DeliveryAddresses]  WITH CHECK ADD  CONSTRAINT [FK_DeliveryAddresses_Users_CustomerId] FOREIGN KEY([CustomerId])
REFERENCES [dbo].[Users] ([UserId])
ON DELETE CASCADE
GO
ALTER TABLE [dbo].[DeliveryAddresses] CHECK CONSTRAINT [FK_DeliveryAddresses_Users_CustomerId]
GO
ALTER TABLE [dbo].[OrderDetails]  WITH CHECK ADD  CONSTRAINT [FK_OrderDetails_Orders_OrderId] FOREIGN KEY([OrderId])
REFERENCES [dbo].[Orders] ([OrderId])
ON DELETE CASCADE
GO
ALTER TABLE [dbo].[OrderDetails] CHECK CONSTRAINT [FK_OrderDetails_Orders_OrderId]
GO
ALTER TABLE [dbo].[OrderDetails]  WITH CHECK ADD  CONSTRAINT [FK_OrderDetails_Products_ProductId] FOREIGN KEY([ProductId])
REFERENCES [dbo].[Products] ([ProductId])
ON DELETE CASCADE
GO
ALTER TABLE [dbo].[OrderDetails] CHECK CONSTRAINT [FK_OrderDetails_Products_ProductId]
GO
ALTER TABLE [dbo].[Orders]  WITH CHECK ADD  CONSTRAINT [FK_Orders_OrderStatus_OrderStatusId] FOREIGN KEY([OrderStatusId])
REFERENCES [dbo].[OrderStatus] ([OrderStatusId])
ON DELETE CASCADE
GO
ALTER TABLE [dbo].[Orders] CHECK CONSTRAINT [FK_Orders_OrderStatus_OrderStatusId]
GO
ALTER TABLE [dbo].[Orders]  WITH CHECK ADD  CONSTRAINT [FK_Orders_Users_CustomerId] FOREIGN KEY([CustomerId])
REFERENCES [dbo].[Users] ([UserId])
ON DELETE CASCADE
GO
ALTER TABLE [dbo].[Orders] CHECK CONSTRAINT [FK_Orders_Users_CustomerId]
GO
