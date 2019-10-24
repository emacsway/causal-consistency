# MongoDB

## paper

- mongoDB@SIGMOD2019 

## satisfied model

- strong causal convergence (SCCv) **?**

## system model

- shared clusters
  
  * each shard represents a horizontally partitioned set of data (non-overlapping *key* domains)

  * each shard has a primary and one or more secondary nodes

     * primary node: receive and compute all writes  
    
     * secondary node: replica all writes from the primary node in the same shard. 
     
- routers: route client commands, not hold data 
  
- clients: application processes
  

## implementation

### logical clock
  
- clustertime

  * content
      
      * hybrid logic clock: <*time, counter*>

          * *time*: physical time

          * *counter*: deal with the case where writes have   the same *time* part

  * ticks for a new write (only on primary node) <*t,c*> 
    
      * computes the current physical time (*lc*)    

      * compare the received clustertime (*rc*) with the local one (*lc*)
    
          * *rc > lc*
          
              *  set *t* as *rc.time*; 

              *  set the *c* as *rc.counter +1*
      
          * *rc <= lc*
        
              *  set *t* as *lc*
              
              *  set *c* as 0   

  * distribution
  
      * primary node receives a write *w1* from client *c1*
          
          * advances its clustertime, if the received one is greater
          
          * ticks a new clustertime *t1*
          
          * adds the *w1* with *t1* to the *oplog*

          * returns *w1* with *t1* to the client *c1*

      * client receives the ack of *w1* from the primary node 

          * advances the local clustertime to *t1*  
  
### causal dependency 

- shard receives a read request (including the eaxct written time *wt* of *key*) from a client
  
  * shard has the *key* 

    * primary node: returns the value 
  
    * secondary node: checks its *oplog* 
      
      * has the data with *wt*: returns results
    
      * has no data with *wt*: waits for the replication from the primary node; returns until it is replicated
  
  * shard contains no such *key*
    
      * **?** router should route the request to the shard which has the *key*, this case should not happen
