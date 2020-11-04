# Software Development Concepts
## Interview questions

### Please write PSEUDO code or write code in your STRONGEST language.

1. Please write simple implementation for LinkedList data structure.
    <details>
    <summary>Click to see the answer</summary>
    <br>

    ```py
    class Node(object):
        def __init__(self):
            self.data = None # contains the data
            self.next = None # contains the reference to the next node


    class LinkedList:
        def __init__(self):
            self.cur_node = None

        def add_node(self, data):
            new_node = Node() # create a new node
            new_node.data = data
            new_node.next = self.cur_node # link the new node to the 'previous' node.
            self.cur_node = new_node #  set the current node to the new one.

        def list_print(self):
            node = self.cur_node # cant point to ll!
            while node:
                print(node.data)
                node = node.next

    ll = LinkedList()
    ll.add_node(1)
    ll.add_node(2)
    ll.add_node(3)

    ll.list_print()
    ```

    output:
    ```sh
    3
    2
    1
    ```
    </details><br>

1. What is time complexity for Search (Lookup) in HashTable? Please explain.
    <details>
    <summary>Click to see the answer</summary>
    <br>
    In hash tables search is performed in O(1) time complexity on average but in worst case scenario, time complexity is O(n) where n is table size.<br>
    Hash tables suffer from O(n) worst time complexity due to two reasons:
    <ul>
    <li>If too many elements were hashed into the same key: looking inside this key may take O(n) time.</li>
    <li>Once a hash table has passed its load balance - it has to rehash [create a new bigger table, and re-insert each element to the table].</li>
    </ul>
    However, it is said to be O(1) average and amortized case because:
    <ul>
    <li>It is very rare that many items will be hashed to the same key [if you chose a good hash function and you don't have too big load balance.</li>
    <li>The rehash operation, which is O(n), can at most happen after n/2 ops, which are all assumed O(1): Thus when you sum the average time per op, you get : (n*O(1) + O(n)) / n) = O(1)</li>
    </ul>
    <br>
    <br>
    <table><thead><tr><th>Hash table example:</th><th></th><th></th><th></th><th>first letter of value</th><th></th><th></th><th></th><th></th><th></th><th></th></tr></thead><tbody><tr><td>index</td><td>vaule</td><td></td><td></td><td>key=value[0]</td><td>index</td><td></td><td>value</td><td>Insert complexity</td><td>Search complexity</td><td>Delete complexity</td></tr><tr><td>1</td><td>Amsterdam</td><td></td><td>hash function:</td><td>a</td><td>1</td><td></td><td>Amsterdam</td><td>1</td><td>1</td><td>1</td></tr><tr><td>2</td><td>Ankara</td><td></td><td></td><td>b</td><td>10</td><td></td><td>Belgrade</td><td>1</td><td>1</td><td>1</td></tr><tr><td>3</td><td>Athens</td><td></td><td></td><td>c</td><td>20</td><td></td><td>Ankara</td><td>2</td><td>2</td><td>2</td></tr><tr><td>4</td><td>Athens1</td><td></td><td></td><td>d</td><td>30</td><td></td><td>Athens</td><td>3</td><td>3</td><td>3</td></tr><tr><td>5</td><td>Athens2</td><td></td><td></td><td></td><td></td><td></td><td>Athens1</td><td>4</td><td>4</td><td>4</td></tr><tr><td>6</td><td>Athens3</td><td></td><td></td><td></td><td></td><td></td><td>Athens2</td><td>5</td><td>5</td><td>5</td></tr><tr><td>7</td><td>Athens4</td><td></td><td></td><td></td><td></td><td></td><td>Athens3</td><td>6</td><td>6</td><td>6</td></tr><tr><td>8</td><td>Athens5</td><td></td><td></td><td></td><td></td><td></td><td>Athens4</td><td>7</td><td>7</td><td>7</td></tr><tr><td>9</td><td>Athens6</td><td></td><td></td><td></td><td></td><td></td><td>Athens5</td><td>8</td><td>8</td><td>8</td></tr><tr><td>10</td><td>Belgrade</td><td></td><td></td><td></td><td></td><td></td><td>Athens6</td><td>9</td><td>9</td><td>9</td></tr><tr><td>11</td><td>Athens7</td><td></td><td></td><td></td><td></td><td></td><td>Athens7</td><td>11</td><td>11</td><td>11</td></tr><tr><td>12</td><td>Bled</td><td></td><td></td><td></td><td></td><td></td><td>Bled</td><td>3</td><td>3</td><td>3</td></tr><tr><td>13</td><td>Athens8</td><td></td><td></td><td></td><td></td><td></td><td>Celje</td><td>1</td><td>1</td><td>1</td></tr><tr><td>14</td><td>Athens9</td><td></td><td></td><td></td><td></td><td></td><td>Bled1</td><td>12</td><td>12</td><td>12</td></tr><tr><td>15</td><td>Athens10</td><td></td><td></td><td></td><td></td><td></td><td>Bled2</td><td>13</td><td>13</td><td>13</td></tr><tr><td>16</td><td>Athens11</td><td></td><td></td><td></td><td></td><td></td><td>Dubrovnik</td><td>1</td><td>1</td><td>1</td></tr><tr><td>17</td><td>Athens12</td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>18</td><td>Athens13</td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>19</td><td>Athens14</td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>20</td><td>Celje</td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>21</td><td>Bled1</td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>22</td><td>Bled2</td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>23</td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>24</td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>25</td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>26</td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>27</td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>28</td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>29</td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>30</td><td>Dubrovnik</td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>31</td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>32</td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr></tbody></table>
    </details><br>
