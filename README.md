# Game Store Management System

A comprehensive C++ application for managing a game store's inventory, sales, customers, and tournaments using SQLite3 database.

## 📋 Features

### Core Functionality
- **Product Management**: Add, view, update, and delete gaming products across multiple categories (Games, Consoles, Accessories)
- **Customer Management**: Maintain customer database with membership tiers (Non-member, Standard, Premium)
- **Sales Processing**: Create sales transactions with automatic inventory updates and total calculations
- **Tournament System**: Organize gaming tournaments with player registration and capacity management
- **Inventory Tracking**: Real-time stock monitoring with minimum stock level alerts

### Technical Highlights
- ✅ Transaction-safe database operations (ACID compliance)
- ✅ Parameterized queries to prevent SQL injection
- ✅ Input validation for all user inputs
- ✅ Modular helper functions for code reusability
- ✅ Automatic inventory depletion on sales
- ✅ Multi-table relationship management

## 🛠️ Technologies Used

- **Language**: C++ (C++11 or higher)
- **Database**: SQLite3
- **Libraries**: 
  - `sqlite3.h` - Database operations
  - `<iostream>` - Input/output
  - `<string>` - String handling
  - `<limits>` - Input validation

## 📦 Installation

### Prerequisites
- C++ compiler (GCC, Clang, or MSVC)
- SQLite3 library installed

### Linux/Mac
```bash
# Install SQLite3
sudo apt-get install sqlite3 libsqlite3-dev  # Ubuntu/Debian
brew install sqlite3                          # macOS

# Clone the repository
git clone https://github.com/evayedon/game-store-management.git
cd game-store-management

# Compile
g++ -std=c++11 main.cpp -lsqlite3 -o game_store

# Run
./game_store
```

### Windows
```bash
# Download SQLite3 from https://www.sqlite.org/download.html
# Extract and add to your project

# Compile with MinGW
g++ -std=c++11 main.cpp -lsqlite3 -o game_store.exe

# Or use Visual Studio with SQLite NuGet package
```

## 🗄️ Database Schema

### Tables
1. **Product**
   - `p_code` (Primary Key)
   - `p_name`, `category_id`, `p_price`, `p_quantity`, `min_stock_level`

2. **Customer**
   - `cus_id` (Primary Key)
   - `cus_fname`, `cus_lname`, `cus_email`, `cus_phone`, `membership_id`

3. **Sale**
   - `sale_id` (Primary Key)
   - `sale_datetime`, `cus_id` (Foreign Key), `total_amount`, `discount_applied`, `payment_status_id`

4. **Sale_Item**
   - `sale_item_id` (Primary Key)
   - `sale_id` (Foreign Key), `p_code` (Foreign Key), `quantity`, `item_price`

5. **Tournament**
   - `tour_id` (Primary Key)
   - `tour_name`, `tour_datetime`, `tour_fee`, `max_players`

6. **Tournament_Registration**
   - `reg_id` (Primary Key)
   - `tour_id` (Foreign Key), `cus_id` (Foreign Key), `registration_datetime`, `payment_status_id`

## 🚀 Usage

### Main Menu Options
```
1. Add Product
2. Add Customer
3. Add Sale
4. Add Sale Item
5. Add Tournament
6. Register for Tournament
7. View Products
8. View Customers
9. View Sales
10. Exit
```

### Example Workflow
```cpp
// 1. Add a customer
Enter customer first name: John
Enter customer last name: Doe
Enter customer email: john.doe@email.com
Enter customer phone: 555-1234
Choose membership status: 2 (Standard)

// 2. Add a product
Enter product name: PlayStation 5
Choose category: 2 (Consoles)
Enter product price: 499.99
Enter product quantity: 10
Enter minimum stock level: 2

// 3. Create a sale
Choose customer: 1 (John Doe)
Enter discount: 10
Payment status: 2 (Paid)

// 4. Add items to sale
Choose sale: 1
Choose product: 1 (PlayStation 5)
Enter quantity: 1
// Inventory automatically updated: 10 → 9
```

## 🔒 Security Features

- **SQL Injection Prevention**: All queries use prepared statements with parameterized inputs
- **Input Validation**: Comprehensive validation for all user inputs (numeric, string, range checks)
- **Transaction Safety**: Database transactions ensure data consistency across multiple operations
- **Error Handling**: Graceful error handling with informative messages

## 📁 Project Structure

```
game-store-management/
├── main.cpp                 # Main program entry point
├── database.cpp             # Database operations
├── helpers.cpp              # Helper functions
├── validation.cpp           # Input validation functions
├── schema.sql               # Database schema
├── README.md               # This file
└── LICENSE                 # License file
```

## 🧪 Key Functions

### Helper Functions
```cpp
bool prepareStatement(sqlite3 *db, const string &query, sqlite3_stmt *&stmt);
bool executeStatement(sqlite3_stmt *stmt);
int selectFromList(sqlite3 *db, const string &query, const string &prompt);
bool getSingleInt(sqlite3 *db, const string &query, int bind_value, int &result);
double getValidatedDouble(double min, double max);
int getValidatedChoice(int min, int max);
```

### Core Operations
- `addProduct()` - Add new products to inventory
- `addCustomer()` - Register new customers
- `addSale()` - Create sales transactions
- `addSaleItem()` - Add items to sales with inventory updates
- `addTournament()` - Create gaming tournaments
- `addTournamentRegistration()` - Register players with capacity checks

## 🐛 Known Issues / Future Enhancements

- [ ] Add update and delete operations for all entities
- [ ] Implement search/filter functionality
- [ ] Add sales reports and analytics
- [ ] Create GUI interface
- [ ] Export data to CSV/PDF
- [ ] Add user authentication system
- [ ] Implement email validation
- [ ] Add barcode scanning support

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👨‍💻 Author

**Your Name**
- GitHub: [@evayedon](https://github.com/evayedon)
- LinkedIn: [Your LinkedIn](https://linkedin.com/in/evans-ayensu-donkor-730b30289)
- Email: optimistdelt80@gmail.com

## 🙏 Acknowledgments

- SQLite3 documentation
- C++ community
- [Any tutorials or resources you used]

## 📸 Screenshots

*Add screenshots of your application here*

```
Main Menu:
┌─────────────────────────────────┐
│  Game Store Management System   │
├─────────────────────────────────┤
│ 1. Add Product                  │
│ 2. Add Customer                 │
│ 3. Add Sale                     │
│ ...                             │
└─────────────────────────────────┘
```

---

**Note**: This is an educational project demonstrating database management concepts in C++.
