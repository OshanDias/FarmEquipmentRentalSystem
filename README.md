# FARM EQUIPMENT RENTAL MANAGEMENT SYSTEM

## Enterprise Application Development - Coursework Project


---

## 📋 PROJECT OVERVIEW

A comprehensive Farm Equipment Rental Management System for the agricultural sector. The system helps farmers rent tractors, harvesters, plows, sprayers, and seeders with automated booking, tracking, and revenue reporting.

---

## 🛠️ TECHNOLOGIES USED

- **Programming Language:** Java (JDK 17)
- **IDE:** Apache NetBeans 19
- **Database:** MySQL 8.0
- **Reporting:** Jasper Reports 6.20.0
- **Architecture:** MVC (Model-View-Controller)
- **Design Patterns:** Singleton, DAO (Data Access Object)
- **UI Theme:** Agricultural/Farm Theme (Earth tones)

---

## 📦 REQUIRED LIBRARIES

- mysql-connector-j-9.6.0.jar
- jasperreports-6.20.0.jar
- commons-collections4-4.4.jar
- commons-logging-1.2.jar
- commons-beanutils-1.9.4.jar
- commons-digester-2.1.jar
- itext-2.1.7.jar

---

## 🗃️ DATABASE SCHEMA

**Database Name:** `farm_equipment_rental_db`

**Tables:**
1. **farmers** - Farmer information with farm details
2. **equipment_categories** - Equipment types and daily rates
3. **equipment** - Farm equipment inventory
4. **rentals** - Rental transactions (Main Transaction Table)

**Relationships:**
- rentals → farmers (Many-to-One)
- rentals → equipment (Many-to-One)
- equipment → equipment_categories (Many-to-One)

---

## ✨ KEY FEATURES

### 1. User Authentication
- Secure login system
- Default credentials: admin / admin123

### 2. Dashboard
- Real-time statistics
- Total farmers count
- Total equipment count
- Active rentals count
- Total revenue display

### 3. Farmer Management
- Add new farmers with farm details
- Update farmer information
- Delete farmers
- Search by name/location/phone
- Full validation (Email, Phone, NIC)

### 4. Equipment Management
- Add new farm equipment
- Update equipment details
- Delete equipment
- Search by brand/model/number
- Equipment categories: Tractor, Harvester, Plow, Sprayer, Seeder
- Status tracking: Available, Rented, Maintenance
- Condition tracking: Excellent, Good, Fair

### 5. Rental Management (Main Transaction)
- Create new rental bookings
- Automatic date calculation
- Dynamic pricing based on equipment category
- Complete rental (return equipment)
- Cancel rental
- Automatic equipment status updates
- Filter: Active/All rentals
- Purpose tracking for agricultural use

### 6. Reporting System
- Revenue Analysis by Equipment Category
- Uses 3 tables with SQL JOINs
- Professional PDF output using Jasper Reports
- Grand total calculation
- Business decision-making support

---

## 🎯 DESIGN PATTERNS IMPLEMENTED

### 1. Singleton Pattern
**Class:** `DatabaseConnection.java`
- Ensures single database connection instance
- Thread-safe implementation

### 2. DAO Pattern
**Classes:** `FarmerDAO.java`, `EquipmentDAO.java`, `RentalDAO.java`
- Separates data access logic
- Full CRUD operations
- Easy to maintain

### 3. MVC Architecture
**Model:** Farmer, Equipment, Rental  
**View:** All UI forms with farm theme  
**Controller:** ReportController

---

## 📊 REPORT DETAILS

**Report Name:** Revenue Analysis by Equipment Category

**SQL Query:**
```sql
SELECT 
    ec.category_name AS category,
    ec.daily_rate AS rate,
    COUNT(r.rental_id) AS total_rentals,
    SUM(r.total_amount) AS total_revenue,
    AVG(r.total_amount) AS avg_revenue,
    SUM(r.total_days) AS total_days
FROM rentals r
JOIN equipment e ON r.equipment_id = e.equipment_id
JOIN equipment_categories ec ON e.category_id = ec.category_id
WHERE r.status = 'COMPLETED'
GROUP BY ec.category_id, ec.category_name, ec.daily_rate
ORDER BY total_revenue DESC;
```

**Tables Used:**
1. rentals
2. equipment
3. equipment_categories

**Purpose:** Identifies most profitable equipment categories for business decisions

---

## 🚀 INSTALLATION & SETUP

### Prerequisites
- JDK 17 or higher
- MySQL 8.0 or higher
- NetBeans IDE (or any Java IDE)

### Steps

1. **Clone/Download Project**
```
   Extract FarmEquipmentRentalSystem.zip
```

2. **Setup Database**
   - Open MySQL Workbench
   - Run the SQL script from database folder
   - Database and tables created automatically

3. **Configure Database Connection**
   - Open `DatabaseConnection.java`
   - Update:
```java
   private static final String PASSWORD = "your_password"; // Change this!
```

4. **Add Libraries**
   - Right-click project → Properties → Libraries
   - Add all JAR files from `/lib` folder

5. **Run Project**
   - Right-click project → Clean and Build
   - Right-click project → Run
   - Login: admin / admin123

---

## 🎨 UI THEME

**Agricultural/Farm Theme:**
- Primary: Brown/Earth tones (139, 90, 43)
- Accent: Orange (255, 140, 0)
- Success: Green (34, 139, 34)
- Background: Wheat (245, 240, 230)
- Icons: Farm emojis 🚜🌾👨‍🌾

---

## 📁 PROJECT STRUCTURE
```
FarmEquipmentRentalSystem/
│
├── src/
│   └── com/farmrental/
│       ├── Main.java
│       ├── model/
│       │   ├── Farmer.java
│       │   ├── Equipment.java
│       │   └── Rental.java
│       ├── dao/
│       │   ├── DatabaseConnection.java (Singleton)
│       │   ├── FarmerDAO.java
│       │   ├── EquipmentDAO.java
│       │   └── RentalDAO.java
│       ├── controller/
│       │   └── ReportController.java
│       ├── view/
│       │   ├── LoginForm.java
│       │   ├── DashboardForm.java
│       │   ├── FarmerForm.java
│       │   ├── EquipmentForm.java
│       │   └── RentalForm.java
│       └── util/
│           └── Validator.java
│
├── lib/ (all JARs)
├── dist/
│   └── FarmEquipmentRentalSystem.jar
├── database/
│   └── farm_equipment_rental_db.sql
└── README.md
```

---

## 🔒 VALIDATION & ERROR HANDLING

### Input Validations
- Email format validation
- Phone number validation (10 digits)
- NIC validation (Old/New format)
- Equipment number format
- Date range validation
- Positive number validation

### Exception Handling
- SQLException handling
- NumberFormatException handling
- User-friendly error messages
- Confirmation dialogs

---

## 👤 DEFAULT LOGIN

**Username:** admin  
**Password:** admin123

---

## 🎓 LEARNING OUTCOMES ACHIEVED

1. ✅ Core programming concepts
2. ✅ Advanced UI with custom theme
3. ✅ Database operations (CRUD)
4. ✅ Design patterns (Singleton, DAO, MVC)
5. ✅ Advanced reports (3-table JOINs)
6. ✅ Deployment (JAR file)

---

## 📝 SAMPLE DATA

- 5 Farmers with farm details
- 11 Equipment items (across 5 categories)
- 5 Sample rentals

---


---

**Developed with 🌾 for Agricultural Sector - 2026**
