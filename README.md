CREATE TABLE Venue (
    VenueID INT PRIMARY KEY,
    Name VARCHAR(100),
    Location VARCHAR(100),
    Capacity INT,
    ContactInfo VARCHAR(100)
);
 
CREATE TABLE Concert (
    ConcertID INT PRIMARY KEY,
    VenueID INT,
    Date DATE,
    Time TIME,
    FOREIGN KEY (VenueID) REFERENCES Venue(VenueID)
);
 
-- Recursive Relationship Example
-- Event Organizer supervises other Event Organizers
CREATE TABLE EventOrganizer (
    OrganizerID INT PRIMARY KEY,
    Name VARCHAR(100),
    SupervisorID INT,
    FOREIGN KEY (SupervisorID) REFERENCES EventOrganizer(OrganizerID)
);
 
-- Arc Relationship Example
-- Ticket can be sold through either TicketSale or TicketType
CREATE TABLE TicketSale (
    TicketSaleID INT PRIMARY KEY,
    Price DECIMAL(10,2),
    Quantity INT,
    DateSold DATE,
    ConcertID INT,
    BuyerInfo VARCHAR(100),
    FOREIGN KEY (ConcertID) REFERENCES Concert(ConcertID)
);
 
CREATE TABLE TicketType (
    TicketTypeID INT PRIMARY KEY,
    Name VARCHAR(100),
    Description VARCHAR(255),
    Price DECIMAL(10,2),
    Availability INT,
    Restrictions VARCHAR(255),
    ConcertID INT,
    FOREIGN KEY (ConcertID) REFERENCES Concert(ConcertID)
);
