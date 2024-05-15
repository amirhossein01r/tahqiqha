[ https://github.com/amirhossein01r/onlineshop-schema/ - ریپوزیتوری مربوط ]
<h2 dir="rtl">نام و نام خانوادگی: امیرحسین رحیمی بهار</h2>
<h2 dir="rtl">طراحی پایگاه داده برای یک فروشگاه</h2>
<p dir="rtl">
تهیه شده با سایت dbdiagram.io
  <img src="https://raw.githubusercontent.com/amirhossein01r/tahqiqha/main/images/onlineshop-schema-img.png" />
  <br>
مواردی از شِما که گفتنشون خالی از لطف نیست:<br>
فیلد isDeleted برای پیاده سازی سافت دیلیت به کار می رود.<br>
می توان با در نظر گرفتن موارد استفاده، بجای integer از guid در فیلد های id و یا از نوع داده های  دیگری در فیلدهای مربوط به قیمت استفاده کرد.<br>
فیلد status در orders برای اطلاع از وضعیت هایی نظیر - تحویل شده به پست، تحویل گرفته شده توسط مشتری و ... - باشد. همچنین فیلد status در shoppingcart  نمایش دهنده وضعیت محصول در سبدخرید را نمایش می دهد؛ این وضعیت می تواند - حذف شده، فعال، خریدشده و ... - باشد.<br>
تجربه حرفه ای در ساخت پایگاه داده ندارم : )
<br><br><br><br>
کد مورد استفاده برای ساخت شِما:<br>
  
```
Table Users {
  ID integer [primary key]
  Username varchar(32)
  Password varchar(64)
  Address nvarchar(128)
  Email varchar(255)
  Phone varchar(11)
  isDeleted bool
}

Table Categories {
  ID integer [primary key]
  Name nvarchar(64)
}

Table Products {
  ID integer [primary key]
  Name nvarchar(64)
  Description nvarchar(256)
  Price num
  StockQuantity integer
  CategoryID integer [ref: > Categories.ID]
  isDeleted bool
}

Table Orders {
  ID integer [primary key]
  UserID integer [ref: > Users.ID]
  OrderDate datetime
  TotalAmount integer
  Status varchar(16)
  IsDeleted bool
}

Table OrderDetails {
  ID integer [primary key]
  OrderID integer [ref: > Orders.ID]
  ProductID integer [ref: > Products.ID]
  Quantity integer
  Subtotal integer
  IsDeleted bool
}

Table Reviews {
  ID integer [primary key]
  UserID integer [ref: > Users.ID]
  ProductID integer [ref: > Products.ID]
  Rating integer
  Comment nvarchar(256)
  ReviewDate datetime
  IsDeleted bool
}

Table ShoppingCart {
  ID integer [primary key]
  UserID integer [ref: > Users.ID]
  ProductID integer [ref: > Products.ID]
  Quantity integer
  Status varchar(16)
  IsDeleted bool
}
```

</p>
