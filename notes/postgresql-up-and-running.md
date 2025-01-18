PostgreSQL: Up and Running (2012)

Regina Obe & Leo Hsu

───────────────

▪ PostgreSQL allows you to write stored procedures and functions in several programming languages, and the architecture allows you the flexibility to support more languages. Example languages that you can write stored functions in are SQL (built-in), PL/pgSQL (built-in), PL/Perl, PL/Python, PL/Java, and PL/R, to name a few, most of which are packaged with many distributions.

▪ PostgreSQL 9.1 introduced a new SQL construct, CREATE EXTENSION
, which allows you to install the many available extensions with a single SQL statement for each in a specific database.

▪ PostgreSQL was designed from the ground up to be a server-side database.

▪ it’s not ideal as an embeddable database, like SQLite or Firebird.

▪ If all you need is a key value store or you expect your database to just sit there and hold stuff, it’s probably overkill for your needs.

▪ PostgreSQL has a rich set of online documentation for each version

▪ Thankfully, those days are gone. Granted, you can still compile should you so choose, but most users nowadays get their PostgreSQL with a prepackaged installer.

▪ If you’re installing PostgreSQL for the first time and have no existing database to upgrade, you should always install the latest stable release version for your OS.

▪ There are three popular tools for managing PostgreSQL and these are supported by PostgreSQL core developers; they tend to stay in synch with PostgreSQL versions

▪ In addition, there are plenty of commercial offerings as well.

▪ psql is a command-line interface for writing queries and managing PostgreSQL. It comes packaged with some nice extras, such as an import and export commands for delimited files, and a reporting feature that can generate HTML output. psql has been around since the beginning of PostgreSQL and is a favorite of hardcore PostgreSQL users.

▪ This is the widely used, free, graphical administration tool for PostgreSQL. You can download it separately from PostgreSQL. pgAdmin runs on the desktop and can connect to multiple PostgreSQL servers regardless of version or OS. Even if you have your database server on a window-less Unix-based server, install pgAdmin and you’ll find yourself armed with a fantastic GUI. pgAdmin is pictured in Figure 1-1.

▪ PHPPgAdmin, pictured in Figure 1-2, is a free, web-based administration tool patterned after the popular PHPMyAdmin for MySQL. PostgreSQL has many more kinds of database objects than MySQL, as such PHPPgAdmin is a step up from PHPMyAdmin with additions to manage schemas, procedural languages, casts, operators, and so on. If you’ve used PHPMyAdmin, you’ll find PHPPgAdmin to be nearly identical.

▪ In PostgreSQL, there is really only one kind of an account and that is a role

▪ Roles can be members of other roles, and when we have this kind of relationship, the containing roles are called groups

▪ For the rest of this discussion, we’ll be using the more generic CREATE ROLE
, which is used to create both users and groups.

▪ If you look at fairly ANSI-SQL standard databases such as Oracle and later versions of SQL Server, you’ll notice they also have a CREATE ROLE
statement, which works similarly as the PostgreSQL one

▪ postgres is an account that is created when you first initialize the PostgreSQL data cluster. It has a companion database called postgres. Before you do anything else, you should login as this user via psql or pgAdmin and create other users.

▪ pgAdmin has a graphical section for creating user roles, but if you were to do it using standard SQL data control language (DCL), you would execute an SQL command as shown in Example 2-3.

▪ CREATE ROLE leo LOGIN PASSWORD 'lion!king'
CREATEDB VALID UNTIL 'infinity';

▪ You can only create a super user if you are a super user yourself.

▪ CREATE ROLE regina LOGIN PASSWORD 'queen!penultimate'
SUPERUSER VALID UNTIL '2020-10-20 23:00';

▪ Group roles are generally roles that have no login rights but have other roles as members. This is merely a convention. There is nothing stopping you from creating a role that can both login and can contain other roles.

▪ We can create a group role with this SQL DCL statement:

CREATE ROLE jungle INHERIT;

▪ And add a user or other group role to the group with this statement:

GRANT jungle TO leo;

▪ One quirky thing about PostgreSQL is the ability to define a role that doesn’t allow its member roles to inherit its rights

▪ This is a feature that causes much confusion and frustration when setting up groups, as people often forget to make sure that the group role is marked to allow its permissions as inheritable.

▪ Some permissions can’t be inherited. For example, while you can create a group role that you mark as super user, this doesn’t make its member roles super users; however, those users can impersonate their parent role, thus gaining super power rights for a brief period.

▪ The simplest create database statement to write is:

CREATE DATABASE mydb;

