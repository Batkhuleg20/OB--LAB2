```mermaid
classDiagram
    class Book {
        -String title
        -String author
        -int publicationYear
        -String category
        -String ISBN
        -String location
        -String loanStatus
        +updateStatus()
        +getDetails()
        +searchByTitle()
        +searchByAuthor()
        +searchByCategory()
    }

    class BookRegistration {
        -DateTime registrationDate
        -String registeredBy
        -String bookCondition
        -String acquisitionMethod
        +registerNewBook()
        +updateBookInfo()
        +removeBook()
        +generateRegistrationNumber()
        +validateISBN()
    }

    class User {
        -String name
        -String address
        -String phone
        -String email
        -String membershipId
        -int numberOfBorrowedBooks
        +updateInfo()
        +searchByName()
        +searchByAddress()
    }

    class LoanRecord {
        -DateTime loanDate
        -DateTime dueDate
        -DateTime returnDate
        -double fineAmount
        +calculateFine()
        +updateStatus()
        +checkDueDate()
    }

    class LibraryStaff {
        -String staffId
        -String name
        -String position
        +checkUserInfo()
        +updateBookRecord()
        +processLoan()
        +processReturn()
        +checkLoanStatus()
        +manageBookRegistration()
    }

    class LibraryStatus {
        -int totalBooks
        -int totalUsers
        -int loanedBooks
        -int staffCount
        +updateStatus()
        +generateReport()
        +checkAvailableBooks()
    }

    User "1" -- "0..*" LoanRecord : has
    Book "1" -- "0..*" LoanRecord : associated with
    LibraryStaff "1" -- "0..*" LoanRecord : manages
    LibraryStaff "1" -- "0..*" Book : manages
    LibraryStaff "1" -- "0..*" User : manages
    LibraryStatus "1" -- "1" LibraryStaff : monitors
    BookRegistration "1" -- "1" Book : registers
    LibraryStaff "1" -- "0..*" BookRegistration : performs
