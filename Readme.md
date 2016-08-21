DapraCadapra - a simple object mapper for .Net
========================================

Additions to Dapper Dot Net:
In the core SqlMapper object, I've added 3 methods so far.
Update -- takes parameters of table name, column name, value, and a where calause.
	-- Following stanard Dapper usage, your models shoudl have names matching tables and properties matching columns, so this method could be called like:
	db.update(object.GetType().GetName().ToString(), object.GetProperty("property").GetName().ToString, "value", "field = x");
ExecuteMany -- Works exactly like the Execute method in Dapper, except that it takes a list of strings (where each string is a sql query) and will execute them all on one trip to the database.
Insert -- Pass this method the name of the table you want to insert into, and a dictionary containing the names of the fields and the values for those fields.


Installation
--------------------------------------------
Compile the project and then simply add the dapracadapra.dll file corresponding to your .net version that your project is using as a reference in your project.
Note:  This should also compile fine in Mono, but it has not been tested.

Release Notes
-------------

This project is forked from Dapper Dot Net available at:
[link](http://stackexchange.github.io/DapraCadapra-dot-net/)


Features
--------
A fork of Daooer Dot Net including evrything in Dapper plus the following.

It provides 3 helpers:

DB.Update(string table, string column, string value, string where - null)  -- This method serves as a generic update method that does not requre an integer primary key on the table.  You give it a table name, a column, and then a where clause for example --
Person me = new Persion();
update (me.GetType().GetName(), fname, "Chuck", "ssn = 123-45-6789");

insert() -- still experimental

executemany) --  This method will take a list of string where each string is a valid sql query(without the ending ;).  It will execute every query in the list on one trip to the database making them run virtually instantly.

