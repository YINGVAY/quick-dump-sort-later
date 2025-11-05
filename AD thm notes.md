In a windows domain, credentials are stored in a centralised repository called the active directory

The server in charge of running the Active Directory services is called the domain controller

AD objects

Users:
Users are one of the objects knows as security principals, meaning that they can be authenticated by the domain and can be assigned privileges over resources like files or printers. You could say that a security principal is an object that can act upon the resources in the network

Users can be used to represent two types of entities:
~ People: employee, clients ETC
~ Services: You can also define users to be used by services like IIS or MSSQL. Every single service requires a user to run, but service users are different from regular users as they will only have the privileges needed to run their specific service.


Machines:
Machines are another type of object within active directory; for every computer that joins the active directory domain, a machine object will be created. Machines are also considered "security principals" and are assigned an account just as any regular user. This account has somewhat limited rights within the domain itself.

The machine accounts themselves are local administrators on the assigned computer, they are generally not supposed to be accessed by anyone except the computer itself, but as with any other account, if you have the password, you can use it to log in.


