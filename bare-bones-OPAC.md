# Creating a Bare Bones OPAC

**PURPOSE** The goal of this assignment
is to develop an understanding of relational
databases by entering and retrieving data.

**TASKS**

1. Create an HTML page for entering queries.
	a. Copy and paste code in Nano.
2. Create a PHP search script. 
	a. Copy and paste code in Nano.
	b. Replace generic IP address in the above code with my IP. 
3. Enter additional books into database to create additional data.
	a. Connect to mysql
		'''
		mysql -u opacuser -p
		'''
	b. Inster the following command:
		'''
		insert into books
		(author, title, publisher, copyright) values
		('Zadie Smith', 'White Teeth', 'Hamish Hamilton', '2001-01-27';
		''' 
