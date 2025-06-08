C# Windows Forms Project: Archiving 
Management System 
Project Goal 
Create a Windows Forms application that allows users to archive, manage, and retrieve 
research/thesis documents and OJT terminal reports. All document metadata and file paths will 
be persistently stored in a MySQL database. 
Learning Objectives 
1. GUI Development (C# Windows Forms): Designing and implementing a user-friendly 
graphical interface. 
2. Database Connectivity (ADO.NET & MySQL): Connecting to and interacting with a MySQL 
database (CRUD operations: Create, Read, Update, Delete). 
3. SQL Fundamentals: Writing and executing SQL queries for data management. 
4. File System Interaction: Handling file paths, copying/moving files to a designated archive 
folder. 
5. Object-Oriented Programming (OOP) in C#: Using classes and objects to model 
documents and database interactions. 
6. Error Handling: Gracefully managing database connection issues, invalid input, and file 
system errors. 
Project Components: Input, Processes, and Results 
Overall Project Goal: To establish a robust system for archiving and managing research/thesis 
documents and OJT terminal reports, ensuring easy storage and retrieval. 
NOTES: These components are guides, for the logic flow of the 
processes (components) 
Component 1: Main Application Interface / Dashboard 
 Description: This is the primary window of the Windows Forms application. It provides 
the main navigation and high-level overview of the archived documents. 
 Input:  
o User clicks on buttons (e.g., "Add New Document," "Search," "View All," "Manage 
Categories"). 
o User interaction with data grids (e.g., selecting a row). 
 Process/es:  
o Form Initialization: Loads initial data or displays a welcome screen. 
o Event Handling: Responds to button clicks and other GUI events. 
o Form Navigation: Opens new forms or panels for specific functionalities (e.g., 
"Add Document Form"). 
o Data Display (Overview): Optionally displays a summary of archived documents 
(e.g., total count, recent additions) by querying the database. 
 Results:  
o The main application window is displayed. 
o Other forms or dialogs are opened based on user actions. 
o Summary data is shown on the dashboard. 
Component 2: Database Connection & Data Access Layer 
 Description: This crucial component manages all interactions with the MySQL database. 
It acts as an intermediary between the UI and the database. 
 Input:  
o SQL queries (INSERT, SELECT, UPDATE, DELETE statements). 
o Connection string for the MySQL database. 
o Data parameters for queries (e.g., document_id, title, author). 
 Process/es:  
o Establishing Connection: Opens a connection to the MySQL database using the 
connection string. 
o Executing Queries: Runs SQL commands (e.g., MySqlCommand, MySqlDataAdapter). 
o Data Retrieval: Fetches data from the database into DataTable or custom C# 
objects. 
o Data Submission: Sends data from C# objects to the database. 
o Connection Management: Ensures connections are opened and closed properly 
(e.g., using statements). 
o Error Handling: Catches and manages MySqlException for database-related errors 
(e.g., connection failed, SQL syntax errors, constraint violations). 
 Results:  
o Data is successfully written to or read from the MySQL database. 
o Errors are logged or reported to the user in a user-friendly way. 
o Database connection is maintained or gracefully closed. 
Component 3: Document Archiving / Adding New Record 
 Description: Allows users to input metadata for a new document (research/thesis or OJT 
report) and select the file to be archived. 
 Input:  
o User input from text fields: Document ID (auto-generated or manually entered), Title, 
Author(s), Year, Document Type (Thesis/Research/OJT Report), Keywords, Abstract. 
o User selection of the actual document file via an OpenFileDialog. 
 Process/es:  
o GUI Input Collection: Gathers data from form controls. 
o Input Validation: Validates that required fields are filled, document ID (if manual) 
is unique, etc. 
o File Copying: Copies the selected document file (.pdf, .docx, etc.) from its original 
location to a predefined central archive folder on the server/local machine. 
o Path Storage: Stores the path to the copied file in the database. 
o Database Insertion: Inserts the document's metadata (including the archived file 
path) into the MySQL database. 
o ID Generation (Optional): Generates a unique Document ID if not manually entered. 
 Results:  
o New document metadata is stored in the database. 
o The actual document file is safely copied to the archive. 
o Confirmation message or error feedback to the user. 
Component 4: Document Search & Retrieval 
 Description: Enables users to search for archived documents based on various criteria and 
view/download the associated file. 
 Input:  
o User input from search fields: Keywords, Title, Author, Year, Document Type. 
o User selection of a document from a search results DataGridView. 
o User click on a "View/Download File" button. 
 Process/es:  
o Query Construction: Builds a dynamic SQL SELECT query based on the user's search 
criteria. 
o Database Query: Executes the constructed query via the Data Access Layer. 
o Results Display: Populates a DataGridView with the fetched document metadata. 
o File Opening/Downloading: When a user selects a document and chooses to 
view/download, the program retrieves the stored file path, checks if the file exists, 
and then opens it using the default application or copies it to a user-specified 
download location. 
o Error Handling: Manages cases where no search results are found, or the linked 
file is missing. 
 Results:  
o Search results are displayed in a table. 
o The selected document file is opened or downloaded. 
o Messages indicating no results found or file access issues. 
Component 5: Document Management (Update & Delete) 
 Description: Allows authorized users to modify existing document metadata or remove 
document records from the archive. 
 Input:  
o User selection of a document from a list/search results. 
o Modified user input for Title, Author, Year, Keywords, Abstract, etc. 
o User confirmation for deletion. 
 Process/es:  
o Data Loading for Edit: Populates an edit form with the selected document's 
current metadata. 
o Input Validation: Validates modified data. 
o Database Update: Executes an SQL UPDATE query to modify the document's 
metadata in the database. 
o Database Deletion: Executes an SQL DELETE query to remove the document's 
record from the database. 
o File Deletion (Optional): Prompts user if they also want to delete the physical file 
from the archive folder during deletion. 
o Error Handling: Catches database errors during update/delete operations. 
 Results:  
o Document metadata is updated in the database. 
o Document record (and optionally the physical file) is removed. 
o Confirmation messages or error feedback to the user. 
Component 6: Category/Metadata Management (Optional, for advanced features) 
 Description: Allows administrators to manage predefined lists like "Document Type" or 
"Departments," ensuring data consistency. 
 Input:  
o User input for new category names. 
o User selection of categories to update/delete. 
 Process/es:  
o CRUD for Categories: Standard Create, Read, Update, Delete operations on 
dedicated category tables in the database (e.g., document_types table). 
o Populating Dropdowns: Populates ComboBox controls in other forms with data 
from these category tables. 
 Results:  
o Predefined lists are updated in the database. 
o User selection options are dynamically populated in relevant forms. 
Grading Criteria for the C# Windows Forms Project: Archiving 
Management System 
1. Functionality (50%) 
Your application must perform all core archiving and management tasks as described. 
 Core Archiving Features (30%)  
o Add New Document: Can a user successfully add a new research/thesis/OJT 
report record with all required metadata? Is the physical file copied to the 
designated archive folder, and its path stored correctly in the database? 
o Search & Retrieve: Can a user effectively search for documents using multiple 
criteria (e.g., title, author, keywords, type)? Are search results displayed clearly? 
Can the associated document file be opened/downloaded from the archive? 
o Update Document Details: Can a user select an existing document and modify its 
metadata (e.g., correct a typo in the title, add keywords)? 
o Delete Document: Can a user select and delete a document record from the 
database? Is there an option to also delete the physical file from the archive? 
 Database & File System Interaction (15%)  
o Database Connectivity: Does the application successfully connect to and interact 
with the MySQL database? 
o CRUD Operations: Are INSERT, SELECT, UPDATE, and DELETE queries executed 
correctly against the database? 
o File System Operations: Are files correctly copied to the archive folder and 
correctly accessed for retrieval? 
 Error Handling & Robustness (5%)  
o Database Connection: Does the application gracefully handle issues like the 
database being unavailable or incorrect connection strings? 
o Invalid Input: Does the application validate user input for required fields and 
appropriate data types before submitting to the database? 
o File Not Found (Archive): Does it handle cases where an archived physical file 
might be missing or corrupted? 
o Unique Constraints: Does it prevent duplicate document IDs (if manual) or other 
primary key violations? 
2. Code Quality & Structure (30%) 
This section assesses the clarity, organization, and adherence to C# and OOP best practices. 
 Modularity & OOP (10%)  
o Classes: Is the code logically organized into classes (e.g., Document class, DbManager 
or DataAccess class, UI-related classes)? 
o Separation of Concerns: Is there a clear separation between the UI logic, business 
logic, and data access logic? 
o Encapsulation: Are class members and methods appropriately encapsulated (e.g., 
using private, public, properties)? 
 Readability & Maintainability (10%)  
o Meaningful Names: Are variables, methods, and classes clearly and descriptively 
named? 
o Comments: Is the code adequately commented where necessary (complex logic, 
public APIs)? 
o Formatting: Is the code consistently indented, spaced, and formatted according 
to C# conventions? 
 Database Interaction Design (5%)  
o Parameterization: Are SQL queries properly parameterized to prevent SQL 
injection vulnerabilities? 
o Connection Management: Are database connections opened and closed 
efficiently (e.g., using using blocks for MySqlConnection, MySqlCommand)? 
 Adherence to C#/.NET Best Practices (5%)  
o Appropriate use of C# language features and .NET framework classes. 
o Efficient use of data structures for in-memory processing. 
3. User Experience (UX) (20%) 
The application's usability and aesthetic appeal. 
 Intuitive Interface: Is the Windows Forms layout logical, clean, and easy to navigate? Are 
controls clearly labeled? 
 Informative Feedback: Does the application provide clear messages about successful 
operations, ongoing processes, and errors (e.g., using MessageBox or status bar)? 
 Input Design: Are input fields appropriately designed (e.g., TextBox for text, NumericUpDown 
for numbers, DateTimePicker for dates, ComboBox for predefined types)? 
 Visual Appeal: Is the overall design of the forms attractive and professional? 
 Responsiveness: Does the application remain responsive during database or file 
operations (for more advanced implementations, consider async/await for long-running 
tasks)? 
