```mermaid
classDiagram
    class BankUI {
        <<Boundary>>
        +mainMenu() void
        +inputUserData() void
        +inputTransactionData() void
    }

    class User {
        -id: String
        -pw: String
        -name: String
        -phone: String
        -address: String
        +registerUser(id: String, pw: String, name: String, phone: String, address: String) User
        +updateUser(id: String, name: String, phone: String, address: String) void
        +deleteUser(id: String) boolean
        +searchUser(id: String) User
    }

    class Account {
        -number: String
        -balance: long
        +deposit(id: String, amount: long) long
        +withdraw(id: String, amount: long) long
        +transfer(id: String, targetAccountNumber: String, amount: long) long
        +computeBalance() long
    }

    %% 관계 설정
    BankUI ..> Account : Depends on
    User "1" -- "1..*" Account : Manages/Associated