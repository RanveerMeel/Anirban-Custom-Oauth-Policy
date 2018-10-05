This policy is helful with Mule Application that has RAML specification in it.
This policy can be used to protect each RAML resources with scopes defined in it. An exampke test.raml is provided here.
This policy also works with non-RAML applications.
Plenty of options given to the users to select if they want to work non-RAML applications. If they don't, they can simply un-check the option
"Allow NonRaml application" and in that case, any non-RAML applications will not work with this policy. It will show error message that application
doesn't have RAML specification. The message will be :- "Cannot find RAML configuration in Application"

If "Allow NonRaml application" option is selected by users, then it will work with any non-RAML applications.

Since a non-RAML application doesn't have scopes defined in it's resources and url as in RAML application, the policy will validate the scope for this 
non-RAML applications with the scope mentioned in the policy configuration. 

If no scope is mentioned in the policy configuration and left blank, then no scope validation will happen for this non-RAML application and only token will be validated.


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