▪ A template database is, as the name suggests, a database that serves as a template for other databases

▪ In actuality, you can use any database as template for another, but PostgreSQL allows you to specifically flag certain databases as templates

▪ The main difference is that a database marked as template can’t be deleted and can be used by any user having CREATEDB rights (not just superuser) as a template for their new database

▪ The template1 database that is used as the default when no template is specified, doesn’t allow you to change encodings

▪ CREATE DATABASE mydb TEMPLATE template0;

▪ If we wanted to make our new database a template, we would run this SQL statement as a super user:

UPDATE pg_database SET datistemplate=true WHERE datname='mydb';

▪ Schemas are a logical way of partitioning your database into mini-containers. You can divide schemas by functionality, by users, or by any other attribute you like.

▪ Aside from logical partitioning, they provide an easy way for doling out rights

▪ CREATE SCHEMA contrib;

▪ The default search_path defined in postgresql.conf is "$user",public. This means that if there is a schema with the same name as the logged in user, then all non-schema qualified objects will first check the schema with the same name as user and then the public schema

▪ Schemas are also used for simple abstraction. A table name only needs to be unique within the schema, so many applications exploit this by creating same named tables in different schemas and, depending on who is logging in, they will get their own version based on which is their primary schema.

▪ Permissions are one of the trickiest things to get right in PostgreSQL. This is one feature that we find more difficult to work with than other databases.

▪ If you find this all overwhelming for setting permissions, just use pgAdmin for permission management

▪ pgAdmin provides a great interface for setting default permissions, as well as retroactively granting bulk permissions of selective objects.

▪ Extensions and contribs are add-ons that you can install in a PostgreSQL database to extend functionality beyond the base offerings. They exemplify the best feature of open source software: people collaborating, building, and freely sharing new features.

▪ In those cases, the term extension has come to replace the term contrib.

▪ The first thing to know about extensions is that they are installed separately in each database

▪ Creates a compressed, single database backup:

pg_dump -h localhost -p 5432 -U someuser -F c -b -v -f mydb.backup mydb

▪ The pg_dumpall utility is what you would use to backup all databases into a single plain-text file, along with server globals such as tablespace definitions and users. Refer to Server Backup: pg_dumpall for listing of available pg_dumpall command options.

▪ There are two ways of restoring in PostgreSQL:

▪ Using psql to restore plain text backups generated with pg_dumpall or pg_dump

▪ Using pg_restore utility for restoring compressed, tar and directory backups created with pg_dump

▪ PostgreSQL, unlike some other databases, lets you embed functions that perform actions within a regular SELECT query

▪ We can kill all her connections by running this command:

Before 9.2:

SELECT pg_terminate_backend(procpid) FROM pg_stat_activity WHERE usename = 'regina';

▪ A plain SQL backup is nothing more than a text file of a huge SQL script. It’s the least convenient of backups to have, but it’s portable across different database systems.

▪ To create a tablespace, you just need to denote a logical name and a physical folder

▪ CREATE TABLESPACE secondary LOCATION 'C:/pgdata91_secondary';

▪ ALTER DATABASE mydb SET TABLESPACE secondary;

To move just a table:

ALTER TABLE mytable SET TABLESPACE secondary;

▪ Moving a table to another tablespace locks it for the duration of the move.

▪ psql is the de rigueur command-line utility packaged with PostgreSQL. Aside from its most common use of running queries, you can use psql as an automated scripting tool, as a tool for importing or exporting data, restoring, database administration, and even go so far as to use it as a minimalistic reporting tool.

▪ To use psql, the first thing you’ll want to know is what you can do interactively. You can get help with psql \?
. For a thorough list of available interactive commands, refer to psql Interactive Commands.

▪ Although you have many more interactive commands than non-interactive ones at your disposal, you can effectively use all interactive commands non-interactively by embedding them into scripts

▪ Non-interactive commands means that you ask psql to execute a script file composed of a mix of SQL statements and psql commands

▪ For situations where you have many commands that must be run in sequence or repeatedly, you’re better off creating a script first and then running it using psql.

▪ There will be far fewer switches to worry about when running psql non-interactively since the details have been embedded in the script file

▪ To execute a file simply use the -f switch as follows:

psql -f some_script_file

▪ Notice how you can have multiple SQL statements as long as you separate them with a semicolon

▪ Since we want the output of our query to be saved as an executable statement, we need to remove the headers by using the \t switch and use the \a switch to get rid of the extra breaking elements that psql normally puts in.

▪ If you do use psql as your workhorse, consider customizing your psql environment. psql can read configuration settings from a file called psqlrc

