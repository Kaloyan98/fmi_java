Generics and Clean Code
Generic In-Memory Cache 📦
Caching in memory is a commonly used approach to improve the performance of algorithms that intensively use data stored on slower devices. We will create our own implementation of a generic cache.

Accessing cached data is much faster, but unfortunately, the cache has a fixed capacity that cannot be exceeded. For this reason, each cache has a so-called eviction policy, i.e., a rule that determines which elements are removed from the cache when attempting to add a new element to a full cache.

Interface
The Cache<K, V> interface is given, which can operate with objects of arbitrary types.

package bg.sofia.uni.fmi.mjt.cache;

public interface Cache<K, V> {

    V get(K key);

    void set(K key, V value);

    boolean remove(K key);

    long size();

    void clear();

    double getHitRate();
    
    int getUsesCount(K key);
    
}

Implementation
We will create two implementations of this interface, differing in the eviction policy they use:

Random Replacement (RR)
Least-Frequently Used (LFU)
A specific implementation of the Cache interface using the eviction policy chosen by us is created through the following static methods of the CacheFactory interface:

/**
 * Constructs a new Cache<K, V> with the specified maximum capacity and eviction policy
 * @throws IllegalArgumentException if the given capacity is less than or equal to zero.
 * Note that IllegalArgumentException is a `RuntimeException` from the JDK
 */
static <K, V> Cache<K, V> getInstance(long capacity, EvictionPolicy policy);

/**
 * Constructs a new Cache<K, V> with a maximum capacity of 10,000 items and the specified eviction policy 
 */
static <K, V> Cache<K, V> getInstance(EvictionPolicy policy); 
where EvictionPolicy, as you might have guessed, is an enumerated type:

public enum EvictionPolicy {
    RANDOM_REPLACEMENT,
    LEAST_FREQUENTLY_USED
}
Clarifications
👉 For the Least Frequently Used implementation:

We consider "usage" for each invocation of get or set for a given element.
When set is called for an already existing key with a new or the same value, the count of times we have used this element is increased by 1, rather than being reset to zero.
If there are two or more elements with equal (minimal) usage frequency, when adding a new element to a full cache, we remove any one of them arbitrarily.
👉 For the Random Replacement implementation, the getUsesCount method throws UnsupportedOperationException (an existing RuntimeException from the JDK).

Notes
❗ Carefully consider which data structures you will choose for your implementation. Which methods of the cache are likely to be used most frequently?

❗ Write clean code! Consider the remarks of the automatic tools regarding the rules for clean code in the grader: strive for your code to remain with 0 remarks.
