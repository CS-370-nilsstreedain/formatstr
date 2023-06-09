# Format String Vulnerability
Please proceed to the `formatstr` folder.

You will be exploiting the format string vulnerability to get the flag.

Your job is to provide malicious input to the program `launcher`. Here is the source code of this program:
```c++
char *trueflag = "{HIDDEN}";
char buff[64];

void process_user_input(void) {
  char *flag = trueflag;
  char *pref = "cs370";

  // get your input
  printf("Your flag address: %p\n", flag);
  printf("Your pref address: %p\n", pref);
  printf("Your buff address: %p\n", buff);
  printf("Enter the input to print out: ");
  if (fgets(buff, 64, stdin) == NULL)
    return;

  // print out the buffer
  printf(buff);
}

int main(void) { ... process_user_input(); }
```
Once you run it, the program will wait for your input (that will be used as the first argument of printf function). You have two jobs here: (1) find out the memory addresses where the pref and flag are (HINT: you can use `%p %p ..` to inspect where each memory address points to) and (2) use the addresses that you figured out to print the flag.

If you are successful, you will have the flag.

Good luck.
