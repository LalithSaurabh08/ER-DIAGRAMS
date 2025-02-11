Overview

This project contains Entity-Relationship (ER) Diagrams for three systems:

Library Management System
Restaurant Reservation System
Real Estate Listing System

The ER diagrams are created using Graphviz (Chen Notation) and Mermaid.js (Crow’s Foot Notation) inside a Quarto (.qmd) report. The report also includes explanations of design choices and relationships.



Diagrams Used

Graphviz (Chen Notation): Used for conceptual ER diagrams.
Mermaid.js (Crow’s Foot Notation): Used for detailed relationship visualization.







ER Diagrams


Library Management System - Mermaid (Crow's Foot)


erDiagram
    Book {
        string BookID
        string Title
        string Author
    }
    Member {
        string MemberID
        string Name
        date MembershipDate
    }
    Loan {
        int LoanID
        date LoanDate
        date ReturnDate
    }
    
    Book ||--o{ Loan : "borrowed"
    Member ||--o{ Loan : "makes"
    Loan }o--|| Member : "by"
    Loan }o--|| Book : "for"


Library Management System - Graphviz (Chen)


digraph LibraryManagement {
    node [shape=rectangle]
    Book [label="{ Book | BookID : String | Title : String | Author : String }"];
    Member [label="{ Member | MemberID : String | Name : String | MembershipDate : Date }"];
    Loan [shape=ellipse, label="{ Loan | LoanID : Int | LoanDate : Date | ReturnDate : Date }"];

    BorrowedBy [shape=diamond, label="borrowed"];
    Makes [shape=diamond, label="makes"];

    Book -> BorrowedBy;
    BorrowedBy -> Loan;
    Member -> Makes;
    Makes -> Loan;
}



Restaurant Reservation System - Mermaid (Crow's Foot)


erDiagram
    Customer {
        string CustomerID
        string Name
        string ContactNumber
    }
    Reservation {
        string ReservationID
        date Date
        time Time
    }
    Table {
        string TableNumber
        int SeatingCapacity
        string Location
    }

    Customer ||--o{ Reservation : "books"
    Table ||--o{ Reservation : "is for"
    Reservation }o--|| Customer : "by"
    Reservation }o--|| Table : "for"


Restaurant Reservation System - Graphviz (Chen)


digraph RestaurantReservation {
    node [shape=rectangle]
    Customer [label="{ Customer | CustomerID : String | Name : String | ContactNumber : String }"];
    Reservation [shape=ellipse, label="{ Reservation | ReservationID : String | Date : Date | Time : Time }"];
    Table [label="{ Table | TableNumber : String | SeatingCapacity : Int | Location : String }"];

    Books [shape=diamond, label="books"];
    IsFor [shape=diamond, label="is for"];

    Customer -> Books;
    Books -> Reservation;
    Table -> IsFor;
    IsFor -> Reservation;
}



Real Estate Listing System - Mermaid (Crow's Foot)


erDiagram
    Property {
        string PropertyID
        string Address
        float ListingPrice
    }
    Agent {
        string AgentID
        string Name
        string ContactInfo
    }
    Client {
        string ClientID
        string Name
        float Budget
    }
    
    Agent ||--o{ Property : "lists"
    Client ||--o{ Interest : "expresses"
    Property ||--o{ Interest : "gains"
    Interest }o--|| Client : "for"
    Interest }o--|| Property : "for"


Real Estate Listing System - Graphviz (Chen)


digraph RealEstateListing {
    node [shape=rectangle]
    Property [label="{ Property | PropertyID : String | Address : String | ListingPrice : Float }"];
    Agent [label="{ Agent | AgentID : String | Name : String | ContactInfo : String }"];
    Client [label="{ Client | ClientID : String | Name : String | Budget : Float }"];
    Interest [shape=ellipse, label="{ Interest }"];

    Lists [shape=diamond, label="lists"];
    Expresses [shape=diamond, label="expresses"];
    Gains [shape=diamond, label="gains"];

    Agent -> Lists;
    Lists -> Property;
    Client -> Expresses;
    Expresses -> Interest;
    Property -> Gains;
    Gains -> Interest;
}
