# fib-complex
Calculating requested n-Fibonacci number. This project uses js, react, expressjs, postgresql, redis


 ===================        ==========
 User submits number    =>   React App 
 ===================        ==========
                                 ||
                                 \/
                           -----------------
                             Express Server      
                           -----------------
                           |               |
                           |               |
                     ----------         ----------
                       Redis             Postgres
                     ----------         ----------
                       |    |
                       |    |
                     ----------
                       Worker
                     ----------
                     
1. Redis: Stores all indices and calculated values as key-value pairs
2. Worker: Watches redis for new indicies. Pulls each new index, calculates new value then puts it back into redis
3. Postgres: Stores a permanent list of indices that have been received
