IT Help Desk Tracker
A local help desk tool that takes an IT support request from Open to Closed. Log requests from a Python terminal menu, then use the browser dashboard to find tickets and check the queue. Both interfaces use the same SQLite database.
Interface	What you can do
Terminal	Create a ticket with a title and description, list open tickets, and close a ticket by ID.
Browser dashboard	View total, open, and closed ticket counts. Search by ticket ID, title, or description and filter the queue by status.


Step	What to expect
In the terminal menu, create Office printer is offline with the description The printer shows Offline on two workstations.	The terminal displays the new ticket ID.
Refresh the dashboard and search for printer.	The ticket appears as Open and the open count includes it.
Close the ticket by ID in the terminal. Refresh the dashboard and select Closed.	The ticket appears in the closed queue and the summary counts reflect the change.
Restart the server and open the dashboard again.	The ticket is still recorded as Closed.


The dashboard reads the database when the page loads. Refresh it after creating or closing a ticket in the terminal. Search and status filters apply to the displayed queue, while the summary cards show counts for the entire database.
How it works
app.py uses parameterised SQL to create and close tickets. web_app.py reuses its database configuration, reads the records, and renders the summary cards and ticket rows into the HTML template. JavaScript filters the rendered rows as you type.
Path	Role
app.py	Terminal menu, database setup, and ticket updates
web_app.py	Local Python HTTP server and dashboard rendering
dashboard.html	Dashboard layout, CSS, and JavaScript filters
helpdesk.db	Local SQLite data created automatically on first run and kept out of version control


Planned improvement
Add a New ticket form and a Close ticket action to the dashboard so the full workflow can run in the browser.
Author
Kgotso Jonas
