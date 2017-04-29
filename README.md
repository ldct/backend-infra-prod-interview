# Notes on Backend/Infrastructure/Production Interview

- Consistency
Transactions
mysql transactions
Elasticsearch, what problems I ran into
A lot of problem solving latency, data etc
Database -> build full text search on top of database (independently)
Overview of different datastores, sql, mongo (document), postgres, mysql
pros and cons of different databases
elastic search how does it differ from typical databases
memcache and redis how does it different from other datastore
high volume data, hadoop, bigtable
why would I use hadoop? went would hadoop be bad?

memory swapping, when program uses too much memory, uses disc as memory temporarily
processes and threads
database indexing, creates a BST usually to search, BST only contains the indexed col / val
important field not being indexed with have a very slow query
index, updating and reading is log(n)
adding to a sql db this not indexed, o(1) but reading will be o(n) and updating will be o(n)
Diagnose a Slow Query
Make sure querying on indexed stuff
keep a log of queries that are really slow, try to avoid them
monitor query speed, track how long query takes (avg request, 20 ms on db, 10ms on web server, 20 ms network latency)



debugging slow code
I/O bound vs CPU bound
where the bottleneck is, is it in processing or in I/O, “ $ top “, to check if CPU bottleneck or I/O


scale from one machine to many
distributed system
store multiple databases, modularizing, scaling
slow web server, have many web servers connecting to one database
i.e 30 web servers, 
load balance, 
how to split db across multiple machines, if one machine cannot take all the space
split by row or by column
vertical sharding vs horizontal sharding
mirroring a database
read heavy vs write heavy workload
different database structure
read heavy
1 master db, replicated to several
write to master, then copy master to several
write heavy
dont index slower to update
log structure merge tree (append in o(1))

what kind of challenges does yelp face????

geographical

find restaurants in my city
	google map api
	quad tree
		start with large area
		set of restaurants
		query within polygon
		traditional db is kinda bad
		recursively start
		postgres has built in geographical data structure stuff or extension?	


read and write heavy?

twitter question
	two ways to design twitter
		store timeline of each user separately
		user 1, user 2 and user 3 all follow person x
		when person x tweets, we add the tweet to person x’s timeline + user 1,2,3  			(pointer to tweet)
		other
		dont precompute timeline
		generate timeline on login, I follow these x people, collect tweets from these 			people and sorta chronologically
		




Theoretical knowledge

OS

https://www.amazon.com/Operating-System-Concepts-Abraham-Silberschatz/dp/0470128720
https://www.amazon.ca/Advanced-Programming-UNIX-Environment-3rd/dp/0321637739

Networks

TCP/IP site (TBD)
https://www.amazon.ca/Computer-Networks-5th-Andrew-Tanenbaum/dp/0132126958

Performance

https://www.amazon.com/Systems-Performance-Enterprise-Brendan-Gregg/dp/0133390098/ref=asap_bc?ie=UTF8
