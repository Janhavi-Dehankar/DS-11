# DS-11
DS code
#include <stdio.h>
#include <ctype.h>
#include <stdlib.h>

#define SIZE 100
int stack[SIZE];
int top = -1;

void push(int x) {
    stack[++top] = x;
}

int pop() {
    return stack[top--];
}

int main() {
    char exp[SIZE];
    int i, op1, op2, res;
    printf("Enter postfix expression: ");
    scanf("%s", exp);
    for (i = 0; exp[i] != '\0'; i++) {
        if (isdigit(exp[i]))
            push(exp[i] - '0');
        else {
            op2 = pop();
            op1 = pop();
            switch (exp[i]) {
                case '+': res = op1 + op2; break;
                case '-': res = op1 - op2; break;
                case '*': res = op1 * op2; break;
                case '/': res = op1 / op2; break;
            }
            push(res);
        }
    }
    printf("Result: %d\n", pop());
    return 0;
}