▪ On Unix-based systems, the file is generally named .psqlrc and searched for in the home directory. On Windows, this file is called psqlrc.conf and searched for in the %APPDATA%\postgresql folder, which usually resolves to C:\Users\your_login\AppData\Roaming\postgresql. Don’t worry if you can’t find the file; it usually doesn’t appear on its own and you need to manually create it.

▪ When we connect with psql to our database, our prompt looks like:

postgres@localhost:5442 postgresql_book#

▪ If you are doing a large batch of precarious updates, you may want a safety net. Start by turning AUTOCOMMIT off:

\set AUTOCOMMIT off

▪ For example, if you use EXPLAIN ANALYZE VERBOSE
all the time and you’re tired of typing it all out, you can define a variable as follows:

\set eav 'EXPLAIN ANALYZE VERBOSE'

Now whenever you want to do an EXPLAIN ANALYZE VERBOSE
of a query, you prefix it with :eav (colon resolves the variable):

:eav SELECT COUNT(*) FROM pg_tables;

▪ The psql history feature generally doesn’t work on Windows unless running under Cygwin

▪ Finally, to unset a variable in psql, simply issue the \unset command followed by the variable name. For example:

\unset qstats91

▪ Although you normally use SQL and psql specific commands in psql, you can call out to the OS shell using the ! command.

▪ psql has a command called \copy for both importing from and exporting to a delimited text file.

▪ Since psql is a client utility, all path references are relative to the client while the SQL version is relative to the server and runs under the context of the postgres OS process account. We detail the differences between the two in Import Fixed-width Data in PostgreSQL with just psql.

▪ pgAdmin (a.k.a. pgAdmin III or pgAdmin3) is the current rendition of the most commonly used graphical administration tool for PostgreSQL.

▪ Since it’s accepted as the official graphical administration tool for PostgreSQL, and packaged with many binary distributions of PostgreSQL,

▪ pgAdmin has the responsibility to always be kept in sync with the latest PostgreSQL releases. Should a new release of PostgreSQL induct new features, you can count on the latest pgAdmin to let you manage it.

▪ Get pgAdmin at http://www.pgadmin.org.

▪ While on the site, you may opt to peruse one of the guides that’ll introduce pgAdmin, but the tool is well-organized and, for the most part, guides itself quite well

▪ Graphical EXPLAIN plan for your queries. This most awesome feature offers a pictorial insight into what the query planner is thinking. Gone are the days of trying to wade through the verbosity of text-based planner outputs.

▪ SQL pane. pgAdmin ultimately interacts with PostgreSQL via SQL; it’s not shy about letting you see the generated SQL. When you use the graphical interface to make changes to your database, the underlying SQL to perform the tasks automatically displays in the SQL pane.

▪ For SQL novices, studying the generated SQL is a great learning opportunity.

▪ Data export. pgAdmin can easily export query results as CSV or other delimited format

▪ Backup and restore wizard. Can’t remember the myriad of commands and switches to perform a backup or restore using pg_restore and pg_dump? pgAdmin has a nice interface that’ll let you selectively back up and restore databases, schemas, single tables, and globals, and the message tab shows you the command line pg_dump or pg_restore it used to do it.

▪ Grant Wizard. This time-saver will allow you to change permissions on many database objects in one fell swoop.

▪ pgAdmin’s tree layout is intuitive to follow but does start off showing you every esoteric object found in the database

▪ pgAdmin does not always keep the tree in sync, with current state of the database. For example, if one person alters a table, the tree for a second person will not automatically refresh.

▪ There is a setting in recent versions that forces an automatic refresh if you check it, but may slow things down a bit.

▪ If you click on the plugin menu item as shown in Figure 4-3 and then psql, this will open a psql session connected to the database you are currently connected to in pgAdmin.

▪ Since this feature relies on a database connection, you’ll see it disabled until you’re connected to a database.

▪ To edit configuration files directly from pgAdmin, you need to have the admin pack extension installed on your server.

▪ Creating a database in pgAdmin is simple. Just right-click on the database section of the tree and choose New Database as shown in Figure 4-6.

▪ For setting permissions on existing objects, nothing beats the pgAdmin Grant Wizard, which you can access from the Tools→Grant Wizard menu of pgAdmin

▪ As with many other features, this option is greyed out unless you are connected to a database. It’s also sensitive to the location in the tree you are on. For example, to set permissions in objects located in the census schema, we select the census and then choose the Grant Wizard.

