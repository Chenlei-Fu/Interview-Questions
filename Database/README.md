# Database

### Normalization
Normalization is basically to design a database schema such that duplicate and redundant data is avoided. If some piece of data is duplicated several places in the database, there is the risk that it is updated in one place but not the other, leading to data corruption.

There is a number of normalization levels from 1. normal form through 5. normal form. Each normal form describes how to get rid of some specific problem, usually related to redundancy.

Some typical normalization errors:

(1) Having more than one value in a cell. Example:
```
UserId | Car
---------------------
1      | Toyota
2      | Ford,Cadillac
```

(2) Having redundant non-key data (ie. data repeated unnecessarily in several rows). Example:
```
UserId | UserName | Car
-----------------------
1      | John     | Toyota
2      | Sue      | Ford
2      | Sue      | Cadillac
```
This design is a problem because the name is repeated per each column, even though the name is always determined by the UserId.
he problem is solved by splitting the table in two, and creating a primary key/foreign key relationship:

```
UserId(FK) | Car               UserId(PK) | UserName
---------------------          -----------------
1          | Toyota            1          | John
2          | Ford              2          | Sue
2          | Cadillac
```