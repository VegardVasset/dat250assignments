# Technical report

Link to fork: https://github.com/VegardVasset/dat250expass2

## Experiment 1: JPA tutorial
forking the repository, cloning it to my machine, was fairly easy.
I also ran Main without errors, and created the new package relationshipexample.
And three classes inside it, Family, Job and Person without errors.

The file persistence.xml is configured to automatically map them to database tables
using Hibernate. The appliacation is using the H2 database, which is a in-memory database.
It will create a file named DB.mv.db in the root of the project, which is the database file.
The property hibernate.connection.url specifies the JDBC URL for connecting to the H2 database

The getters and setters in the classes are generated by lombok, which is a library that
generates getters and setters for you. It also generates constructors, toString, equals and hashCode.

## Experiment 2: JPA associations

Started of by activating the automatic tests on commmit under the actions tab in github.
Then i implemented the domain model for the credit card example and ran the tests to verify that they worked.
In order to implement the domain model I had to take into account the relations
between the classes. I used the @OneToMany and @ManyToOne annotations to specify the relations.
I sometimes used lombok to generate getters and setters and sometimes I wrote them myself in order
for the names to match the tests.

The database here is the same as described in the above experiment.
When the application starts it will initiallize and manage the database. JPA will
create the tables and columns for the classes based
on entetity classes and configuration. In order to
view what sql queries are generated bewi go into the persistence.xml file and change
the property hibernate.show_sql to true. Here is the sql query for creating the table Customer
```sql 
    create table Customer (
        id bigint generated by default as identity,
        name varchar(255),
        primary key (id)
    )
```

Inspecting the database schema proved to be a bit problematic I tried to access the H2 console
but I could not get it to work. For some unknown reason i could not manage to log in
to the console with the credentials I specified in the persistence.xml file. I also tried using
the IntelliJ database tool but I could not get that to work either so this is a pending
issue. So instead of viewing a database schema I used the hibernate.show_sql property to view the sql queries
and checked that it looks like what I expected. 