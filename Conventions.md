<h1>Conventions</h1>
This is an outline of how code should be written and submitted to the codebase.
The following is subject to change as the team decides what specifically should be followed.
<h2>Comments</h2>
Every class, function, significant block of code, edit, and file should have a descriptive comment.
Files should start with a header describing what the file is for and who worked on it.

```Python
'''
This is an example file header. State its purpose, etc.
Authors:
James Meyers
'''
```

Classes and functions should give a short description, as well as descriptions for parameters and it's return.
Note that obvious functions (ie, getter and setter functions) do not need descriptions. Be sure to include both parameter types and return types to your functions.

```Python
class CoolClass(Cooler):
    '''
    Example class
    Inherits Cooler class
    param1 : Useful description
    '''
    
    def __init__(self,param1: type):
        self.param1 = param1

    def addValue(self,param2: type) -> type:
        '''
        adds given number to param
        param2 : Useful description
        '''
        return param1 + param2
```

Significant code blocks should be given comments for clairity.

```Python
#Joins strings from given lists 'A' and 'B' depending on conditions from list 'C'
gross = ''.join([ ( A[i], B[i] )[ C[i] ] for i in range( len(C) ) ])
```
Edits to existing files should be commented to help track changes. This should include who made the change and what it changes. Use double '#' to make it easier to diferentiate. Make sure to get rid of the comment after the PR is approved, so it does no clutter the code. Example:

```Python
##James Meyers, deleted everything.
```

<h2>Naming</h2>
Variables, functions, and classes should be named in a similar way so they can be quickly identified. Names should also be descriptive of what they are used for.

```Python
STATIC_VARIABLE = None

class ClassName:
    def __init__(self,parameterName : type):
        self.variableName = parameterName
    
    def methodName(self):
        pass
    
    def getVariable(self):
        return self.variable
    def setVariable(self,value: type):
        self.variable = value
```

<h2>Code Base</h2>
When pushing a file to the code base, please get another team member to review your code ensuring it works and follows conventions.

* If it is a **new** file it can be safely added to the **main branch**.
* If it is **modifying** an existing file: **fork it** into it's own branch.

The team should occasionally review and merge branches to the main code when necessary.
    