1. Please explain what SOLID principles are. Example for each principle is much
appreciated.
    <details>
    <summary>Click to see the answer</summary>
    <br>
    <u>Single Responsibility Principle:</u><br>
    A class should have only one job.  If a class has more than one responsibility, it becomes coupled.
    A change to one responsibility results to modification of the other responsibility.<br>
    <a href="https://github.com/MilovanTomasevic/Python-Design-Patterns/blob/master/src/1_patterns/1_SOLIDDesignPrinciples/1_SingleResponsibility/srp.py"  target="_blank">Source Code</a><br><br>
    <u>Open-Closed Principle:</u><br>
    Software entities(Classes, modules, functions) should be open for extension, not modification.<br>
    <a href="https://github.com/MilovanTomasevic/Python-Design-Patterns/blob/master/src/1_patterns/1_SOLIDDesignPrinciples/2_Open-Closed/ocp.py" target="_blank">Source Code</a><br><br>
    <u>Liskov Substitution Principle:</u><br>
    A sub-class must be substitutable for its super-class.  The aim of this principle is to ascertain that a sub-class can assume the place of its super-class without errors.  If the code finds itself checking the type of class then, it must have violated this principle.<br>
    <a href="https://github.com/MilovanTomasevic/Python-Design-Patterns/blob/master/src/1_patterns/1_SOLIDDesignPrinciples/3_LiskovSubstitution/lsp.py" target="_blank">Source Code</a><br><br>
    <u>Interface Segregation Principle:</u><br>
    A client should not be forced to implement an interface that it does not use.<br>
    <a href="https://github.com/MilovanTomasevic/Python-Design-Patterns/blob/master/src/1_patterns/1_SOLIDDesignPrinciples/4_InterfaceSegregation/isp.py" target="_blank">Source Code</a><br><br>
    <u>Dependency Inversion Principle:</u><br>
    This principle suggests that below two points:
    <ul><li>High-level modules should not depend on low-level modules. Both should depend on abstractions.</li>
    <li>Abstractions should not depend on details. Details should depend on abstractions.</li></ul>
    <a href="https://github.com/MilovanTomasevic/Python-Design-Patterns/blob/master/src/1_patterns/1_SOLIDDesignPrinciples/5_DependencyInversion/dip.py" target="_blank">Source Code</a><br><br>
    </details><br>



### PYTHON