▪ More often than setting permissions on existing objects, you may want to set default privileges for new objects in a schema or database. To do, so right-click the schema or database, select Properties, and then go to the Default Privileges
tab and set permissions for the desired object types as shown in Figure 4-8.

▪ If your server is remote or your databases are huge, we recommend using the command-line tools for backup and restore instead of pgAdmin to avoid adding another layer of complexity in what could already be a pretty lengthy process.

▪ To back up selective objects right-mouse click on the object you want to back up and select Backup

▪ One of the great gems in pgAdmin is its informative, at-a-glance graphical explain of the query plan. You can access the graphical explain plan by opening up an SQL query window, write some query and then clicking on the ￼ icon.

▪ The best tip we can give for reading the graphical explain plan is to follow the fatter arrows. The fatter the arrow, the more time consuming a step.

▪ pgAgent is a handy utility for scheduling jobs.

▪ Since pgAgent can execute batch scripts in the OS, we use it for much more than scheduling PostgreSQL jobs

▪ You can download pgAgent from pgAgent Download. The packaged SQL install script will create a new schema named pgAgent in the postgres database and add a new section to your pgAgmin.

▪ This is often due to permission issues. pgAgent always runs under the context of the account the pgAgent service is running under

▪ Each scheduled job has two parts: the execution steps and the schedule to run

▪ For each step, you can enter SQL to run, point to a shell script on the OS, or even cut and paste in a full shell script

▪ The syntax for the SQL will not vary across OS

▪ Steps run in alphabetical order and you can decide what kind of actions you wish to take upon success or failure of each individual step

▪ pgAgent really consists of two parts: the data defining the jobs and storing the job logging

▪ PostgreSQL supports the workhorse data types of any database: numerics, characters, dates and times, booleans, and so on.

▪ Strictly speaking, serial is not a data type in its own right. Serial and its bigger sibling bigserial are auto-incrementing integers

▪ In PostgreSQL, each data type, including custom types you build, has a companion array type. For example, integer has an integer array type integer[], character has a character array type character[], and so forth.

▪ If you try to access an element above the upper bound, you won’t get an error—only NULL will be returned.

▪ PostgreSQL also supports array slicing using the start:end syntax.

▪ And to glue two arrays together end to end, we simply use the concatenation operator as follows:

SELECT fact_subcats[1:2] || fact_subcats[3:4] FROM census.lu_fact_types;

▪ People have different opinions as to whether you should abandon the use of varchar and just stick with text.

▪ Performance-wise, there is no speed benefit with using character over varchar in PostgreSQL.

▪ The most common manipulations done to strings is to pad, trim off white space, and extract substrings.

▪ PostgreSQL is the only database that we know of that offers table inheritance

▪ All structural changes made to the parent will automatically propagate its child tables. To save you even more time, whenever you query the parent, all rows in the children are included as well.

▪ For ephemeral data that could be rebuilt in event of a disk failure or don’t need to be restored after a crash, you might prefer having more speed over redundancy. In 9.1, the UNLOGGED modifier allows you to create unlogged tables. These tables will not be part of any write-ahead logs. Should you accidentally unplug the power cord on the server, when you turn back the power, all data in your unlogged tables will be wiped clean during the roll-back process.

▪ Let’s say we now need to add a phone number to all our tables. We simply have to run the following command to alter the underlying type:

ALTER TYPE app_user ADD ATTRIBUTE main_phone varchar(18) CASCADE;

▪ Normally, you can’t change the definition of a type if tables depend on that type. The CASCADE modifier allows you to override this restriction.

▪ PostgreSQL syntax pretty much abides by the ANSI-SQL standards for adding data, but it does have some lagniappes not always found in many other databases, one of which is a multi-row constructor that can be used to insert more than one record at a time

▪ It’s much like a single row INSERT VALUES()
syntax except you can add more than one row at a time.

▪ We’ll be using the new DO command, which allows you to write a piece of procedural language code on the fly.

▪ Think of schemas as another level of organization for database objects. We use it liberally to group our tables into logical units.

▪ You can have two tables with the same name as long as they are in separate schemas. To distinguish between them, you must prepend the schema name.

▪  Insert using DO to generate dynamic SQL

▪ DO language plpgsql
$$
DECLARE var_sql text;
BEGIN
var_sql :=

▪ We’ll start off with something familiar to most relational folks: foreign key, unique, and check constraints before moving onto exclusion constraints introduced in 9.0.

▪ PostgreSQL follows the same convention as most databases you may have worked with that support referential integrity

▪ Unlike primary key and unique constraints, PostgreSQL doesn’t automatically create an index for foreign key constraints; you need to do this yourself.

