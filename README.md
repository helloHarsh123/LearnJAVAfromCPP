# LearnJAVAfromCPP

- **Architecture**: cpp (g++)compiles to machine code, java (javac) converts to .class, and it gets converted to machine code on run time in JVM. (Java is a cross-platform, and Java is slower).
- **JVM** – make java class runs, JDK - tools for java programming
- **Inputs**: Scanner scn = new Scanner(System.in);
    1. int n = scn.nextInt();
    2. String s = scn.next(); // first string
    3. s = scn.next(); // next string
- **Output**:
    1. System.out.println(“Your Input” + n);
    2. System.out.print(); // no next line
- **Loops**: for, while, do-while, break, continue, if, else, if-else, switch
- **DataTypes**(8 inbuilt or primitive):
    1. byte 1, short 2, int 4, long 8 (1byte has 8 bits)
    2. char 2 bytes
    3. float 4, double 8(pref)
    4. boolean
- **Wrapper Classes(Primitive to objects) - Used for conversions:**
    1. All Java collections allow only objects(Made using Wrapper Classes). Also helpful in synchronization
    2. char->Char, int->Int, double->Double etc.
    3. Autoboxing and unboxing: implicit conversion between primitive and wrapper
    4. **Wrapper.valueOf(String)**; converts string to Wrapper
    5. Wrapper.valueOf(String s,int radix); s is to be read using base as radix. 11,2 will give 3 // only for integral classes
    6. **Wrapper.valueOf(primitive)** // return wrapper object
    7. **xxxValue()**: byteValue(), longValue(), floatValue() //Integral+Float Wrappers have it;
    8. **primitive parseXxx(String s)**; // gives out primitive

parseInt, parseDouble, parseBoolean

- 1. primitive parseXxx(String s, int radix); 1000,2 → 8
  2. o.**toString**(): – gives string version of o
  3. **Wrapper.toString(primitive)** – converts prim to string
  4. Wrapper.toString(primitive, radix) - 5,2 gives 101
- There is no pointer. (no addressing, pass-by reference or pointers)
- **Arrays**:
    1. int\[\] arr = new int\[5\]; only one way,
    2. Memory allocated in the heap, we have arr.length data member
    3. for(int i = 0; i < arr.length; i++) arr\[i\]
    4. for(int val : arr)
    5. Here (arr is pointing to the same memory if passing to a function)
- **2-D arrays**
    1. int\[\]\[\] arr = new int\[2\]\[3\]; // all memory in heap
    2. int\[\]\[\] arr = new int\[2\]\[\];
        1. arr\[0\] = new int\[3\]; //each row can have different num of els
    3. int\[\]\[\] arr= { {1, 2, 3, 4}, {5, 6, 7} };
- **Classes and Other Objects**
```
    1. Class Point{

int x,

int y

};

- 1. Point p = new Point();, p.x, p.y
  2. Class Rectangle{

Point tl;

Point br;

}
```
- 1. Rectangle r = new Rectangle; r.tl = new Point; r.br = new Point;
  2. All class object names are references(equivalent to pointers)
- **ArrayList(equivalent to vectors)**
    1. ArrayList&lt;Integer&gt; list = new ArrayList<>();
    2. list.add(10); list.add(20);// 10 20
    3. list.add(1, 1000);// 10 1000 20
    4. list.get(1); // 1000
    5. list.set(1, 2000); // 2000 list\[i\] = 2000 wont work
    6. list.remove(1); 10 20
    7. ArrayList&lt;String&gt; l2 = new ArrayList<>();
    8. looping: a way is using .size()
    9. other way for(int val1 : list)
    10. Print all: System.out.println(list);// \[10, 20\]
    11. ArrayList, like all objects – passes reference to functions.
    12. Arrays to ArrayList:

String\[\] strArr = { "A", "B", "C", "D", "E" };

List&lt;String&gt; al = new ArrayList&lt;String&gt;(Arrays.asList(strArr));

