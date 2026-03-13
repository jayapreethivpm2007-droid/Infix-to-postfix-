Infix to Postfix Program (Basic)

def precedence(op):
    if op == '+' or op == '-':
        return 1
    if op == '*' or op == '/':
        return 2
    return 0

def infix_to_postfix(exp):
    stack = []
    result = ""

    for ch in exp:
        if ch.isalnum():
            result += ch
        else:
            while stack and precedence(stack[-1]) >= precedence(ch):
                result += stack.pop()
            stack.append(ch)

    while stack:
        result += stack.pop()

    return result

exp = "A+B*C"
print("Infix:", exp)
print("Postfix:", infix_to_postfix(exp))

Output:
Infix: A+B*C
Postfix: ABC*+
