##Redisson - distributed and scalable Java data structures on top of Redis server. Advanced Redis client

Use familiar Java data structures with power of [Redis](http://redis.io).

Based on patched version of [lettuce](https://github.com/wg/lettuce) [Redis](http://redis.io) client and [Netty 4](http://netty.io) framework.  
Redis 2.8+ and JDK 1.6+ compatible  


Read [wiki](https://github.com/mrniko/redisson/wiki) for more Redisson usage details


Licensed under the Apache License 2.0.


Features
================================
* Cluster servers mode:
    1. automatic master discovery
    2. automatic new master server discovery
    3. automatic slots change discovery
* Sentinel servers mode: 
    1. automatic master and slave servers discovery
    2. automatic new master server discovery
    3. automatic new slave servers discovery
    4. automatic slave servers offline/online discovery
    5. read data using slave servers, write data using master server
* Master with Slave servers mode: read data using slave servers, write data using master server
* Single server mode: read and write data using single server
* Distributed implementation of `java.util.List`  
* Distributed implementation of `java.util.Set`  
* Distributed implementation of `java.util.SortedSet`  
* Distributed implementation of `java.util.Queue`  
* Distributed implementation of `java.util.concurrent.BlockingQueue`  
* Distributed implementation of `java.util.Deque`  
* Distributed implementation of `java.util.Map`  
* Distributed implementation of `java.util.concurrent.ConcurrentMap`  
* Distributed implementation of reentrant `java.util.concurrent.locks.Lock` with TTL support  
* Distributed alternative to the `java.util.concurrent.atomic.AtomicLong`  
* Distributed alternative to the `java.util.concurrent.CountDownLatch`  
* Distributed publish/subscribe messaging via `org.redisson.core.RTopic`  
* Distributed HyperLogLog via `org.redisson.core.RHyperLogLog`  
* Thread-safe implementation
* Supports OSGi  
* With over 110 unit tests  

Projects using Redisson
================================
Setronica: [setronica.com](http://setronica.com/)  
Monits: [monits.com](http://monits.com/)  
Brookhaven National Laboratory: [bnl.gov](http://bnl.gov/)  
Netflix Dyno client: [dyno] (https://github.com/Netflix/dyno)

Recent Releases
================================
####Please Note: trunk is current development branch.

####04-Jul-2015 - version 1.3.0 released
Feature - `RQueue.pollLastAndOfferFirstTo` method added  
Feature - `RObject.rename`, `RObject.renameAsync`, `RObject.renamenx`, `RObject.renamenxAsync` methods added  
Feature - `RList.getAsync`, `RList.addAsync`, `RList.addAllAsync` methods added  
Feature - `RObject.deleteAsync` method added  
Feature - unix sockets support via `Configuration.useLinuxNativeEpoll` setting  
Feature - Redisson.getTopicPattern method added (thanks to alex-sherwin)  
Improvement - `RLock` auto-unlock then client lock-owner is gone (thanks to AndrewKolpakov)  
Improvement - lua scripts used instead of multi/exec commands to avoid connection errors during execution (thanks to AndrewKolpakov)  
Improvement - `RObject.delete` method now returns `boolean` status  
Improvement - propagate Command processing exceptions to ConnectionManager (thanks to marko-stankovic)  
Improvement - KryoCodec classes registration ability added  
Fixed - slave status handling in Sentinel mode  
Fixed - String codec  
Fixed - Cluster ASKING command support  
Fixed - `RedissonBlockingQueue#drainTo` method (thanks to Sergey Poletaev)  
Fixed - Cluster.STATE.HANDSHAKE enum added  
Fixed - `RedissonClient.getScript` method added  
Fixed - `BlockingQueue.poll` method  
Fixed - Incorrect map key encoding makes hmget return no fields when string keys are used (thanks to sammiq)  

####02-Apr-2015 - version 1.2.1 released
Feature - all redis-script commands via 'RScript' object  
Feature - implementation of `java.util.concurrent.BlockingQueue` (thanks to pdeschen)  
Feature - buckets load by pattern (thanks to mathieucarbou)  
Improvement - IPv6 support  
Improvement - `isEmpty` checks for added collections  
Fixed - KryoCodec keys decoding (thanks to mathieucarbou)  
Fixed - `RMap.addAndGet()` data format  
Fixed - timeout support in cluster, sentinel and single connections configurations  
Fixed - ClassCastException in `RedissonCountDownLatch.trySetCount`  
Fixed - `RMap.replace` concurrency issue (thanks to AndrewKolpakov)  
Fixed - `RLock` subscription timeout units fixed (thanks to AndrewKolpakov)  
Fixed - Re-throw async exceptions (thanks to AndrewKolpakov)  

####09-Jan-2015 - version 1.2.0 released
Feature - cluster mode support  
Fixed - `RList` iterator race conditions  
Fixed - `RDeque.addFirst` `RDeque.addLast` methods  
Fixed - OSGi support

####16-Dec-2014 - version 1.1.7 released
Improvement - `RAtomicLong` optimization  
Fixed - `RMap.fastRemove` and `RMap.getAll` methods  
Fixed - `RTopic` listeners re-subscribing in sentinel mode  
Fixed - `RSet.toArray` and `RSet.iterator` values order  
Fixed - keys iteration in `RMap.getAll`  
Fixed - `RSet` iteration  
Fixed - `RAtomicLong` NPE  
Fixed - infinity loop during master/slave connection acquiring  
Fixed - `RedissonList.addAll` result  

####18-Nov-2014 - version 1.1.6 released
Feature - `RBucket.exists` and `RBucket.existsAsync` methods added  
Feature - `RMap.addAndGet` method added  
Feature -  database index via `database` and operation timeout via `timeout` config params added  
Improvement - `RLock` optimization  
__Breaking api change__ - Redisson now uses `RedissonClient` interface  
Fixed - NPE in `CommandOutput`  
Fixed - unsubscribing during `RTopic.removeListener`  
Fixed - all object names encoding, no more quotes  
Fixed - HashedWheelTimer shutdown  
Fixed - `RLock` race conditions (thanks to jsotuyod and AndrewKolpakov)  
Fixed - `RCountDownLatch` race conditions  

####23-Jul-2014 - version 1.1.5 released
Feature - operations auto-retry. `retryAttempts` and `retryInterval` params added for each connection type  
Feature - `RMap.filterEntries`, `RMap.getAll`, `RMap.filterKeys`, `RMap.filterValues` methods added  
Feature - `RMap.fastRemove`, `RMap.fastRemoveAsync`, `RMap.fastPut` & `RMap.fastPutAsync` methods added  
Fixed - async operations timeout handling  
Fixed - sorting algorithm used in `RSortedSet`.  

####15-Jul-2014 - version 1.1.4 released
Feature - new `RLock.lockInterruptibly`, `RLock.tryLock`, `RLock.lock` methods with TTL support  
Fixed - pub/sub connections reattach then slave/master down  
Fixed - turn off connection watchdog then slave/master down  
Fixed - sentinel master switch  
Fixed - slave down connection closing  

####13-Jul-2014 - version 1.1.3 released
Improvement - RedissonCountDownLatch optimization  
Improvement - RedissonLock optimization  
Fixed - RedissonLock thread-safety  
Fixed - master/slave auth using Sentinel servers  
Fixed - slave down handling using Sentinel servers  

####03-Jul-2014 - version 1.1.2 released
Improvement - RedissonSet.iterator implemented with sscan  
Improvement - RedissonSortedSet.iterator optimization  
Feature - `RSortedSet.removeAsync`, `RSortedSet.addAsync`, `RSet.removeAsync`, RSet.addAsync methods added  
Feature - slave up/down detection in Sentinel servers connection mode  
Feature - new-slave automatic discovery in Sentinel servers connection mode  

####17-June-2014 - version 1.1.1 released
Feature - sentinel servers support  
Fixed - connection leak in `RTopic`  
Fixed - setted password not used in single server connection  

####07-June-2014 - version 1.1.0 released
Feature - master/slave connection management  
Feature - simple set/get object support via `org.redisson.core.RBucket`  
Feature - hyperloglog support via `org.redisson.core.RHyperLogLog`  
Feature - new methods `getAsync`, `putAsync` and `removeAsync` added to `org.redisson.core.RMap`  
Feature - new method `publishAsync` added to `org.redisson.core.RTopic`  
Feature - [Kryo](https://github.com/EsotericSoftware/kryo) codec added (thanks to mathieucarbou)  
__Breaking api change__ - `org.redisson.Config` model changed  
Fixed - score calucaltion algorithm used in `RSortedSet`.  
Fixed - `RMap.put` & `RMap.remove` result consistency fixed.  
Fixed - `RTopic.publish` now returns the number of clients that received the message  
Fixed - reconnection handling (thanks to renzihui)  
Improvement - `org.redisson.core.RTopic` now use lazy apporach for subscribe/unsubscribe  

####04-May-2014 - version 1.0.4 released
Feature - distributed implementation of `java.util.Deque`  
Feature - some objects implements `org.redisson.core.RExpirable`  
Fixed - JsonJacksonCodec lazy init  

####26-Mar-2014 - version 1.0.3 released
Fixed - RedissonAtomicLong state format  
Fixed - Long serialization in JsonJacksonCodec  

####05-Feb-2014 - version 1.0.2 released
Feature - distributed implementation of `java.util.SortedSet`  
Fixed - OSGi compability  

####17-Jan-2014 - version 1.0.1 released
Improvement - forceUnlock, isLocked, isHeldByCurrentThread and getHoldCount methods added to RLock  
Feature - connection load balancer to use multiple Redis servers  
Feature - published in maven central repo  

####11-Jan-2014 - version 1.0.0 released
First stable release.

### Maven 

Include the following to your dependency list:

    <dependency>
       <groupId>org.redisson</groupId>
       <artifactId>redisson</artifactId>
       <version>1.2.1</version>
    </dependency>

### Supported by

YourKit is kindly supporting this open source project with its full-featured Java Profiler.
YourKit, LLC is the creator of innovative and intelligent tools for profiling
Java and .NET applications. Take a look at YourKit's leading software products:
<a href="http://www.yourkit.com/java/profiler/index.jsp">YourKit Java Profiler</a> and
<a href="http://www.yourkit.com/.net/profiler/index.jsp">YourKit .NET Profiler</a>.