- **Stack and Queue:**
    1. Stack&lt;Integer&gt; st = new Stack<>();
    2. st.push(), st.peek(), st.pop()
    3. ArrayDeque&lt;Integer&gt; que = new ArrayDeque<>();
    4. que.addLast(el); que.getFirst(); que.removeFirst();
- **Strings and StringBuilders:**
    1. String s1 = scn.next();
    2. String s2 = scn.nextLine();
    3. s1.charAt(i) // s\[i\]
    4. s1.length() // diff from array length is a function
    5. s.substring(startindex, endindex+1); // diff from c++
    6. s.substring(startindex); // till end
    7. s1+=’a’; // (helloa)allowed, s1+=10 // (hello10)also allowed, s1+=”world”// not allowed
    8. “hello” + 10 + 20 // process from left to right hello1020
    9. 10 + 20 + “hello” // 30hello
    10. String s1 = “hello world harsh”;

String\[\] parts = s1.split(“ “); \[“hello”,”world”,”harsh”\] // use any delimeter

- 1. String Interning:

String s1 = “hello”;

String s2 = “hello”; // since hello is already in intern pool, s2 starts pointing to it, instead of creating a new one

String s3 = new String(“hello”); // Creates a new String object and its not in intern pool. However it can point to the same character array

- 1. Check if 2 Strings are equal:
        1. Dont use == (only compares addresses)
        2. s1.equals(s2); // first checks address then checks character by character
  2. Immutability:
        1. s1 = “hello” then s1 = “bye” is also possible(reference is mutable and instance is immutable)
        2. but s1\[i\] or s.set(i) not possible
        3. Interning induces immutability
        4. Impact: String performance slows
        5. eg: for(int i = 0; i < 100; i++){

s+=i;

} // Looks O(n) is O(n^2)

- 1. StringBuilder(Mutable String):
        1. StringBuilder sb = new StringBuilder(“hello”);
        2. sb.charAt(0)//h, sb.setCharAt(0,’d’)// dello
        3. sb.insert(2,’y’); // deyllo
        4. sb.deletecharAt(2); // dello
        5. sb.append(‘g’)// dellog, sb.length();//6
        6. eg: for(int i = 0; i < 100; i++){

sb.append(i + ‘0’);

} Here it costs O(n)

- **HashMaps: Similar to unordered_map**
    1. HashMap&lt;String, Integer&gt; hm = new HashMap<>();
    2. System.out.println(hm); // works shocking
    3. hm.put(“India”, 130); // if already present update else create it
    4. hm.get(“Namibia”)// returns vals if present else returns NULL
    5. hm.getOrDefault(“Uganda”, “Default”); // returns default value if not found
    6. hm.containsKey(“India”); // returns true or false
    7. hm.remove(key);
    8. Set&lt;String&gt; keys = hm.keyset(); // we get all the keys// set is an interface here // keyset gives a HashSet
    9. Java's HashMap and HashSet are not thread-safe by default (use ConcurrentHashMap and ConcurrentSkipListSet for concurrency).
    10. Looping through:

for(String key: hm.keyset()){

Integer val = hm.get(key); // put logic here

}

- 1. HashSet, hs.add, hs.contains, isEmpty, size, remove
- **PriorityQueue**
    1. PriorityQueue&lt;Integer&gt; pq = new PriorityQueue<>(); // Min Heap Default
    2. pq.add(val); // logn complexity
    3. pq.remove(); // removes top // logn
    4. pq.peek(); // shows top // logn
    5. PriorityQueue&lt;Integer&gt; pq = new PriorityQueue<>(Collections.reverseOrder()); // Max Heap
- **Comparable in Java:** Java automatically use Comparable for comparison in data structures
    1. Comparison is not bool but **integer**.
    2. static class **Student** implements **Comparable**&lt;Student&gt; {

int rno;

int name;

//write constructor

public int **compareTo**(Student o){ // override compareTo

return this.rno - o.rno;

}

}

