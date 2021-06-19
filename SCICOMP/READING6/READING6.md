# Software Design Patterns

## Software design

### Separation of concerns

Exercise: In the above program, identify and describe at least two of the sub-problems which are solved multiple times. (I see at least three or four.)

- I would divide this program into two subprograms. The first subroutine receives the data, the second processes it. The fact that this is now happening in one script is wrong.
- There are no checks. Checks are required for the parameters entered. For example on the operation parameter.
- Also users are not informed that you can not enter fractional numbers. 
- There is no "else" processing without parameters.


Exercise: Choose one of the sub-problems, write a common solution to that subproblem in the form of a function, and modify the program to use your common solution instead of solving the problem multiple times.

```python
def get_data():
    x = float(input("Tell me the first number: "))
    y = float(input("Tell me the second number: "))
    allowed_operations = ['add', 'multiply']
    typed_operation = None
    while typed_operation not in allowed_operations:
        typed_operation = input("tell me the operation (add, multiply): ")
    
    return x, y, typed_operation


def process_data(x, y, op):
    result = None
    if op == "add":
        result = x + y
    elif op == "multiply":
        result = x * y
    else:
        raise "Operation error"
    return result


def main():
    x, y, op = get_data()
    result = process_data(x=x, y=y, op=op)
    if result is not None:
        print('result is ', result)
    else:
        print('Some error with result')

if __name__ == '__main__':
    main()
```