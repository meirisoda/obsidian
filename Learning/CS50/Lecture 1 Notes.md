```c
if (x < y)
{
	printf("x is less than y\n");
}
else if (x > y)
{
	printf("x is greater than y\n");
}
else
{
	printf("x is equal to y\n");
}
```

```c
char c = get char("Do you agree? ")
	if (c = 'y' || c = 'Y')
	{
		printf("Agreed."\n);
	}
	if (c = 'n' || c = "N")
	{
		printf("Disagreed."\n);
	}
```

## Operations
```c
int counter = 0 
// set counter to 0
```
```c
counter = counter + 1 
counter += 1; 
counter++;
// increase counter by 1 (right to left)
```
```c 
counter--; 
// decrease counter by 1
```

## Loops
### while loop
```c
int counter = 3;
while (counter > 0)
{
	printf("meow\n");
	counter = counter - 1;
}
// say meow 3 times

int i = 3;
while (i > 0) // counting down from 3
{
	printf("meow\n");
	i--;
}

int i = 1; // starting at 1 
while (1 <= 3) // counting up to 3, but it starts at one, so you need to declare that it must equal 3
{
	printf("meow\n");
	i++;
}

int i = 0; // best practice to start at 0
while (i < 3)
{
	printf("meow\n");
	i++;
}
```
### for loop
```c
for (int i = 0; i < 3; i++) // first argument is only done once, and it keeps checking for i, and loops around 
{
	printf("meow\n");
}
```
## Mario
```c
for (int i = 0; i < 4; i++)
{
	printf("?");
}
printf("\n");
```
Output:
```
????
```

```c
if (i = 0; i < 3; i++)
{
	printf
}
```