▪ Each table can have no more than a single primary key

▪ Should you need to enforce uniqueness on other columns, you must resort to unique constraints. Adding a unique constraint automatically creates an associated unique index. Unlike a primary key, a column with unique constraints can still be populated with NULLs.

▪ Having a unique constraint doesn’t qualify a column to participate in a foreign key relationship.

▪ Check constraints are conditions that must be met for a field or set of fields for each row.

▪ ALTER TABLE logs ADD CONSTRAINT chk_lusername
CHECK (user_name = lower(user_name));

▪ PostgreSQL comes with a superbly flexible index framework

▪ At time of writing, PostgreSQL comes with at least four types of indexes.

▪ Should you find these insufficient, you can define new index operators and modifiers to work on top of these. If still unsatisfied, you’re free to create your own index type.

▪ To take full advantage of all that PostgreSQL has to offer, you’ll want to understand the various types of indexes and what they can and can’t be used for

▪ B-tree is the index you’ll find most common in any relation database

▪ B-tree is designed to be a general purpose type of index. You can usually get by with just this one alone if you don’t want to experiment with additional types.

▪ If PostgreSQL automaticaly creates an index for you or you don’t bother picking the type, B-tree will be chosen.

▪ It is currently the only index type allowed for primary key and unique indexes.

▪ Generalized Search Tree (GiST) is an index type optimized for full text search, spatial data, astronomical data, and hierarchical data.

▪ You can’t use it to enforce uniqueness, however, you can use it in exclusion constraints.

▪ Generalized Inverted Index (GIN) is an index type commonly used for the built-in full text search of PostgreSQL and the trigram extensions.

▪ GIN indexes are generally faster to search than GiST, but slower to update.

▪ PostGIS 2.1 spatial extension has planned support for it. The only types built-in that currently have support for it are the built-in PostgreSQL geometry types like point and box and text.

▪ Hash is an index that was popular before GiST and GIN came along. General consensus is that GiST and GIN outperform and are more transaction safe than hash

▪ PostgreSQL has relegated hash to legacy status. You may encounter this index type in other databases, but it’s best to avoid it in PostgreSQL.

▪ Operator classes support a given set of operators. In short, an operator can utilize an index only if the operator class for that index supports it.

▪ For example, many B-tree operator classes support =, >= but not pattern operations like ~>~.

▪ Each data type comes with a default operator class. For instance, the default opclass for varchar is varchar_ops, which includes operators such as =, >, and < but no support for pattern operations.

▪ If you create an index without being explicit about the opclass(es) to be used, the default for the data type(s) being indexed would automatically be picked.

▪ CREATE INDEX idx_bt_my_table_description_varchar_pattern ON my_table
USING btree (description varchar_pattern_ops);

▪ PostgreSQL has a feature called functional indexes, which you won’t often find in other databases. A more common parallel you’ll see in other databases like Microsoft SQL Server or MySQL are computed columns and the ability to place indexes on computed columns.

▪ PostgreSQL didn’t buy into the idea of computed columns since views are more appropriate places for them. To still reap the speed advantage of indexes, PostgreSQL lets you place indexes on functions of columns.

▪ A classic example where you’d want to employ a functional index is for dealing with mixed case text. PostgreSQL is a case-sensitive database, so to be able to search using an index when casing doesn’t matter; you can create an index as follows:

CREATE INDEX idx_featnames_ufullname_varops ON featnames_short
USING btree (upper(fullname) varchar_pattern_ops);

