#### Meaningful names
- Use intention-revealing names
- Avoid disinformation
- Make meaningful distinctions
- Use pronounceable names
- Use searchable names

#### Functions
- small! Functions should be small
- If, else, and while statements should be one line long. Preferably a function
- It is best to have no arguments in a function. A single argument is the next best thing. Two arguments make it hard to work with. More than two should definitely be avoided.
- Output arguments (take in an argument then transforms that argument :void) are harder to understand than inout arguments (take in an argument then return value :prim) 
- Flag arguments are ugly (render(boolean isSuite)). Split it into two functions instead (renderForSuite() and renderForSingleTest())
- SRP - The Single Responsibility Principle states that a function or a class should have only one reason to change. In other words, it should have a single responsibility or concern

#### Rules of simple design
- Do duplication
- Expressive
- Minimal classes & methods