**There are several differences between HashMap and Hashtable in Java:**

Hashtable is synchronized, whereas HashMap is not. This makes HashMap better for non-threaded applications, as unsynchronized Objects typically perform better than synchronized ones.
Hashtable does not allow null keys or values.  HashMap allows one null key and any number of null values.
One of HashMap's subclasses is LinkedHashMap, so in the event that you'd want predictable iteration order (which is insertion order by default), you could easily swap out the HashMap for a LinkedHashMap. This wouldn't be as easy if you were using Hashtable.
Since synchronization is not an issue for you, I'd recommend HashMap. If synchronization becomes an issue, you may also look at ConcurrentHashMap.  
If you want to make a HashMap thread-safe, use Collections.synchronizedMap()  

**Collision Handling** . 
**Collisions:** Two keys mapping to the same location in the hash table.  
**Separate Chaining** Collisions can be resolved by creating a list of keys that map to the same value.
[explanation](http://www.cs.cmu.edu/~ab/15-121N11/lectures/lecture16.pdf)  
**Linear Probing** h(x, i)=(f(x)+i) mod N (i=1,2,...)  

**Do you Know how HashMap works in Java or How does get () method of HashMap works in Java** . 
But some interviewee definitely answers this and will say HashMap works on the principle of hashing, we have put(key, value) and get(key) method for storing and retrieving Objects from HashMap. When we pass Key and Value object  to put() method on Java HashMap, HashMap implementation calls hashCode method on Key object and applies returned hashcode into its own hashing function to find a bucket location for storing Entry object, important point to mention is that HashMap in Java stores both key and value object as Map.Entry in a bucket which is essential to understand the retrieving logic. 

Read more: http://javarevisited.blogspot.com/2011/02/how-hashmap-works-in-java.html#ixzz4u9ukjMYd . 

[How hashMap works in Java](http://javarevisited.blogspot.de/2011/02/how-hashmap-works-in-java.html)  

**Resize**  
[Resize a hashtable](http://www.vias.org/javacourse/chap19_08.html)  
load factor: the average number of entries per list. If it gets too high, we have to resize the table.  
The load factor is a measure of how full the hash table is allowed to get before its capacity is automatically increased.   
Generally, the default load factor (.75) offers a good tradeoff between time and space costs. Higher values decrease the space overhead but increase the time cost to look up an entry (which is reflected in most Hashtable operations, including get and put).  

**Good and detailed explanation**  
[How does a HashMap work in JAVA](http://coding-geek.com/how-does-a-hashmap-work-in-java/)  
Each time you add a new key/value in your Map with put(…), the function checks if it needs to increase the capacity of the inner array. In order to do that, the map stores 2 data:

The size of the map: it represents the number of entries in the HashMap. This value is updated each time an Entry is added or removed.
A threshold: it’s equal to (capacity of the inner array) * loadFactor and it is refreshed after each resize of the inner array  
[hashtable source code](http://grepcode.com/file/repository.grepcode.com/java/root/jdk/openjdk/6-b14/java/util/Hashtable.java) . 
