Any additional parameter in scope will be rejected

example: 
config: READ_BOOKSHELF WRITE_BOOKSHELF ABC
Actual scope from HTTP: READ_BOOKSHELF WRITE_BOOKSHELF

result:Rejected
/////////////////////////////////////////

config: READ_BOOKSHELF WRITE_BOOKSHELF 
Actual scope from HTTP: READ_BOOKSHELF WRITE_BOOKSHELF

result:Accepted
//////////////////////////////////////////////

config: READ_BOOKSHELF
Actual scope from HTTP: READ_BOOKSHELF WRITE_BOOKSHELF

result:Accepted
//////////////////////////////////////////////

config: WRITE_BOOKSHELF 
Actual scope from HTTP: READ_BOOKSHELF WRITE_BOOKSHELF

result:Accepted
////////////////////////////////////////////////

config: READ_BOOKSHELF
Actual scope from HTTP: READ_BOOKSHELF

result:Accepted
/////////////////////////////////////////////////

config: READ_BOOKSHELF
Actual scope from HTTP: WRITE_BOOKSHELF

result:Rejected