▪ Partial indexes (read more about them here: http://www.postgresql.org/docs/current/interactive/indexes-partial.html) are indexes that only index that portion of data fitting a specific WHERE condition

▪ The main caveat with partial indexes is that you must use the same WHERE condition when you created the index in your query to activate the index.

▪ An easy way to ensure that your partial index will always be used is to use a view when querying the data.

▪ To ensure our index is always used for active subscriptions, we can create a view with the built-in condition and always use this view when querying active subscriptions:

CREATE OR REPLACE VIEW vw_active_subscribers AS
SELECT id, lower(user_name) As user_name
FROM allsubscribers WHERE deact_dt IS NULL;

▪ To ensure index usage, we always query against our view as follows:

SELECT * FROM vw_active_subscribers WHERE user_name = 'sandy';

▪ PostgreSQL, like many other databases, supports compound indexes, a.k.a. multicolumn indexes. Compound indexes allow you to combine multiple columns or functions on columns into one index.

▪ PostgreSQL is one of the most ANSI-SQL compliant databases on the market. It even supports many of the additions introduced with the SQL:2006+ standard.

▪ Like most relational databases, PostgreSQL supports views. Some things have changed over the years on how views work and how you can update the underlying tables via updates on views

▪ In PostgreSQL 9.1, the preferred way of updating data via a view is to use INSTEAD OF
triggers instead of rules, though rules are still supported.

▪ Unlike Microsoft SQL Server and MySQL, simple views are not automatically updatable and require writing an instead-of rule or trigger to make them updatable. On the plus side, you have great control over how the underlying tables will be updated.

▪ Views are most useful for encapsulating common joins.

▪ CREATE OR REPLACE VIEW census.vw_facts AS
SELECT lf.fact_type_id, lf.category, lf.fact_subcats, lf.short_name
, f.tract_id, f.yr, f.val, f.perc
FROM census.facts As f
INNER JOIN census.lu_fact_types As lf
ON f.fact_type_id = lf.fact_type_id;

▪ We first define the trigger function(s). There is no standard in naming of the functions and a trigger function can be written in any language that supports triggers.

▪  Trigger function for vw_facts to update, delete, insert

CREATE OR REPLACE FUNCTION census.trig_vw_facts_ins_upd_del() RETURNS trigger AS
$$
BEGIN
IF (TG_OP = 'DELETE') THEN ￼
DELETE FROM census.facts AS f
WHERE f.tract_id = OLD.tract_id AND f.yr = OLD.yr AND f.fact_type_id = OLD.fact_type_id;
RETURN OLD;
END IF;
IF (TG_OP = 'INSERT') ￼ THEN
INSERT INTO census.facts(tract_id, yr, fact_type_id, val, perc)
SELECT NEW.tract_id, NEW.yr, NEW.fact_type_id, NEW.val, NEW.perc;
RETURN NEW;
END IF;
IF (TG_OP = 'UPDATE') THEN
IF ROW(OLD.fact_type_id, OLD.tract_id, OLD.yr, OLD.val, OLD.perc) ￼
!= ROW(NEW.fact_type_id, NEW.tract_id, NEW.yr, NEW.val, NEW.perc) THEN
UPDATE census.facts AS f ￼
SET tract_id = NEW.tract_id, yr = NEW.yr
, fact_type_id = NEW.fact_type_id
, val = NEW.val, perc = NEW.perc
WHERE f.tract_id = OLD.tract_id
AND f.yr = OLD.yr
AND f.fact_type_id = OLD.fact_type_id;
RETURN NEW;
ELSE
RETURN NULL;
END IF;
END IF;
END;
$$
LANGUAGE plpgsql VOLATILE;

▪ Next, we bind the trigger function to the view as shown in Example 7-3.

▪ CREATE TRIGGER trip_01_vw_facts_ins_upd_del
INSTEAD OF INSERT OR UPDATE OR DELETE ON census.vw_facts
FOR EACH ROW EXECUTE PROCEDURE census.trig_vw_facts_ins_upd_del();

Now when we update, delete, or insert into our view, it will update the underlying facts table instead:

▪ Although we have just one trigger function to handle multiple events, we could have just as easily created a separate trigger and trigger function for each event.

▪ Window functions are a common ANSI-SQL feature supported in PostgreSQL since 8.4.

▪ A window function has the unusual knack to see and use data beyond the current row, hence the term window

▪ Without window functions, you’d have to resort to using joins and subqueries to poll data from adjacent rows

▪ Here’s a quick example to get started. Using a window function, we can obtain the average value for all records with fact_type_id of 86 in one simple SELECT.

Example 7-4. The basic window

SELECT tract_id, val, AVG(val) OVER () as val_avg
FROM census.facts WHERE fact_type_id = 86;

▪ Notice how we were able to perform an aggregation without having to use GROUP BY

▪ When PostgreSQL sees a window function in a particular row, it will actually scan all rows fitting the WHERE clause, perform the aggregation, and output the value as part of the row.

▪ Other databases tend to limit window functions to using built-in aggregates like AVG(), SUM(), MIN(), MAX() etc.

▪ Although PostgreSQL is fairly ANSI-SQL compliant, it does have a few unique constructs you probably won’t find in other databases

▪ The ON modifier can take on multiple columns, all will be considered to determine uniqueness.

▪ Finally, the ORDER BY
clause has to start with the set of columns in the DISTINCT ON
, then you can follow with your preferred ordering.

▪ LIMIT and OFFSET are clauses in your query to limit the number of rows returned. They can be used in tandem or separately. These constructs are not unique to PostgreSQL and are in fact copied from MySQL. You’ll find it in MySQL and SQLite and probably various other databases.

▪ An OFFSET of zero is the same as leaving out the clause entirely. A positive offset means start the output after skipping the number of rows specified by the offset. You’ll usually use these two clauses in conjuction with an ORDER BY
clause.

▪ ANSI-SQL specs define a construct called CAST, which allows you to cast one data type to another

▪ As with most databases, you can string a series of SQL statements together and treat them as a unit. Different databases ascribe different names for this unit—stored procedures, modules, macros, prepared statements, and so on. PostgreSQL calls them functions.

▪ Aside from simply unifying various SQL statements, these units often add the capability to control the execution of the SQL statements through using procedural language (PL).

▪ Regardless which language you choose to write a particular function, they all share a similar structure.

▪ CREATE OR REPLACE FUNCTION func_name(
arg1 arg1_datatype)
RETURNS some_type | setof sometype | TABLE (..) AS
$$
BODY of function
$$
LANGUAGE language_of_function

▪ Functional definitions can include additional qualifiers to optimize execution and to enforce security

▪ LANGUAGE has to be one you have installed in your database. You can get a list with the query: SELECT lanname FROM pg_language;

▪ VOLATILITY defaults to VOLATILE if not specified. It can be set to STABLE, VOLATILE, or IMMUTABLE. This setting gives the planner an idea if the results of a function can be cached

▪ STABLE means that the function will return the same value for the same inputs within the same query.

▪ VOLATILE means the function may return something different with each call, even with same inputs. Functions that change data or are a function of other environment settings like time, should be marked as VOLATILE.

▪ IMMUTABLE means given the same inputs the function is guaranteed to return the same result

▪ The volatility setting is merely a hint to the query planner. It may choose to not cache if it concludes caching is less cost effective than recomputation.

▪ STRICT. A function is assumed to be not strict unless adorned with STRICT

▪ A strict function will always return NULL if any inputs are NULL and doesn’t bother evaluating the function so saves some processing.

▪ When building SQL functions, you should be careful about using STRICT as it will prevent index usage as described in STRICT on SQL Functions

▪ COST is a relative measure of computational intensiveness. SQL and PL/pgSQL functions default to 100 and C functions to 1. This affects the order functions will be evaluated in a WHERE clause and also the likeliness of caching. The higher the value, the more costly the function is assumed to be.

▪ ROWS is only set for set returning functions and is an estimate of how many rows will be returned; used by planner to arrive at best strategy

▪ SECURITY DEFINER
is an optional clause that means run under the context of the owner of the function. If left out, a function runs under the context of the user running the function. This is useful for giving people rights to update a table in a function but not direct update access to a table and also tasks that normally require super user rights.

▪ Function languages can be divided into two levels of trust. Many—but not all—languages offer both a trusted and untrusted version

▪ Trusted—Trusted languages are languages that don’t have access to the filesystem beyond the data cluster and can’t execute OS commands. They can be created by any user. Languages like SQL, PL/pgSQL, PL/Perl are trusted. It basically means they can’t do damage to the underlying OS.

▪ Untrusted—Untrusted languages are those that can interact with the OS and even call on webservices or execute functions on the OS. Functions written in these languages can only be created by super users, however, a super user can delegate rights for another user to use them by using the SECURITY DEFINER
setting.

▪ By convention, these languages have a u at the end of the name to denote that they’re untrusted—for instance, PL/PerlU, PL/PythonU.

▪ Writing SQL functions[2] is fast and easy. Take your existing SQL statements, add a functional header and footer, and you’re done. The ease does mean you’ll sacrifice flexibility

▪ You won’t have fancy control languages to create conditional execution branches. You can’t have more than one SQL statement (though you can wrap multiple into a CTE or subqueries to achieve same result). More restrictively, you can’t run dynamic SQL statements that you piece together based on parameters as you can in most other languages.

▪ On the positive side, SQL functions are often inlined by the query planner into the overall plan of a query since the planner can peek into the function. Functions in other languages are always treated as blackboxes. Inlining allows SQL functions to take advantage of indexes and collapse repetitive computations.

▪ When your functional needs exceed reaches beyond SQL, PL/pgSQL is the most common option

▪ PL/pgSQL stands apart from SQL in that you can declare local variables using DECLARE, you can have control flow, and the body of the function needs be enclosed in a BEGIN..END block.

▪ PostgreSQL automatically converts PostgreSQL datatypes to Python datatypes and back

▪ You can use PL/Python to write triggers and create aggregate functions.

▪ Python allows you to perform feats that aren’t possible in PL/pgSQL.

▪ Recall that PL/Python is an untrusted language without a trusted counterpart. This means it’s capable of interacting with the filesystem of the OS and a function can only be created by super users.

▪ No database of merit should be without triggers to automatically detect and handle changes in data

▪ Triggers can be added to both tables and views.

▪ PostgreSQL offers both statement-level triggers and row-level triggers. Statement triggers run once per statement, while row triggers run for each row called.

▪ More distinction is made between a BEFORE, AFTER, and INSTEAD OF
trigger.

▪ A BEFORE trigger fires prior to the execution of the command giving you a chance to cancel and change data before it changes data.

▪ An AFTER trigger fires afterwards giving you a chance to retrieve revised data values. AFTER triggers are often used for logging or replication purposes.

▪ The INSTEAD OF
triggers run instead of the normal action. INSTEAD OF
triggers can only be used with views. BEFORE and AFTER triggers can only be used with tables.

▪ PostgreSQL offers specialized functions to handle triggers. These trigger functions act just like any other function and have the same basic structure as your standard function.

▪ Where they differ are in the input parameter and the output type. A trigger function never takes a literal input argument though internally they have access to the trigger state data and can modify it.

▪ They always output a datatype called a trigger. Because PostgreSQL trigger functions are just another function, you can reuse the same trigger function across different triggers.

▪ To apply multiple triggering functions, you must create multiple triggers against the same event. The alphabetical order of the trigger name determines the order of firing and each trigger passes the revised trigger state data to the next trigger in the list.

▪ You can use almost any language to write trigger functions, with SQL being the notable exception

▪ Our example below uses PL/pgSQL, which is by far the most common language for writing triggers.

▪ You will see that we take two steps: First, we write the trigger function. Next, we attach the trigger function to the appropriate trigger, a powerful extra step that decouples triggers from trigger functions.

▪ CREATE OR REPLACE FUNCTION trig_time_stamper() RETURNS trigger AS ￼
$$
BEGIN
NEW.upd_ts := CURRENT_TIMESTAMP;
RETURN NEW;
END;
$$
LANGUAGE plpgsql VOLATILE;

CREATE TRIGGER trig_1
BEFORE INSERT OR UPDATE ￼ OF session_state, session_id ￼
ON web_sessions ￼
FOR EACH ROW
EXECUTE PROCEDURE trig_time_stamper();

▪ This is a new feature introduced in PostgreSQL 9.0+ that allows us to limit the firing of the trigger only if specified columns have changed

▪ Aggregates are another type of specialized function offered up by PostgreSQL

▪ In many other databases, you’re limited to ANSI-SQL aggregate functions such as MIN(), MAX(), AVG(), SUM(), and COUNT(). You can define your own aggregates in PostgreSQL.

▪ Don’t forget that any aggregate function in PostgreSQL can be used as a window function. Altogether this makes PostgreSQL the most customizable database in existence today.

▪ You can write aggregates in almost any language, SQL included

▪ An aggregate is generally composed of one or more functions

▪ It must have at least a state transition function to perform the computation and optional functions to manage initial and final states

▪ You can use a different language for each of the functions should you choose

▪ The final function is optional, but if specified must take as input the result of the state function

▪ Our transition state function, as shown in Example 8-10, takes two inputs: the previous state passed in as a one-dimensional array with two elements and also the next element in the aggregation process. If the next element is NULL or zero, the state function returns the prior state

▪ Sooner or later, we’ll all face a query that takes just a bit longer to execute than what we have patience for

▪ The best and easiest fix to a sluggish query is to perfect the underlying SQL, followed by adding indexes, and updating planner statistics.

▪ The easiest tool for targeting query performance problems is using the EXPLAIN and EXPLAIN ANALYZE
commands

▪ Perhaps the most exciting enhancement for the common user came when pgAdmin introduced graphical EXPLAIN several years back. With a hard and long stare, you can identify where the bottlenecks are in your query, which tables are missing indexes, and whether the path of execution took an unexpected turn.

▪ EXPLAIN will give you just an idea of how the planner intends to execute the query without running it. EXPLAIN ANALYZE
will actually execute the query and give you comparative analysis of expected versus actual.

▪ Writing efficient SQL takes practice. There’s no such thing as a wrong query as long as you get the expected result, but there is such a thing as a slow query.

▪ PostgreSQL stores large blob and text objects using TOAST (The Oversized-Attribute Storage Technique). TOAST maintains side tables for PostgreSQL to store this extra data. 
