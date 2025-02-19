```mermaid
classDiagram
    class Book {
        -String title
        -String author
        -int publishYear
        -String category
        -String ISBN
        -String location
        -String loanStatus
        +addBook()
        +updateBook()
        +searchByTitle()
        +searchByAuthor()
        +searchByCategory()
    }

    class User {
        -String name
        -String address
        -String phone
        -String email
        -String membershipId
        -int borrowedBooksCount
        +register()
        +updateInfo()
        +searchByName()
        +searchByAddress()
        +checkLoanHistory()
    }

    class LoanTransaction {
        -DateTime loanDate
        -DateTime dueDate
        -String status
        +loanBook()
        +returnBook()
        +checkOverdue()
        +updateLoanStatus()
    }

    class LoanHistory {
        -Book book
        -User user
        -DateTime loanDate
        -DateTime returnDate
        -double fineAmount
        +recordLoan()
        +updateHistory()
        +calculateFine()
        +checkUserHistory()
    }

    class LibraryStaff {
        -String staffId
        -String name
        -String role
        +verifyUser()
        +processLoan()
        +processReturn()
        +updateBookInventory()
        +manageUserAccounts()
    }

    class LibraryStatus {
        -int totalBooks
        -int totalUsers
        -int loanedBooks
        -int staffCount
        +updateStatus()
        +generateReport()
        +checkInventory()
    }

    LibraryStaff "1" --> "*" Book : manages
    LibraryStaff "1" --> "*" User : manages
    User "1" --> "*" LoanTransaction : makes
    Book "1" --> "*" LoanTransaction : involved_in
    LoanTransaction "1" --> "1" LoanHistory : records
    LibraryStaff "1" --> "*" LoanTransaction : processes
    LibraryStatus "1" --> "*" Book : tracks
    LibraryStatus "1" --> "*" User : tracks
