Real-Time high (throughput)(=Items amount passing through a system in unit time, Operations per second) data streaming. Seeing the Cases of zomato and discord Databses like mongo and postgres have very less htroughput , if given under high through put they shut down ,
Soln kafka: has high thorough , will not down on high OP/s, but not a direct alterntive to DB as faster memory, less storage amount and temporaray storage , kafka mein you cant quet data
Soln: Kafka + DB: \
Data Produceer->Kafka->Consumer(diff services)->DB(bulk insert)
Inside Kafka you have topics(logical partions of data), inside topic you have may multiple partitions but partioning is not dome based on time it is doen based on field .kafka does auto balancing betwencosumers and partitions , consumer gtoups sove this by balancing partions acress gorup members and groups, partition sharing happens first at group level, then at individual level 