- 1. <0 means it should be considered smaller.
  2. **PriorityQueue**< **Student** \> = new **PriorityQueue**<>();
  3. to reverse do: o.rno - this.rno
- **Custom Compare in Java (Override Comparable)**
    1. Comparison is not bool but **integer**.
    2. **PriorityQueue**&lt; Pair<Integer, Integer&gt; > = new PriorityQueue<>(new CustomCompare()); // Pair is a Comparable but we are overriding the default comparison

    ```
    public class **CustomCompare** implements **Comparator&lt; Pair<Integer,Integer&gt; >** {
    
        @Override
        
        public int **compare**( Pair&lt;Integer, Integer&gt; p1, Pair&lt;Integer, Integer&gt; p2) {
        
        return (p1.getKey() + p1.getValue()) - (p2.getKey() + p2.getValue());
        
        }
    
    }
    ```
- 1. Arrays.sort(arr, new **CustomCompare**);
- LinkedLists: Singly, Doubly, Circular
    1. While doing all the operations: addNode, deleteNode, showAll

keep in mind that as soon as an object is out of reference in Java we can consider it as good as deleted.

```
public class Node { // Singly node

    int value;
    
    Node next;
    
    public Node(int value) {
    
    this.value = value;
    
    next = null;
    
    }

}
```
```
public class Node { // doubly or circular

    int value;
    
    Node next;
    
    Node previous;
    
    public Node(int value) {
    
        this.value = value;
        
        next = null;
        
        previous = null;
    
    }

}
```
- 1. Using Collections LinkedList // By default singly //time complexities match normal LinkedList which maintains head and tail
        1. LinkedList&lt;String&gt; ll = new LinkedList<>();
        2. ll.add(“Hello”); ll.add(“World”); ll.add(“Harsh”); // add at end
        3. ll.add(1,”one”); // add at an index
        4. ll.set(1,”other”); // change a certain index
        5. ll.remove(Object) //”other”, ll.remove(index) //1
        6. for(String str: ll)
        7. Object\[\] arr = ll.toArray(), size(), addFirst(), removeFirst(), removelast();
        8. Collections.addAll(ll, arr);
- **Formatter in Java:**
    1. String greetings = String.format("Welcome %s!","Harsh"); // Welcome Harsh!
    2. String greetings = String.format("Welcome %2 %1!","Harsh",”Gupta”); // Welcome Gupta Harsh!
    3. Calendar c = new GregorianCalendar(2017, 11, 10);

String s = String.format("The date is: %tm %1$te,%1$tY", c);//month year day(te)

- 1. String s = String.format("John scored 90%% in Fall semester"); // Allow percentage sign
- **Generics in Java**:

1. public &lt;T&gt; List&lt;T&gt; fromArrayToList(T\[\] a) {

return Arrays.stream(a).collect(Collectors.toList());

}

&lt;T&gt; in the method signature implies that the method will be dealing with generic type T.

List&lt;T&gt; is return type

1. **Multiple Generics:**

public static &lt;T, G&gt; List&lt;G&gt; fromArrayToList(T\[\] a, Function&lt;T, G&gt; mapperFunction) {

return Arrays.stream(a).map(mapperFunction)

.collect(Collectors.toList());

}

1. Generics.fromArrayToList(intArray, Object::toString); // Using It
2. **Bounded Generics:**
    1. public &lt;T extends Number&gt; List&lt;T&gt; fromArrayToList(T\[\] a) // Number and all its child classes // upper bound
    2. public &lt;T super Number&gt; List&lt;T&gt; fromArrayToList(T\[\] a) // Number and all its parent classes // lower bound
    3. &lt;T extends Number & Comparable&gt; // Multiple Bounds
3. **Wildcards With Generics:**

public static void paintAllBuildings(List&lt;? extends Building&gt; buildings) {

...

} // Anything that extends Buildings

1. **Type Erasure:** At compile time all generics are removed and their Bounds are used instead. If no bound, then nothing
2. A Generic Type can never be primitive.
