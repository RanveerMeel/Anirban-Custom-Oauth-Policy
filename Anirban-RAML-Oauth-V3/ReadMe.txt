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


Fixed in this version:
- Allow to control nonRaml application to access this policy. We can restrict if we don't want to call nonRaml application.
- Check if there is really a nonRaml application or an individual flow in Raml application that don't use Raml.
- Restrict and control if there is no [securedBy] in Raml config of a particular resource.