1. Please provide simplest example for single inheritance with overriden method.
    <details>
    <summary>Click to see the answer</summary>
    <br>
    Method overriding is an ability of any object-oriented programming language that allows a subclass or child class to provide a specific implementation of a method that is already provided by one of its super-classes or parent classes. When a method in a subclass has the same name, same parameters or signature and same return type(or sub-type) as a method in its super-class, then the method in the subclass is said to override the method in the super-class.<br>
    
    ```py
    class Parent:
        def hello(self):
            print("I'm Parent")                          

    class Child(Parent):
        def hello(self):
            print("I'm Child")                             

    obj=Child()
    obj.hello()
    ```

    output:
    ```sh
    I'm Child
    ```

    </details><br>
1. Could you explain what is the difference between <code>*args</code> and <code>**kwargs</code>? Additionally, is
this valid function definition <code>def func(*args123, **kwargs456)</code>?
    <details>
    <summary>Click to see the answer</summary>
    <br>
    I use <code>*args</code> and <code>**kwargs</code> as an argument when I have no doubt about the number of arguments I should pass in a function.<br>
    <br>
    <table><thead><tr><th></th><th>In function construction</th><th>In function call</th></tr></thead><tbody><tr><td>*args</td><td>def f (*args):<br>&nbsp;&nbsp;&nbsp;&nbsp;for arg in args:<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;print(arg)<br>f(1, 2)</td><td>def f(a, b):<br>&nbsp;&nbsp;&nbsp;&nbsp;return a + b<br>args = (1, 2)<br>f(*args)</td></tr><tr><td>**kwargs</td><td>def f(a, b):<br>&nbsp;&nbsp;&nbsp;&nbsp;return a + b<br>def g(**kwargs):<br>&nbsp;&nbsp;&nbsp;&nbsp;return f(**kwargs)<br>g(a=1, b=2)</td><td>def f(a, b):<br>&nbsp;&nbsp;&nbsp;&nbsp;return a + b<br>kwargs = dict(a=1, b=2)<br>f(**kwargs)</td></tr></tbody></table>

    <br><u>Args:</u><br>

    ```py
    def print_everything(*args):
        for count, thing in enumerate(args, start=1):
            print('{0}. {1}'.format(count, thing))

    print_everything('apple', 'banana', 'cabbage')
    ```
    output:
    ```sh
    1. apple
    2. banana
    3. cabbage
    ```
    <br><u>Kwargs:</u><br>
    
    ```py
    def table_things(**kwargs):
        for name, value in kwargs.items():
            print( '{0} = {1}'.format(name, value))

    table_things(apple = 'fruit', cabbage = 'vegetable')
    ```
    output:
    ```sh
    apple = fruit
    cabbage = vegetable
    ```

    <br><u>Args & Kwargs:</u><br>

    ```py
    def hello(*args,**kwargs):
        print(f"args: {args}")
        print(f"kwargs: {kwargs}")
    
    hello('I', 'am', 'Milovan', first="I", second="am", third="Milovan")
    ```

    output:
    ```sh
    args: ('I', 'am', 'Milovan')
    kwargs: {'first': 'I', 'second': 'am', 'third': 'Milovan'}
    ```
    </details><br>
1. Please explain what is the difference between tuple and list.
    <details>
    <summary>Click to see the answer</summary>
    <br>
    List and Tuple in Python are the class of data structure. The list is dynamic, whereas tuple has static characteristics.
    <br><br>

    <table><thead><tr><th>R.NO.</th><th>LIST</th><th>TUPLE</th></tr></thead><tbody><tr><td>1</td><td>Lists are mutable </td><td>Tuple are immutable </td></tr><tr><td>2</td><td>Implication of iterations is Time-consuming</td><td>Implication of iterations is comparatively Faster</td></tr><tr><td>3</td><td>The list is better for performing operations, such as insertion and deletion.</td><td>Tuple data type is appropriate for accessing the elements</td></tr><tr><td>4</td><td>Lists consume more memory</td><td>Tuple consume less memory as compared to the list</td></tr><tr><td>5</td><td>Lists have several built-in methods </td><td>Tuple does no have must built-in methods.</td></tr><tr><td>6</td><td>In tuple, it is hard to take place.</td><td>The unexpected changes and errors are more likely to occur</td></tr></tbody></table>
    </details><br>