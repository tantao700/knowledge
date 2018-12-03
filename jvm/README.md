# jvisualvm

- histogram(直方图)
    Shallow Heap(自身并不包含引用的大小)
    Retained Heap(自身并包含引用的大小)

- Dominator Tree(支配树)
    显示对象及其包含对象的引用关系

# (Reference)对象引用    
对象引用按从最强到最弱有如下级别，不同的引用（可到达性）级别反映了对象的生命周期：

- 强引用（Strong Ref）：通常我们编写的代码都是强引用，于此相对应的是强可达性，只有去掉强可达性，对象才能被回收。
- 软引用（Soft Ref）：对应软可达性，只要有足够的内存就一直保持对象，直到发现内存不足且没有强引用的时候才回收对象。
- 弱引用（Weak Ref）：比软引用更弱，当发现不存在强引用的时候会立即回收此类型的对象，而不需要等到内存不足。通过java.lang.ref.WeakReference和java.util.WeakHashMap类实现。
- 虚引用（Phantom Ref）：根本不会在内存中保持该类型的对象，只能使用虚引用本身，一般用于在进入finalize()方法后进行特殊的清理过程，通过java.lang.ref.PhantomReference实现。

# GC Roots和Reference Chain
JVM在进行GC的时候是通过使用可达性来判断对象是否存活，通过GC Roots（GC根节点）的对象作为起始点，从这些节点开始进行向下搜索，搜索所走过的路径成为Reference Chain（引用链），当一个对象到GC Roots没有任何引用链相连（用图论的话来说就是从GC Roots到这个对象不可达）时，则证明此对象是不可用的。

Reference:https://www.javatang.com/archives/2017/11/08/11582145.html