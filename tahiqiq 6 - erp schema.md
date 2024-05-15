<h2 dir="rtl">نام و نام خانوادگی: امیرحسین رحیمی بهار</h2>
<h2 dir="rtl">طراحی پایگاه داده برای یک erp</h2>
<p dir="rtl">
تهیه شده با سایت dbdiagram.io
  <img src="https://raw.githubusercontent.com/amirhossein01r/tahqiqha/main/images/erp-schema-img.png" />
  <br>
مواردی مهم از شِما:<br>
در payroll فقط پرداختی ها به کارمندان ثبت می شود. در این جدول grosspay حقوق ناخالص، deductions کسورات و netpay حقوق خالص است.<br>
در جدول هایی که expense دارند سازوکار نگه داری اطلاعات مربوط به هزینه ها پیاده سازی شده است. این هزینه ها از پرداخت حقوق جداهستند. برای مثال هزینه اجاره هتل برای قرار کاری توسط کارمند. فیلد totalamount جمع هزینه های amount را نشان می دهد<br>
در جدول employees اطلاعات مربوط به کارمندان و در departments اطلاعات مربوط به دپارتمان ها نگه داری می شود.<br>
نکته نهایی نیز این است طبق چیزی که متوجه شدم erp ها معمولا طوری طراحی می شوند که بتوانند چندین موضوع و حوزه مختلف را پوشش دهند. در همین erp ساده سعی در ترکیب دو بخش انسانی و مالی شده است. <br>

  
کد مورد استفاده برای ساخت شِما:<br>
  
```
Table Employees {
    EmployeeID INT [pk, increment]
    FirstName VARCHAR(50)
    LastName VARCHAR(50)
    Email VARCHAR(100) [unique]
    DepartmentID int [ref: > Departments.DepartmentID]
    HireDate DATE
    JobTitle VARCHAR(100)
    Salary DECIMAL(10, 2)
}

Table Payroll {
    PayrollID INT [pk, increment]
    EmployeeID INT [ref: > Employees.EmployeeID]
    PayDate DATE
    GrossPay DECIMAL(10, 2)
    Deductions DECIMAL(10, 2)
    NetPay DECIMAL(10, 2)
}

Table ExpenseCategories {
    CategoryID INT [pk, increment]
    CategoryName VARCHAR(100) [unique]
}

Table ExpenseReports {
    ReportID INT [pk, increment]
    EmployeeID INT [ref: > Employees.EmployeeID]
    ReportDate DATE
    TotalAmount DECIMAL(10, 2)
    Status VARCHAR(50)
}

Table Expenses {
    ExpenseID INT [pk, increment]
    ReportID INT [ref: > ExpenseReports.ReportID]
    CategoryID INT [ref: > ExpenseCategories.CategoryID]
    ExpenseDate DATE
    Amount DECIMAL(10, 2)
    Description TEXT
}


Table Departments {
  DepartmentID INT [pk, increment]
  DepartmentName VARCHAR(50)
}
```

</p>
