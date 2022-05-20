# Software Design

```python
If you reuse code, you'll save a load,
but if you reuse design, your future will shine.
```

- Immutable Objects in Java
    
    An object is considered *immutable* if its state cannot change 
    after it is constructed. Maximum reliance on immutable objects is widely
     accepted as a sound strategy for creating simple, reliable code.
    
    Immutable objects are particularly useful in concurrent applications.
     Since they cannot change state, they cannot be corrupted by thread 
    interference or observed in an inconsistent state.
    
    Programmers are often reluctant to employ immutable objects, because 
    they worry about the cost of creating a new object as opposed to 
    updating an object in place. The impact of object creation is often 
    overestimated, and can be offset by some of the efficiencies associated 
    with immutable objects. These include decreased overhead due to garbage 
    collection, and the elimination of code needed to protect mutable 
    objects from corruption.
    
- Wrapper Classes
    
    In general, a wrapper class is any class which "wraps" or "encapsulates" the functionality of another class or component. These are useful by providing a level of abstraction from the implementation of the underlying class or component; for example, wrapper classes that wrap COM components can manage the process of invoking the COM component without bothering the calling code with it. They can also simplify the use of the underlying object by reducing the number interface points involved; frequently, this makes for more secure use of underlying components.
    
- explain double dispatch
    
    "Double-dispatch" simply means the operation that gets executed depends
    on the kind of request and the types of *two* receivers. Accept is a double-
    dispatch operation.    Its meaning depends on two types: the Visitor's and the Element's. Double-dispatching lets visitors request different operations on
    each class of element. Double dispatch macht nur einen Workaround für etwas was andere Sprachen als Single-Dispatch können.
    
    → aus sicht des rectangle.  dispatch wird immer nur nach receiver-objekt gemacht. daher  verwende ich das andere objekt als receiver. Ich weiß ja selbst schon, dass ich ein rectangle bin und ich weiß dass das andere Shape objekt eine spezifische, passende intersect Methode hat, die rufe ich jetz auf und übergebe mich selbst.
    
    ![Screen Shot 2021-12-02 at 11.04.56 AM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2021-12-02_at_11.04.56_AM.png)
    
- why is A.accept(visitor) ein double dispatch ?
    
    Accept is a double- dispatch operation. Its meaning depends on two types: the Visitor's and the Element's. Double-dispatching lets visitors request different operations on each class of element. (in single dispatch only the type  of receiver of the request determines the operation)
    
- Indirektion
    
    In [computer programming](https://en.wikipedia.org/wiki/Computer_programming), **indirection** (also called **dereferencing**) is the ability to reference something using a name, reference, or container instead of the value itself. The most common form of indirection is the act of manipulating a value through its [memory address](https://en.wikipedia.org/wiki/Memory_address).
    
- Why Uniform Acces Principle ? #
    
    no diff if stored or computed value 
    
    This gives an object the flexibility to change between the two easily as well as removing what is usually an unnecessary concern from the client. It's an important part of encapsulation - or at least the data-hiding aspect of encapsulation.
    
- Was ist das eigentliche Ziel von direct mapping ?
    
    durch Anlehnung des Designs an die modulare Struktur der Realität erreichen wir COMPATIBILITÄT MIT ANDEREN MODULEN die auch dieser Regel folgend designed wurden. 
    
- Disadvantage Factory Method
    - A potential disadvantage of Factory methods is that clients might have to sub-class the creator class just to create a particular concrete product object.
    - Subclassing is fine when the client has to subclass the creator class anyway, but otherwise, the client now must deal with another point of evolution.
- Criteria for good software
    
    ![Screen Shot 2022-02-21 at 2.32.21 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2022-02-21_at_2.32.21_PM.png)
    
- why is extendibility part of external criteria?
    
    → feature requests werden schnell umgesetzt
    
- robustness
    
    Software soll auch nichts schädliches machen, auch wenn das nicht in der Spezifikation steht. Z.b. Taschenrechner Result Button soll nicht Festplatte löschen. 
    
- efficiency
    
    ... effizienz macht eher mit Methoden Sinn, die häufig ausgeführt werden. 
    
- modul im folgenden Kontext
    
    meint meistens eine Klasse. kann auch in manchen Zusammenhängen ein Paket sein etc.
    
- Woher werden Artefakte geladen?
    
    Maven Central. wenn es schon da ist, aus dem lokalen Repository. 
    
- Vorteile von Maven Dependencies
    - Ich kann die Version festsetzen eines Sofwareartefaktes welches ich als Dependency angebe. → mit dieser Version habe ich Funtionalität getestet.
- Wichtiges Beispiel für “verletzt open/closed principle”
    
    abstrakte klasse ist nie “closed for use”.
    
- High Coupling erzeugt welche Probleme ?
    
    hänge von vielen Modulen ab um Klasse nutzen/kompilieren zu können.
    
    - brauche andere Module um meine Klasse zu verstehen
    - brauche andere Module um meine Klasse wiederverwenden zu können
    - fehler aus anderen Klassen bringe ich evtl. mit / gebe weiter wo ich wiederverwendet werde.
- Problem von Player in P
    
    Proliferation of classes - Concept vs Behaviour → In den Modi wird teilweise nur ein Subset der Player-Methoden verwendet. Es wurde implizit zwischen zwei Playerobjekten abstrahiert indem nur 1 Klasse. → kleines Ausmaß, not so bad. 
    
- Gibt es unnütze Klassen im P ?
    - auf die nur zugegriffen wird: Felder.Feld (?)
- Was lässt die Anwendung von Stragegy / Factory Method in P nicht zu  ?
    
    Dynamisches Austauschen/Hinzufügen von Strategien / Factories. 
    → beser Objekt machen. 
    
- Wie z..B. Felder Factory Method verbessern?
    
    Anwendngs-Indikation für Stragegy pattern: Klasse hat mehrere Behaviours, die mit Conditionals unterscheiden werden.  
    
- Draw UML of RuleSet idea.
- why sometimes not good to use subclassing to extend functionality?
    
    con: 
    
    - statisch. Kann nicht mehr zur Laufzeit verändert werden.
    - kann zusätzliche Funktionalität nicht beliebig kombinieren (altert messaging example (guru) (wie bei decorator Pattern möglich) die einzelnen Kombinationen müsste man jeweils als eigene Subklasse implementieren.
    - man kann mit Sublassing nicht die selbe Erweiterung mehrfach verschachtelt anwenden (z.B. textView umrahmen und nochmal umrahmen)
- Diffs Structural vs. Behavioral Design Patterns
    - Structural patterns explain how to assemble objects and classes into larger structures while keeping these structures flexible and efficient.
    - Behavioral design patterns are concerned with algorithms and the assignment of responsibilities between objects.
- Patterns Matrix
- Welche Faktoren hängen mit Faultrate im Code zusammen ?
- Warum ist GUI → Businesslogic im P kein Command Pattern ?
    
    keine Queue, asynchrone Componente (kein Undo etc. Möglich) 
    

Software design methods fulfill criteria :

- Modular decomposeability Criterion + Anforderung daran + Vorteil
    
    → decompostition of systems into subsystems, in order to seperate the workload for seperate subsystems amongst different groups/people. 
    
    → dependencies between these parts need to be known in order to track them and kept to a minimum.  (dependency management). 
    
- Modular composeability Criterion
    
    → software elements can be freely combined with one another and be reused in environments other than the one they were originally intended for. 
    
    → elements are reusable and designed to perform well defined tasks that are usable in different contexts. 
    
    → elements are sufficiently autonomous and independent from their immediate goal.
    
    (easy example: no hardcoded paths to file on disk)
    
    unix shell consists of input and output streams that can be piped together and combined. 
    
- Modular understandability criterion Wann erreicht?
    
    → a method of software development favours modular understandability, if a reader can understand each module without having to understand the others, or, at worst, having to only examine a few others. 
    
- Modular continuity
    
    a design approach fulfills mudular continuity, if in the architecture that it produces, the size of a change in the problem specification causes only a change in one modul or a small number of modules. 
    
    → change in implementation is proportional to change in specification.
    
    → magic numbers → define constants with expressive names instead of hardcoding numeric or textual constants. (example: window resolution changes; small workload if changeable in one place in the code.)
    
- Modular protection + example
    
    effect of an abnormal condition occuring at runtime will remain confinded to the one module, or at worst, propagate to only a few neighbouring modules. 
    
    → fehler im Modul selbst behandeln. oder wenn nicht möglich eine abstraktere Fehlerbeschreibung weitereichen. Sodass der Aufrufer versteht was passiert. 
    
    → example for modular protection: validating input at the source. → a module passing data to another module is also responsible for checking validity.
    

(Cereal, Milk 5 → Ziele)

Rules

- modularity/direct mapping rule?
    
    the modular structure devised in the process of building a software system should be compatible with any other modular structure devised to model the real world. 
    
    program "what" and not "how".  → 
    
    continuity: keeping a trace of the problem's modular structure in the solution's structure makes it easier to assess and limit the impact of changes. → Änderungen der Anforderungen kommen aus Änderungen in der realen Welt. Also bei gleicher Struktur sind diese Anpassungen in der Umestzung leichter zu lokalisieren und zu limiteren. 
    
    decomposibility: work done to analyse the modular strucure of the problem will provide a good starting point for the decomposition of the software. 
    
- modularity/ few interfaces + Bsp.
    
    every module should communicate with as few others as possible.
    
    → changes might have effect on communicating modules. so less is best.
    
    Bsp: Schichtenarchitektur → achieve with layering. layers only communicate with adjacent layers.
    
    →  Indirektion → Bsp. N Sprachen für M Platformen implementieren → N*M Aufwand. Besser → Jede Sprache in eine Virtual machine und diese für jede Plattform Implementieren. (n + m Aufwand).
    
- Modularity/ Small interfaces + why
    
    If two modules communicate, they should exchange as little information as possible.  (size of interface is number of communicated variables and complexity of variables) 
    
    Module kommunizieren praktisch über ihre Methoden → je mehr Parameter eine Methode erwartet, desto unwahrscheinlicher wird es, dass ich diese in einem anderen Kontext verwenden kann. 
    
- Modularity/ Explicit Interfaces + counterexample
    
    whenever two modules communicate, this must be obvious from the text of one or both. 
    
    Counterexample: A changes a variable that B will use. So here it's hidden that A communicates with B. 
    
- Modularity/ Information Hiding
    
    The designer of every module must select a subset of the module's properties as the official information about the module, to be made available to authors of client modules. 
    

(5 → ways to achive these)

5 Principles Mayer: 

- Linguistic Modular Units
    
    Modules must correspond to syntactic units in the language used. 
    
    → sprache muss ermöglichen, dass ich die Dekomposition so wie geplant durchführen kann. Die designten Module müssen auch separat kompilierbar sein.
    
- Self-Documentation
    
    All Information about a module should be part of the module itself. 
    
- Uniform Access Principle
    
    → all services of a module shold be accessible through uniform notation, that does not betray if values are computed or come from storage.
    
    Example: Bank Account Ballance computed or stored? account.ballance() Zugriff nicht davon abhängen, wie der Wert zustande kommt: ensures continuity. 
    
- Open / Close Principle + Bsp.
    
    Modules should be both open and closed
    
    Open Module: Is still available for extension to add methods and fields.
    Closed Module: Is ready for use and has a well defined, stable interface.
    
    Bsp. Klasse in Java ist closed for reuse wenn es eine Instanz davon gibt. Aber solange sie nicht final ist und einen öffentlichen Konstruktor hat → diese erfüllt das Open-Close Prinzip. 
    
    Abstrakte Klasse erfüllt das nicht, erfüllt nicht closed for use. (Es ist nicht immer schlecht so ein Prinzip zu verletzen; man sollte sich nur bewusst sein, dass z.B. abstrakte Klassen so sind.
    
- single choice principle
    
    By requiring that **knowledge of the list of choices be confined to just one module**, we prepare the scene for later changes: if variants are added, we will only have to update the module which has the information — the point of single choice.
    
    - whenever a software system must support alternatives, one and only one module should know the exhaustive list.
    
    → nur eine Stelle kennt kontret die Implementierungen dieser Möglichkeiten. Dadurch werden später Änderungen leichter.
    

(Mayer Besuch, 5 → )

Metrics (messbar) and Heuristics of good design

- low coupling + measured how + why important
    
    coupling measures "interconnectedness"
    
    Class A is connected to class B if requires class (directly or indirectly) B to compile. 
    
    - – a class that depends on 2 other classes has a lower
    coupling than a class that depends on 8 other classes
    - – coupling measures the strength of dependency between classes and packages.
    - undesirable because: changes in related classes force local changes
    this class is harder to understand in isolation
    this class is harder to reuse because its use requires
    the inclusion of all classes it is dependent upon
    
    →no coupling at all is not desirable either (decomposability)
    
- high cohesion + decided how
    
    Elemente der Klasse gehören zusammen. 
    
    - cohesion measures the strength of the relationship
    amongst elements of a class
    - classes with high cohesion can often be described by
    a simple sentence
    - all operations and data within a class should naturally
    “belong” to the concept the class models
    - when methods within a class use a "similar" set of
    instance variables, the class is considered highly
    cohesive
    
    → *high cohesion* and *low coupling* is preferred
    	
    
- 2 arten von Kohäsion
    
    logical vs. temporal cohesion: 
    
    logical: elements of a class perform one kind of logical function
    
    temporal: all elements of a class are executed together. 
    
- worauf weist eine niedrige Kohäsion evtl. hin?
    
    *Wenn Klassen niedrige Kohäsion aufweisen, ist das ein Zeichen dafür, dass die Klasse ein zu grobkörniges Konzept der Realität abstrahiert. Der Klasse wurden Aufgaben zu gewiesen die weiter auf verschiedene Objekte aufgeteilt werden hätten sollen.* 
    

(Lineal an der Tür 2 (+2 Details zu 2)→ wie messen wir die Modulariät)

- God Class Problem
    - Heuristik 1:
    
    Klasse mit zu vielen Verantwortlichkeiten. 
    
    Distribute system intelligence as uniformly as possible,
    that is, the top-level classes in a design should share
    the work uniformly.
    
- Con von Accessor Methods.
    
    zB: getx(), gety() in class Point.
    
    Accessor methods indicate poor encapsulation of related data and
    behavior. Warum macht scheinbar eine andere Klasse Operationen auf dem Punkt? Das ist evtl. nicht mehr objektorientiert. 
    
    → Often the client that is using accessor methods is a god class
    capturing centralized control that requires data from the mindless
    point.
    → beware of classes that have many accessor methods defined in
    their public interface. Having many implies that related data and
    behavior are not kept in one place.
     
    

Proliferation of Classes:

- The Proliferation of Classes Problem 1 — Concepts vs. Behavor
    1. CP1: Modelierte Abstraktionen sollen Klassen sein und nicht bloß die Aufgaben die Objekte übernehmen.
    
    Family1: Mother, Father, Children
    
    Family2: Person,Person, Person[]
    
    Distinction depends on differing behavior. Before creating new
    classes, be sure the behavior is truly different and that you do not
    have the situation where each role is using a subset of Person
    functionality
    
- Proliferation of classes Problem 2 — Classes to eliminiate
    
    → Eliminate irrelevant clases from your design
    → Irrelevant Class: one that does not have a meaningful behaviour in the domain of the system. Could be classes that have no operations other than accessors and print functions. 
    
    → Eliminate classes outside the system 
    
    Hallmark of such classes is an abstraction that sends messages to
    the system domain but does not receive message sends from other
    classes in the domain.
    
- Proliferation of classes Problem 3  — No Operations as Classes
    - Do not turn an operation into a class.
        - Be suspicious of any class whose name is a verb or is derived
        from a verb, especially those that have only one piece of
        meaningful behavior
        - Ask if that that piece of meaningful behavior needs to be migrated
        to some existing class
    
    → Objekte bilden Entitäten der realen Welt ab. Normalerweise haben diese Entitäten Aktivitäten, aber das sind in der Regel keine Objekte. 
    

- Beziehungen
    
    ![Screen Shot 2021-11-05 at 5.12.54 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2021-11-05_at_5.12.54_PM.png)
    
- how to minimize coupling
    
    unten: Anstatt Klasse Restaurant Patron hat Abhängigkeit zu 3 versch. Klassen 
    
    → Verkapseln der drei einzelnen Klassen zu Meal = eine Abhängigkeit. 
    
    ![Screen Shot 2021-11-05 at 6.47.45 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2021-11-05_at_6.47.45_PM.png)
    
- Containment Relationship - 5 Heuristics
    - UR2: If class A contains objects of class B, then A should be sending
    messages to its fields of type B.
        
        This heuristic prohibits:
        – Orphaned fields (ones that are never used)
        – Fields that are only accessed in get/set methods
        The one exception is **container classes (= collection)**
        
    
    - UR3: Most of the methods defined on a class should be using most of
    the fields in the class most of the time
    - UR4: Classes should not contain more objects than a developer can
    fit in his or her short-term memory. A common value for this number is 6.
    - Narrow and deep containment hierarchies
        
        ![Screen Shot 2021-11-05 at 7.09.48 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2021-11-05_at_7.09.48_PM.png)
        
    - No Talking Between Fields
        
        UR6: Objects that are contained
        in the same containing class
        should not have a uses
        relationship between them.
        The containing class should send
        messages to the contained
        objects
        
        ![Screen Shot 2021-11-05 at 7.15.57 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2021-11-05_at_7.15.57_PM.png)
        

(Contraindikationen von guten DesignCriteria)

Design Patterns:

- Pattern
    
    Entwurfsmuster = Wiederverwendbares Design.
    
    A pattern describes a problem which occurs
    over and over again in our environment,
    and then describes the core of the solution to
    that problem, in such a way that you can use
    this solution a million times over,
    without ever doing it the same way twice.
    
- Structure
    
    ![Screen Shot 2021-11-05 at 7.45.35 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2021-11-05_at_7.45.35_PM.png)
    
    ![Screen Shot 2021-11-05 at 7.45.16 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2021-11-05_at_7.45.16_PM.png)
    

→ where used:  is / could be ?

- Stragegy Pattern
    
    **Es geht darum verschiedene Strategien ein Problem zu lösen sinnvoll im Programm umzusetzen:**
    
    - Problem: Many related classes differ only in their behavior; needs different variants of algrorithm. → Die Aufgabe ist immer die selbe, nur wie diese durchgeführt wird unterscheidet sich.
    - Strategy is a behavioral design pattern that turns a set of behaviors into objects and makes them interchangeable inside original context object.
    
    - client besorgt sich ein Strategieobjekt. → Abhängigkeit zu der Schnittstelle Strategy(Abstrakt (oder auch Interface?) weil kusiv) → besser Abhängigkeit zur oberen Klasse der Hierarchie. Kennen nur die abstrakte Schnittstelle, nicht die konkreten Strategies. 
    
    ![Screen Shot 2021-11-16 at 2.11.36 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2021-11-16_at_2.11.36_PM.png)
    
    → nachteil: Wir müssen alle Informationen als Parameter übergeben, was gegen Small Interfaces verstoßen könne, weil ich eine lange Liste an Paramtern an Strategy übergeben muss. 
    
    → wenn verschiedene konkrete Implementierungen verschiedene Argumente braucht → Stragegy muss alle möglichen benötigten Argumente abdecken, die von mind. einer konkreten Implementierung benötigt werden.
    
    alternative: Kontext übergibt sich selbst. Dann muss ich nur einen Wert übergeben → Strategie nimmt sich die jeweils benötigten Daten raus. 
    
- Collaboration between Context and Strategy
    
    Strategy and Context interact to implement chosen algorithm
    – Context passes all required data
    – Or Context passes itself (Minimizes redundant data + Couples Strategy to Context)
    
- Example. for Strategy - Formatting Documents
    
    There is a Variety of formatting algorithms available that must break text into lines, lines into columns, and so on, taking into account the user's desires
    
    Zwei problematische Möglichkeiten:
    
    ![Screen Shot 2021-11-16 at 3.52.04 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2021-11-16_at_3.52.04_PM.png)
    
    ![Screen Shot 2021-11-16 at 3.49.42 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2021-11-16_at_3.49.42_PM.png)
    
    Strategy Pattern anwenden:
    
    ![Screen Shot 2021-11-16 at 3.58.14 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2021-11-16_at_3.58.14_PM.png)
    
    → repair() wird an Strategy delegiert. Wir rufen die Strategie (hier Compositor genannt) auf einem anderen Objekt auf. 
    
    → ist jetzt erweiterbar, weil ich neue Instanzen von Compositor hinzufügen kann .
    
    ![Screen Shot 2021-11-16 at 3.59.36 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2021-11-16_at_3.59.36_PM.png)
    
- Wann Strategy Pattern anwenden? (4)
    
    **Indicators**
    
    - Many related classes differ only in one respect of their behavior
    - You need different variants of an algorithm
    - An algorithm uses data that clients shouldn't know about
    - A class defines many behaviors, and these appear as multiple
    conditional statements in its operations
- Vorteile des Strategy Patterns (3)
    - Hierarchies of Strategy classes define a family of algorithms or
    behaviors for contexts to reuse.
    - Inheritance can help factor out common functionality of the
    algorithms.
    - Alternative to subclassing. 
    Subclassing ...
    – mixes the algorithm implementation with Context's
        
        – makes Context harder to understand, maintain, and extend
        – can't vary the algorithm dynamically
        – leads to many related classes only differing in algorithm
        – hinders switching algorithm independent from Context
        
    - Strategies eliminate conditional statements
- Probleme des Strategy Patterns
    
    Clients must be aware of different strategies and how they differ
    
    – Clients might be exposed to implementation issues.
    
    – Use Strategy only when the variation in behavior is relevant to
    clients.
    
    Increase the number of objects
    
    – Sometimes you can reduce this overhead by implementing
    strategies as stateless objects that contexts can share.
    
    - Any state is maintained by the context, which passes it in each
    request to the Strategy object.
    - Shared strategies should not maintain state across invocations.
- Alternative Implementierungen für Strategy Pattern
    1. Alt
    
    → context hat die Informationen, Strategy braucht sie. Unterschied ist hier: push vs pull.
    
    → nachteil bei push → da Context die konkreten Strategies nicht kennt, kann es nicht vorhersehen welche Daten gebraucht werden und muss daher alles pushen.
    
    → pull: weniger Informationsoverhead. Aber stärkere Kopplung (weil ich für diese Richtung des Zugriffs ja den gesamten Kontext mit übergeben muss.)
    
    ![Screen Shot 2021-11-16 at 4.52.00 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2021-11-16_at_4.52.00_PM.png)
    
    1. Alt: (Steigerung Effizienz) 
    
    A template parameter is **a special kind of parameter that can be used to pass a type as argument**
    
    ![Screen Shot 2021-11-16 at 5.02.00 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2021-11-16_at_5.02.00_PM.png)
    
    1. Alt: (Default Behaviour + Optional Strategy Objects) → easier for clients to use. 
        
        ![Screen Shot 2021-11-16 at 5.11.26 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2021-11-16_at_5.11.26_PM.png)
        
- Beispiel für Stragegy in Library
    
    Collections.sort() - Argument Comparator → Sortiert nach individueller compare methode 
    

- State Pattern
    
    Problembeschreibung: An object’s behavior depends on its state and it must change its behavior at run-time.
    
    - client ist immer derjenige, der die nächste Aktion triggern will. Greift auf Context zu. Auf basis des Zustands unterscheidet sich diese Operation.
    - Einziger Unterschied zu StrategyPattern ist, dass Client nicht auf State zugreifen kann.
    - Wenn wir eine Operation auf dem Context aufrufen, wird das an das State-Objekt weitergegeben und das kann seine zustandsabhängige Aktivität ausführen.
    - Bei Strategy ist oft einfach so, dass wenn ich eine Operation auf dem Kontext aufrufe, dann kann die Implementierung der Operation in der ContextKlasse einen Teil selbst ausführen, und nur ein Teil davon ist Strategie-Abhängig und wird delegiert. Bei State sind das aber genau die gleichen Methoden → der State gesamte Methoden aus dem Kontext ... und zustandsabhängig implementiert.
    
    ![Screen Shot 2021-11-16 at 5.19.20 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2021-11-16_at_5.19.20_PM.png)
    
- Collaborations State Pattern
    
    ![Screen Shot 2021-11-16 at 6.08.43 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2021-11-16_at_6.08.43_PM.png)
    
- Beispiel State Pattern
    
    Allg:
    
    ![Screen Shot 2021-11-16 at 6.18.19 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2021-11-16_at_6.18.19_PM.png)
    
    Bsp:
    
    ![Screen Shot 2021-11-16 at 6.18.23 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2021-11-16_at_6.18.23_PM.png)
    
    State objekt kennen wir nur durch die Schnittstelle. Da steckt eine Instanz der Subklassen von State drin → hier wird konkrete Implementierung ausgeführt. 
    
    Der Zustand des Kontextes kann sich verändern. Oft ist es so, dass der Zustand mit der Operation selbst zu tun hat. Beispiel ist ein Netzwerkprotokoll → Socketverbindung hat Operation "Verbindung herstellen" sobald der Verbunden ist(Socket ist im Zustand verbunden)  kann ich lesen/schreiben, zuvor nicht. Allerdings darf ich dann auch nicht nochmal verbinden.
    
- Fixed vs. Variable Aspects of State Pattern
    - Fixed:
    
    Schnittstelle → Operationen die der Kontext durchführen kann. Dabei unterstützt mich das Muster nicht. Wenn ich neue Zustandsabhängige OP hinzufügen will, dann muss ich diese Operationen in der State-Hierarchie Spiegeln. Geht also nicht modular. Daher sagen wir die Schnittstelle ist fest.
    
    - Variabilität:
    
    Polymorphie stellt hier die Variabilität her —  die Möglichkeit zur Laufzeit was auszutauschen. (das geht eig. allg. immer mit Polym.)
    
- Anwendbarkeit State Pattern
    - Indicators
    – Behavior depends on object's state
    – Must change its behavior at runtime
    
    – Operations have large multi-part conditional statements
    – That depend on object's state
    – Conditionals test enumerated constants
    – Several operations contain same conditional structure
    
- Unterscheidung Strategy vs State → Abhängigkeit der Alternative
    
    Wenn die Auswahl der Alternative abhängt vom internen Zustand des Kontextes → State Pattern. Wenn die Alternative vom Nutzer gewählt werden kann: → Strategy Pattern. 
    
    → ist in der Implementierung oft nicht so unterschiedlich → in der Dokumentation Intention angeben. Für später Erweiterung durch andere Entwickler. 
    
- PRO/CON - State Pattern
    
    PRO: Erweiterbar und Expliziter Zustand
    
    CON: Code ist verteilt, Mehr Objekte 
    
    - Localized state-specific behavior
    – Partitioned for different states
    – Behavior associated with a particular state in one object
    – New states and transitions can be added
    - Better way to structure state-specific code
    - Logic determining state transitions doesn't reside in monolithic if
    or switch statements → explizitere/übersichtlicherere Def. des Übergangs
    - Encapsulating each state transition and action in a class elevates
    the idea of an execution state to full object status
    - Clear structure of code
    - Intent explicit in code
    
    - Explicit state transitions
    - Protect the Context from inconsistent internal states
    – State transitions are atomic from the Context's perspective
    – Rebinding one rather than several variables
    - Behavior for different states distributed across several State
    subclasses.
    - This increases the number of classes and is less compact than a
    single class.
    - It is not explicit in the design that a State object is performing
    behavior on behalf of a Context object.
- Implementation alternatives - State Pattern.
    
    ![Screen Shot 2021-11-16 at 7.33.43 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2021-11-16_at_7.33.43_PM.png)
    
    → Unten: wenn ich subklassen von Kontext implementieren wollen würde, müsste ich ja bei der Erzeugung des Objektes den Zustand schon festlegen. Dann bräuchte man dynamsiche Vererbung (gibt es z.B: in smallTalk) . 
    
    ![Screen Shot 2021-11-16 at 7.37.42 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2021-11-16_at_7.37.42_PM.png)
    

- Command Pattern - Problemdefinition
    
    Problem Description:
    
    - Part of my program knows how/where to handle requests  **(tatsächliche Methode welche z.B. Linien und Rechtecke zeichnet)**
    - Another part knows when to issue a request **(Beispiel Toolbar Paint Tool)**
        
        – Called “invoker” 
        – Possibly in a library
        – Cannot know implementation of request handling
        
    - Requests are not processed immediately.
    – E.g., they are stored in a queue for later processing.
    - Want to keep track of handled requests and undo the processing **(Undo list)**
- EXAMPLE
    
    ![Screen Shot 2022-02-27 at 4.38.25 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2022-02-27_at_4.38.25_PM.png)
    
- CP UML
    - Obere Hälfte: Bibliothek, die wir konfigurieren, indem wir die Schnittstelle der Library implementieren. Bibliothek weiß wie die Ausführung ablaufen soll und durch das Command Pattern können wir unsere Benutzerdefinierte Funktion reinschieben.
    
    ![Screen Shot 2021-11-17 at 9.06.05 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2021-11-17_at_9.06.05_PM.png)
    
    - Command provides an interface for executing commands
    - ConcreteCommand (z.B. Button, Shortcut) provides binding between a receiver and
    command. It implements execution by calling receiver methods.
    - Receiver actually performs the command processing
    - Client creates a concrete Command object, sets its receiver, and
    registers command with invoker
    - Invoker issues command when an invoker event occurs
    
    ![https://refactoring.guru/images/patterns/diagrams/command/solution3-en-2x.png](https://refactoring.guru/images/patterns/diagrams/command/solution3-en-2x.png)
    
- Command Pattern - Intent
    - A command encapsulates a request as an object. A reference to the
    command is given to an invoker for later invocation.
    
    Intent:
    
    - de-couple the event triggering a command from the processing
    associated with the command.
    - the invoker of a command knows about the trigger event but
    does not need to know anything about command’s processing.
    The creator of the command class knows about the processing
    but nothing about the invoker’s event.
    - With commands, you can control their selection, sequencing,
    queue them, undo them, and otherwise manipulate them. (→ Commands sind First Class Objekte -> die kann ich in Listen speichern → Protokolle. )
    - **Commands are an object-oriented replacement for function
    pointers.**
    
- Wann CP anwenden?
    
    Use the command pattern when you want to:
    
    - parameterize objects by an action to perform (menu items) (generic type arguments)
        
        → i.e. Have a user-programmable button in the menue. 
        
    - specify, queue, and execute requests at different times
    (command object can have lifetime independent of the original
    request)
    - respond to library events in client code
    (library calls client functions even though the library knows
    nothing of client code)
- Nachteil von CP
    
    Objektkomposition und Indirektion → wir rufen auf einer Schnittstelle eine Methode auf und wissen nicht, welche konkrete Implementierung dran hängt. → durch die Indirektion wird das Programmverständnis etwas erschwehrt. 
    
- Alternative zu CP
    
    Lokaler Kontext: x y Koordinaten  und BEFORE STATA to undo action. 
    
    hier Nachteil: 
    
    → Variable Command kann ich nicht mehr ändern nachdem die Closure erzeugt wurde.
    
    ![Screen Shot 2021-11-17 at 10.05.20 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2021-11-17_at_10.05.20_PM.png)
    

- Interpreter Pattern
    
    → wenn ich Eingaben habe, die einer bestimmten Grammatik folgen. 
    
    → aus der Eingabe wird ein abstrakter Syntaxbaum erzeugt. Muss also parsbar sein. 
    
    → in der Regel nicht sonderlich effizient. Nur auf kleine Eingaben verwenden. 
    
- Interpreter Pattern UML
    
    ![Screen Shot 2021-11-17 at 10.16.07 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2021-11-17_at_10.16.07_PM.png)
    
- Vorteile Nachteile Int Pattern
    - It is easy to change and extend the grammar;
    • Implementing the grammar is easy too;
    • Adding new ways to interpret expressions is easy. (einfach neue Methode)
    - But: Complex grammars are hard to maintain.

- Composite Pattern
    
    **Composite** is a structural design pattern that lets you compose objects into tree structures and then work with these structures as if they were individual objects.
    
    → Zusammengesetzte Teile wobei Teile und das Ganze ähnlich sind, ähnliche Schnittstelle habe und diese gleich behandelt werden können. 
    
- Composite Pattern  UML
    
    Component : Schnittstelle
    
    Wenn ich compute aufrufe→ wird auf allen children compute aufgerufen.
    
    ![Screen Shot 2021-11-18 at 7.57.59 AM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2021-11-18_at_7.57.59_AM.png)
    
- Implement. Alts. CP
    
    Child-Management Operationen in Component oder Composite deklarieren?
    
    safety vs. lesbarkeit/transparency 
    
    ![Screen Shot 2021-11-18 at 8.19.44 AM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2021-11-18_at_8.19.44_AM.png)
    
    - What to put into the Component interface?
    - – To achieve high regularity, put as much common operations into
    Component as possible
    - – Possibly provide default implementation in Component
    - – But design principle says: only put operations in super class that
    are meaningful for all sub classes
- Composite Patter - Vorteile/Nachteile
    - easy to use - weil ich alles gleich verwenden kann und
    - easy to add components or composites
    - schwieriger Verwendung von bestimmten Komponenten zu kontrollieren/beschränken.
    
    ![Screen Shot 2021-11-18 at 8.34.18 AM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2021-11-18_at_8.34.18_AM.png)
    
    - Regularity:
    – Composition can be recursive
    – Client does not need to distinguish leafs and composed objects
    – No conditional code in clients
    - Can easily add new components
    - Hard to restrict components of a concrete composite
    – Cannot rely on type system to enforce constraints

- Decorator Pattern
    - Attach additional responsibilities to INDIVIDUAL object dynamically. Decorators provide a flexible alternative to subclassing for extending functionality.
    - Funktionen in Form von Dekoratoren dynamisch hinzufügen. Dekoratoren können verschachtelt sein.
    - Können zur Laufzeit zu Objekten hinzugefügt oder weggenommen werden.
    
- DP UML
    
    Dekorator wird über das Component Objekt drübergestülpt.
    
    super.operation() reicht an eingekapselte Methode weiter. (?)
    
    ![Screen Shot 2021-12-01 at 3.59.12 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2021-12-01_at_3.59.12_PM.png)
    
- wann decorator pattern nicht verwenden?
    - Interface von Component darf nicht zu groß sein, denn alle konkreten Dekoratoren müssen diese implementieren → dann hätten wir zu große Komplexiät. Verschachtelte Methoden reichen nur die Methodenaufrufe weiter.
- downsides - worauf achten beim Decorator Pattern ?
    1. Component und decorator sind unterschiedliche Objekte! -
    
    → Client muss die Component über den Decorator verwenden um die Extension zu nutzen. 
    
    → Gefahr: man kann die in den decorator eingebettete Component  (mit Referenz )weiter verwenden und den decorator umgehen. 
    
    1. man hat viele Kleine Objekte (die die ursprüngliche Component umschließen) die nur geringe Modifikation der Methodenaufrufe umsetzen. → Code wird schwerer zu lesen und komplizerter: beim debugging muss man sich durch viele Delegationsmethoden durchklicken bis man zum eigentlichen Component Objekt mit seinem Zustand angelangt. 
    
- welchen Vorteil bietet decorator Pattern bezüglich der Complexität der Klassenhierarchie  ?
    - Avoids feature-laden classes high up in the hierarchy (= component muss nicht alles können)
    - But still enables flexible extensions
    - Little preparation for unforeseen extensions in Component
    required
- Diffs Strategy vs. Decorator Pattern
    
    → bei decorator  wird eine Hülle um das component objekt gelegt, während beim Strategy Pattern das Objekt im inneren verändert wird. Daher gibt es bei Strategy nicht das Problem, dass jemand noch eine Refernz auf das ursprüngliche Objekt hat und die Dekorationen umgeht, wir rufen die operation immer noch über das interface von strategy aufrufen und strategy verwendet intern die jeweilige Strategie. Nachteil bei Strategy ist wir können keine neue Funktion hinzufügen, wir können nur dort wo der Kontext die Beeinflussbarkeit vorgesehen hat, können wir die konfigurieren. Decorator ist hier flexiebler. Die Komponente bekommt den Decorator der übergestülpt wird gar nicht mit. 
    

- Visitor Pattern
    - es gibt hier keine Containment relationship → Visitor muss erzeugt werden und dann z.B. in einenm for-loop in den selben scope mit der Liste von Elementen gebracht werden, sodass die Elemente auf ihre entsprechende Implementierung im Visitor zugreifen können.
    - With the Visitor pattern, you define two class hierarchies: one for the elements being operated on (the Node hierarchy) and one for the visitors that define operations on the elements (the NodeVisitor hierarchy.
    - You create a new operation by adding a new subclass to the visitor class hierarchy.
- Vergleich mit ähnlichem Pattern
    
    Composite Pattern ist ähnlich: aber dort haben wir nur eine festgelegte Anzahl an Operationen die auf Objektstruktur ausgeführt werden können sollen. Aber bei Visitor wollen wir diese Operationen erweiterbar haben. 
    
- UML Visitor
    
    → Visitor Objekt läuft an Objektstruktur bestehend aus verschiedenen Objekten (z.B. Baumstrukur) entlang und sammelt informationen ein. Visitor 1/2 → z.b. Preis Berechnen Visitor vs. Verbrauch berechnen Visitor; haben dann jeweils eine Methode für jede Objektklasse die in der Klassenstruktur vorkommen kann. In den klassen der Objektstruktur muss jeweils eine MethodeA liegen, die den Visitor Akzeptiert (accept(visitor))  und darin dann die visitor.AOperation() darin selbst auftruft.
    
    Vorsicht bei 
    
    ![Screen Shot 2021-12-02 at 10.11.17 AM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2021-12-02_at_10.11.17_AM.png)
    
- Visitor Pseudocode example
    
    ![Screen Shot 2021-12-02 at 10.18.26 AM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2021-12-02_at_10.18.26_AM.png)
    
    unten: chassis hat keinen Power Verbrauch
    
    ![Screen Shot 2021-12-02 at 10.20.07 AM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2021-12-02_at_10.20.07_AM.png)
    
- Wann Visitor einsetzen?
    - You want to perform operation on data structures
    – Classes potentially are not uniform
    – Operation depends on concrete classes
    - There are many unrelated operations
- Wann Visitor nicht einsetzen ?
    
    Classes defining data structure rarely change
    – Otherwise all visitor implementations have to change! (sonst müssste man das Interface und alle Visitors ändern)
    
    - But Operations may change frequently. (per class operation can be changed easily in Visitor Class (auch nicht so anders...))
- Implementation Alternativen
    1. who passes visitor?
    
    – Pass visitor to data structure's accept method 
    
    – May also be performed by visitor
    
    1. Who is responsible for traversing an object structure?
    – Object structure
    - Collection node forwards accept() to all its children
    – Visitor
    - visit method for collection node performs traversal
    • Potentially duplicate traversal code in visitors
    • Possibly include in abstract Visitor class

- Bridge Pattern
    
    Der abstrahierte Teil des Programms (jener der für alle Anwendungsbereiche gleich bleibt, z.B. die GUI (abstrakt) die wir auf verschiedenen Plattformen (anwendungsb) laufen lassen wollen, bekommt ein Objekt welches die Plattformspezifischen Methoden enthält, die er dann in seinen Operationen verwendet. 
    
    ![Screen Shot 2022-02-24 at 3.56.14 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2022-02-24_at_3.56.14_PM.png)
    
- Bridge Pattern UML
    
    ![Screen Shot 2021-12-02 at 12.03.58 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2021-12-02_at_12.03.58_PM.png)
    
- When use Bridge Pattern
    - both the abstractions and their implementations should be extensible by subclassing. In this case, the Bridge pattern lets you combine the different abstractions and implementations and extend them independently.
        
        **Use the pattern when you need to extend a class in several orthogonal (independent) dimensions.** 
        
        → Erst wollten wir die verschienen Arten von UI-Fenster als Vererbungsbaum unter Window darstellen (1. Dim), danach wollten wir das ganze auf verschiedenen Plattformen laufen lassen (2. Dim). 
        
    - you want to avoid a permanent binding between an abstraction and its implementation. This might be the case, for example, when the implementation must be selected or switched at run-time. → hier kann der Verlust des Zustands im Implementation-Objekt ein Problem sein.
    1. wir wollen alles miteinander kombinieren können: 
    
    ![Screen Shot 2021-12-02 at 12.09.19 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2021-12-02_at_12.09.19_PM.png)
    
    1. oder: wir wollen die selbe Implementierung zwischen versch. Klassen teilen: 
        
        ![Screen Shot 2021-12-02 at 12.11.34 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2021-12-02_at_12.11.34_PM.png)
        
- Bridge pattern code example (shapes)
    
    ![Screen Shot 2021-12-02 at 12.13.36 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2021-12-02_at_12.13.36_PM.png)
    
- limitations of BP
    - all the methods of implementation must be declared at the interface. → jene die für alle Implementierungen zur Verfügung stehen. Wenn ich eine bessere spezifische Implementierung geschrieben habe → könnte darauf nicht zugreifen, weil nicht im Interface spezifiziert.
        
        ![Screen Shot 2021-12-02 at 12.32.50 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2021-12-02_at_12.32.50_PM.png)
        
    - wir können im Implementierungsobjekt keinen Zustand haben (weil die Implementierung zwischen verschiedenen Abstraktions-Objekten geteilt werden können sollen). Der Zustand muss also in der Abstraction allein sein.
    

- Kategorien von Designpatterns
    
    Purpose: Behavioral, Structural, Creational
    
    Scope: mainly class-based interactions or  object-based interactions
    
    |  | behavioral | structural |
    | --- | --- | --- |
    | class | interpreter |  |
    | object | command
    state
    strategy
    visitor | bridge
    composite
    decorator |
- Creational Design Patterns

- Singleton Pattern
    
    We must make sure only one instance of a type can be created
    – We want to be flexible to choose which sub-type to instantiate
    • Who is responsible for the creation?
    • How can others access the instance?
    
    ![Screen Shot 2022-01-03 at 7.12.10 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2022-01-03_at_7.12.10_PM.png)
    
    - Private constructor
    – Only Singleton itself can create instance
    - Implicit instance creation (lazy initialization)
    – Implementation of instance():
    – check if theInstance already initialized
    – if not, initialize it
    – return theInstance
- Verletzt welche Principles
    
    Mayer: Open/Close Principle: 
    
    → it breaks the Open/Closed Principle, because the singleton class itself is in control over the creation of its instance, while consumers will typically have a hard dependency on its concrete instance. This disallows the implementation to be changed, without having to make sweeping changes throughout the application.
    
    → ist nicht open for extension → kann nicht von außen verändert werden, wegen der Instance Methode. 
    
    Tipp um das zu umgehen. : Initialisierung nicht in der instance Methode machen, sondern im Konstruktor (instance() ist kein Konstruktor!!!) → der Konstruktor kann das dann von außen Überprüfen ob das Feld schon gesetzt ist, wenn das der Fall ist dann eine Exception werfen. 
    
    → weil ich laut Defintion keine Änderung/neu Instanziierung zulassen darf.  
    

- Abstract Factory Pattern
    
    Abstract factory separates creation from utilization.
    
    → Logic of fittting parts together is always the same; but parts need to be compatible. 
    
    → ensures that all the manufactured products are compatible (from same concrete factory)
    
    Jeweilige konkrete Factory wird dann übergeben und von einem Objekt verwendet um Produkte, immer vom gleichen Typ, zu erzugen.
    
    ![Screen Shot 2022-01-04 at 10.58.28 AM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2022-01-04_at_10.58.28_AM.png)
    
    ![Screen Shot 2022-02-27 at 5.32.55 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2022-02-27_at_5.32.55_PM.png)
    
- use abstract factory pattern when?
    
    **Use the Abstract Factory when your code needs to work with various families of related products, but you don’t want it to depend on the concrete classes of those products—they might be unknown beforehand or you simply want to allow for future extensibility.**
    
    - System should be independent of how its products are created
    - Family of related product objects is designed to be used together
    - Control of which classes objects are created
    - Only reveal the interface of components, not their implementation
- Nachteil abstract Factory
    - Concrete class of factory only appears in one place
    - Single point to switch product family
    - Fixes the set of products that can be instantiated
    → wenn ich ein neues Teil hinzufügen will, muss ich eine neue abstrakte create methode in der abstrakten factory Klasse erzeugen und diese dann in jeder konkreten Factory einzeln implementieren.
    - Complicated (Abstraction hiding behind Abstracion)
- Alternative Implementierung
    
    → erlaube Parametrisierung in den create Methoden um neue Produkte/Produktvariationen adden zu können. 
    
    → damit habe ich mehr Flexibilität Nachteil davon ist, dass ich die Typsicherheit verliere. Kann sein dass ich ein Produkt erzeugen möchte, dass von der konkrete Factory nicht unterstützt wird und das fällt dann erst zur Laufzeit auf. 
    

- The Factory Method Pattern
    
    Abstrakte Klasse Creator hat Lücken = abstrakte Methoden. Diese fülle ich mit Unterklassen welche die Factory Methoden implementieren und darin einen Konstruktor aufrufen. 
    
    ![Screen Shot 2022-01-04 at 11.45.34 AM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2022-01-04_at_11.45.34_AM.png)
    
- Diff Factory Method vs. Abstract Factory Pattern
    
    The factory method is just a method, it can be overridden in a subclass, whereas the abstract factory is an object that has multiple factory methods on it.
    
    → Abstract Factory ist praktisch eine mehrfache Anwendung von Factory Method. 
    
    → bei Factory Method bekommen wir nicht explizit eine konkrete Factory übergeben, sondern wir erwarten das von uns selbst, die richtige creation Methode zu verweden. 
    
- Factory Method Pattern - wann anwenden? + 1 Nachteil
    
    A class cannot anticipate the class of objects it must create
    • Allow customization of objects to create
    • Good use case: Decouple parallel hierarchies, e.g.,
    – a data model of model entities
    – from the representational model.
    – Each data model entity can create corresponding
    representational model entity
    
    **Use the Factory Method when you don’t know beforehand the exact types and dependencies of the objects your code should work with.**
    
    **Use the Factory Method when you want to provide users of your library or framework with a way to extend its internal components.**
    
    Nachteil: schwieriger die Konsistenzbedingungen zu garantieren.. 
    

- Prototype Pattern _ Goal, Problem + Solution
    
    We want to make a copy of an object. 
    
    Problems: 
    
    - some fields might be private, and therefore not accessible from the outside.
    - we have to know the object’s class, so our code becomes dependent on it.
    - sometimes we might not know the concrete object, but only the interface it follows.
    
    Solution:
    
    → wir delegieren die Aufgabe des Klonens an das zu klonende Objekt selbst. 
    
    “Prototypen” Objekte (die geklont werden sollen) implementieren alle ein Interface welches eine clone() Methode zur Verfügung stellt. 
    
- Prototype UML
    
    ![Screen Shot 2022-01-04 at 4.07.13 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2022-01-04_at_4.07.13_PM.png)
    
- Prototype Pattern ist ähnlich zu welchem anderen Pattern?
    
    ähnlich zu Command-Pattern 
    
    Command: ein Teil weiß wie man Operation ausführt, ein anderer weiß wann die Operation auszuführen ist. 
    
    Prototype: Ist hier ähnlich. an der Stelle wo wir wissen wie man den Klon erzeugt, erzeugen wir das Objekt und die Stelle welche die Objekte verwenden soll, der übergeben wir dieses bereits erzeugt Objekt. 
    
- When to use Prototype Pattern?
    - es entscheidet sich erst zur Laufzeit welche Instanzen wir erzeugen müssen.
    - Instanzen sind aufwendig in der Erstellung (evtl. Berechnung) → dann klonen wir besser.
    
    **Use the pattern when you want to reduce the number of subclasses that only differ in the way they initialize their respective objects.** 
    
- Problem wann?
    
    → wenn shallow copy nicht ausreicht. = referenz vs. copy. - aber wir könnten auch deep umsetzen. 
    
    **= all the fields values of the original object are copied to the new object**. If a field value is a primitive type, a shallow copy copies the value of the primitive type. But, if a field value is a reference type, then only the reference is copied, and not the referred object itself.
    

- Builder Pattern Problem + Solution
    
    Wir wollen verschiedene Ausführungen/Variationen von Objekten erstellen. 
    
    z.B. Haus mit oder ohne Garten mit Garage etc.
    
    → 
    
    ![Screen Shot 2022-01-04 at 5.00.14 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2022-01-04_at_5.00.14_PM.png)
    
- Builder UML
    
    Director can: 
    
    - define the order in which to execute the building steps, while the builder provides the implementation for those steps.(Guru)
    - = Client, kennt alle Schritte die nötig sind um Produkt aufzubauen + BEINHALTET DIE BUILDER (folien)
    
    ![Screen Shot 2022-02-24 at 4.46.38 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2022-02-24_at_4.46.38_PM.png)
    
    ![Screen Shot 2022-02-24 at 6.09.58 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2022-02-24_at_6.09.58_PM.png)
    
- Konsequenzen
    
    → denke Variationen (garage, ein zwei pools ... werden durch den Director umgesetzt.)
    
    - Abstracts construction implementation details
    – Allows varying internal representation of product
    • Encapsulates the way in which objects are constructed improving the
    modularity of a system.
    • Finer control over the creation process, by letting a builder class have
    multiple methods that are called in a sequence to create an object.

- Arten von Tests
    
    *developer* testing (bottom-up):
    – unit testing (≈ component testing)
    
    - testclass/ method /.. in isolation
    
    – integration testing
    
    - combination of 2+ units
    
    – system testing →final configuration,including external systems
    
    further tests:
    
    - regression testing
    - repetition of tests (to see if software still passes tests)
    – acceptance∼, performance∼, stress∼, platform∼, usability∼
- JUNIT Zeit-Performance Test
    
    **void** testLongRunning() {
    
    *assertTimeout*( Duration.*ofSeconds*(1), () -> *doSomething*() );
    
    }
    
- JUNIT nach Exceptions abfragen
    
    @Test
    
    **void** testValidation() {*assertThrows*( IllegalStateException.**class**, () -> *doSomethingElse*() );
    
    }
    
- Timeout
    
    @Timeout(value = 2, unit = TimeUnit.***SECONDS***)
    für eine Testmethode oder für alle Testmethoden innerhalb einer Klasse. 
    
- What is Jupiter (Testing)
    
    Assumptions is a collection of utility methods that support conditional test execution based on assumptions.
    
- Tests mehrfach ausführen + Info
    
    ![Screen Shot 2022-01-04 at 7.23.14 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2022-01-04_at_7.23.14_PM.png)
    
- Parametrisierte Tests
    
    ![Screen Shot 2022-01-04 at 7.36.08 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2022-01-04_at_7.36.08_PM.png)
    
- Explain Hamcrest
    
    Hamcrest is a framework that **assists writing software tests in the Java programming language**. It supports creating customized assertion matchers ('Hamcrest' is an anagram of 'matchers'), allowing match rules to be defined declaratively. These matchers have uses in unit testing frameworks such as JUnit and jMock.
    
- Hamcrest methoden
    
    ![Screen Shot 2022-01-04 at 8.01.41 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2022-01-04_at_8.01.41_PM.png)
    
    ![Screen Shot 2022-01-04 at 8.03.06 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2022-01-04_at_8.03.06_PM.png)
    
- Descriptive Assertions with Hamcrest - collections
    
    ![Screen Shot 2022-01-04 at 8.11.58 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2022-01-04_at_8.11.58_PM.png)
    
- d a w Hamcrest - numbers, text, logical
    
    ![Screen Shot 2022-01-04 at 8.13.37 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2022-01-04_at_8.13.37_PM.png)
    
- Diff between @Before and @BeforeClass
    
    The code marked `@Before` is executed before each test, while `@BeforeClass` runs once before the entire test fixture. If your test class has ten tests, `@Before` code will be executed ten times, but `@BeforeClass` will be executed only once.
    

- White box vs. Black box testing
    
    Black box testing Beispiel: GUI ernten drücken und schauen ob richtiger Score. 
    
    Experts generally consider path coverage testing to be a type of white box testing, which actually inspects the internal code of a program, rather just relying on external inputs and strategies that are considered black box testing, which do not consider internal code
    
- dff Unit Test vs. Integrationstest
    
    Unit = einzelne Einheit wird getestet → eine Klasse oder eine Methode
    
    Integration = mehrere Einheiten 
    
- Why use Mockito ?
    
    A unit test should only verify the part implemented **by the class itself**.
    
    - The outcome of tests should not be influenced by defects in other
        
        classes.
        
        Solution: replace objects of referenced classes with a **mock object**
        – An instance of a class implementing the expected interface.
        – The methods return pre-defined values. (Mockito)
        
- Types of Code Coverage (4)
    - **Statement:** Each statement is executed at least once.
    - **Branch:** Each branch is traversed (and every entry point is taken) at
    least once.  (*branch coverage measures the coverage of both conditional and unconditional branches.*)
    - **Condition:** Each condition (including sub logical evaluations like (a || b) is evaluated to **true** at least once and to **false** at least once (NOT ALL COMBINATIONS) (and every entry point taken).
    - **Path:** All program paths are traversed at least once. (includes EVERY FOR LOOP POSSIBILITY
- Decision Coverage ?
    - does not care about subexpressions
    - → only CONDITION COVERAGE does !!! (not covered in class)
- Branch Coverage vs Decision Coverage DIFF
    
    *Decision coverage measures the coverage of conditional branches; branch coverage measures the coverage of both conditional and unconditional branches.* 
    
- Example were decision coverage is not sufficient
    
    decision coverage reicht auch nicht aus → nur Condition coverage !!!
    
    - Bug tritt nur auf, wenn 1. Boolean Wert false ist.
    
    ![Screen Shot 2022-02-25 at 6.47.20 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2022-02-25_at_6.47.20_PM.png)
    
- Block Coverage
    
    Block: **defined as not having any branch point within.** 
    
    - Block coverage assumes that if a block of statements without
    branches is entered **and exited**, all statements in the block were
    executed.
        
        – That is, the counter is at the end of the block, instead of before
        the source code statement.
        
    - Result: If an exception occurs in the block, the **entire** block is not
    recorded as having executed.
- Nachteil Block Coverage
    - – This may be fine for application source code, but it does not work
    well with JUnit test source code or in **code for which exceptions
    are commonplace.**
    - – JUnit throws exceptions internally when tests fail, so the test may
    not have appeared to be executed.
    - – But: we mainly want to measure coverage of application code.
- Fault Seeding und Estimation
    
    1.Insert a set of faults into the code (z.B.• Save and seed faults identified during earlier project activities, random changing of numbers and +/- etc. )
    2. Run the current test set
    3. see if we found all faults with current testing suite
    						
    					
    
- Estimation Formula
    
    ![Screen Shot 2022-02-21 at 4.09.22 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2022-02-21_at_4.09.22_PM.png)
    
    ![Screen Shot 2022-02-21 at 4.10.07 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2022-02-21_at_4.10.07_PM.png)
    
- Teilmenge der Paths für Path-Coverage
    
    loop coverage: different ideas: one is: write test to execute loop body, zero, once, twice ... each. 
    
    basic paths coverage: test all decision outcomes independently of one another. Testing the  basic paths achieves this goal, making the other paths extraneous"
    
    dataflow coverage: selecting paths through the program's control flow in order to explore sequences of events related to the status of variables or data objects. Dataflow Testing focuses on the points at which variables receive values and the points at which these values are used.
    
- Welche Coverage Metrik sollten wir verwenden?
    
    → Statement ist leicht zu erreichen aber zu schwach.  (weil z.B. for loops nur ein einziges mal ausgeführt werden müssen) 
    
    → Path ist schwer zu erreichen (wenn Loops existieren unmöglich)
    
    → Branch Coverage ist ein guter Kompromiss. 
    

→ Refactoring Martin Fowler refactoring.com/catalog

- Extract Method - when to use + goals
    
    (teil-) Funktionalität einer Methode (die zu lang oder zu schwer verständlich geworden ist) in (Funktionalität gut beschreibende) eigene Methode auslagern und diese aufrufen. (
    
    When to use:
    
    - a method is too long
    - or it needs comments to be understandable
    
    Goals:
    
    - short, well-named methods should be preferred
    – increased chances that the code will be used by other
    methods
    – allows calls of higher-level methods` to be read more like a
    series of “comments”
    – overriding is easier with fine-grained methods (weil ich die Teilmethoden einzeln überschreiben (@Override) kann)
- wann kann man z.B. extract Method nicht anwenden ?
    
    → z.B. wenn der extrahierte Code-Abschnitt mehr als eine lokale Variable verändert und diese dann später wiederverwendet werden wollen. 
    
    → bei einer einzigen können wir hier den Rückgabewert der neuen Methoden verwenden aber bei mehreren nicht. (zumindest nicht einfach und Refactoring soll ja eher vereinfachen.)
    
- Was ist “feature envy” und wie fixen wir das?
    
    Bsp hier: 
    
    ![Screen Shot 2022-01-06 at 5.03.48 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2022-01-06_at_5.03.48_PM.png)
    
    Klasse Customer greift sehr oft auf Felder und Methoden der Klasse Rental zu. 
    
    - Custormer ist evtl. God Class.
    - + in Rental haben wir den “bad smell”, dass zusammengehörige Informationen und Operationen **nicht am selben Ort verwendet und verwaltet** werden.
    
    → Lösen wir damit, dass die Methode eher nach Rental gehört. 
    
- Wie Position einer Methode in der Klassenstruktur ändern?
    
    IDE > Refactor > Push-up / Pull-down
    
    → zieht die Methode in die Ober-Unterklasse.
    
- Gegenteil von Extract Method  + warum?
    
    → Inline Method 
    
    wenn die Methode nur in einem Kontext aufgerufen wird → hat den Vorteil, dass man die Methode dann nicht pflegen muss (sodass sie, wenn sie von woanders aufgerufen werden würde auch noch funktioniert).
    

- Was für Entwicklungswerkzeuge kennen Sie?
    - **Emma**: Measures Test Coverage:
    
    Supports class, method, “basic block”, and line coverage.
    
    - “Fractional”linecoveragesupported,but**not**branchcoverage.
    
    Uses byte code instrumentation.
    – Classes can be instrumented in advance, or during class loading
    
    - Profiling (JAVA VISUALVN . NTS, **JetBrains dotTrace)**
    – Get detailed performance data
    – Identify bottlenecks
    – Do not litter your code
    - Tools that check CODE STYLE (conventions)
- Anomalies with byte code instrumentation
    
    • There are cases where the compiler may emit multiple copies of object code
    for a single instance of source code.
    
- Handling exception → what happens? miss info?
- Wie performance optimieren  ?
    - ist auch aufwändig zu machen und macht den Code evtl. schwieriger zu verstehen.
    - fertig arbeiten, bottlenecks identifizieren und dann diese optimalisieren.
- Warum code conventions ?
    - easier to read and understand between developers
    - makes it easier to identifiy bug patterns with tools (tool: checkstyle)

- Debugger
    - define certain event → when occurs, stop execution.
    
     events
    – Stop in main
    – Line break points
    – Method breakpoints
    – Field watch points
    – Exceptionbreakpoints → stop when excpetion is thrown
    – Classloadingbreakpoints
    
    -Expresion Breakpoint → stop when condition becomes true or changes. 
    
     behavior
    – Suspend all threads
    – Suspendt hread with event (GUI läuft z:B. weiter, wenn exception in backend) 
    
    - hit count on breakpoint → stop only the n-th time breakpoint is reached
- Debugger ohne Breakpoint und Views
    
    Stepper: 
    
    Resume, Suspend, StepIntoMethod, StepReturn (continue til next return is executed) ) Drop Frame from Stack_Trace (fehler war früher als wo ich den breakpoint gesetzt habe) 
    
    - **Variables view** shows all the
    variables currently in scope.
        
        – Change values
        
    - **Expressions view** lets you
    evaluate expressions.
    - Tracepoint: Breakpont mit Bedingung → Macht nichts → bei Auswertung wird aber auf die Konsole geschrieben → kann z.B. reihenfolge der Auführung besser nachvollziehen.
- Profiler
    
    Performance Profiling
    
    - measure time for executing methods (includes called methods)
    
    Memory Profiling
    
    - measure usage of heap, how many instances of class are created, where are they created
- Style Check
    - Checkstyle:
        
        Checkstyle performs source code analysis.
        – Originally for "coding standards" (formatting)
        – Now includes design-level best practice compliances.
        
    - PMD :
    
    – More 'design’-oriented than Checkstyle.
    – Lots of overlap.
    
    - PMD rulesets:
    - – Empty try/catch/finally/switch blocks,
    - – Unused local variables, parameters
    and private methods,
    - – Empty if/while statements,
    - – Overcomplicated
    expressions
    - – Duplicate code
    

Metrics

- 3 kinds of complexity
    
    module complexity (i.e. cyclomatic complexity)
    structure complexity (fan in fan out)
    system complexity ( System Complexity = inter + intra model complexities)
    
- ****Module size as measure of complexity         ???**
    
    **There is an optimal module size.**
    
    Komplexität steigt nicht unbedingt immer mit dem Umfang, denn: 
    
    Interfacekomplexität: Existenz von Modul bringt schonmal bestimmte Komplexäität → Dadurch kann schonmal ein Fehler existieren, nur weil es da ist. → Konstante BasisKomplexität  - die nimmt erstmal mit steigender Größe des Moduls ab. 
    ****As size increases, impact of interface complexity decreases
    
- Cyclomatic Complexitiy
    
    Should be under 10 for a Method. 
    
    → criticism: ignores diff - kann auch unter 10 unverständliche Progarmme schreiben. 
    
    ![Screen Shot 2022-02-21 at 6.59.53 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2022-02-21_at_6.59.53_PM.png)
    
    unabh: verschiedene Möglichkeiten den Graph zu durchlaufen
    
    Repräsentatnten 
    
    ![Screen Shot 2022-02-21 at 7.05.26 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2022-02-21_at_7.05.26_PM.png)
    
- What does Code-Complexity measure ?
    - expected defect rate.
    - testability
    - + manchmal sagt es uns wie viele Tests wir schreiben müssen
        
        z.B. decision coverage → gibt mir minimale anzahl von tests 
        
        lines of code hängt mit statement coverage zusammen (schwieriger zu wissen wie viele methoden) 
        
    
    ![Screen Shot 2022-02-21 at 7.41.36 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2022-02-21_at_7.41.36_PM.png)
    
- Verbesserung von Cyclomatic Comp. ?
    
    diff. weights for kinds
    
    ![Screen Shot 2022-02-21 at 7.48.33 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2022-02-21_at_7.48.33_PM.png)
    
- Structure Metrics
    - Most commonly used: coupling between modules in terms of
        - fan-in: # of modules calling a given module
        - fan-out: # of modules called by a given module
- Fan in (what is it’s significance?)
    
    Large fan-in:
    
    - (Typically) **small/simple modules**
    - Usually located at the **lowest levels** of the system structure
    - Expected to have **low defect levels**
    - **Fan-in is expected to have negative or insignificant correlation with
    defects**
    
    Small fan-in
    
    - (Typically) large/complex modules
    - **Fan-in has been found not to be a good indicator of
    complexity**.
- Fan out  + what should not be the case ?
    
    Large fan-out:
    
    Modules expected to have higher defect levels
    
    - Fan-out is expected to have positive correlation with
    defects.
    - Modules should generally**not have both high fan-in and
    high fan-out**
        
        **because i might pass imported defects on**
        
- System complexity model
    
    System complexity = Structure complexity + Data Complexity 
    
    - Structure: inter-module (außreiser nach oben werden bestraft → muss für gleichmäßige Verteilung sorgen)
    - Data: intra-module (vergleiche Anzahl von I/O variablen mit der Anzahl der Module von denen ich abhänge) → wenn ich eine Verhältnis grßer 1 habe, habe ich mehr solche variablen als Module, also habe ich mind. ein Modul von dem ich mehere Objekte benutze. → ist dann eine hohe Datenkomplexität
    - System-Kompl. ist Summe von beidem oben.
    
    ![Screen Shot 2022-02-21 at 8.06.42 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2022-02-21_at_8.06.42_PM.png)
    
- Fault location prediction
    - Modules Most frequently fixed (MFF)
    - Modules local to those above  - most locally fixed (MLF)

**Chidamber and Kemerer (CK) Metrics Suite**

- **CK Metrics Suite: Coupling Between Object Classes**
    - wir interessieren uns für Objekte und Klassen sind Schablonen für Objekte.
    
    ![Screen Shot 2022-02-21 at 10.15.58 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2022-02-21_at_10.15.58_PM.png)
    
- Lack of Cohesion
    
    ![Screen Shot 2022-02-21 at 10.21.53 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2022-02-21_at_10.21.53_PM.png)
    
    - Build all possible **method pairs**For each pair determine **commonly accessed fields**
    
    – **Empty set**: methods are **dissimilar**
    
    – **Non-empty set**: methods are **similar**
    • P := number of dissimilar method pairs
    • Q := number of similar method pairs
    • LCOM := surplus of dissimilar method pairs
    
    – if P > Q: LCOM: = P – Q
    – otherwise: LCOM := 0
    
    → KRITIK: zu simpel → kein unterschied z:B bei länge der methode oder anzal der gemeinsamen felder. 
    
- Coupling & Cohesion to achieve modularity
    
    ![Screen Shot 2022-02-21 at 10.32.30 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2022-02-21_at_10.32.30_PM.png)
    
- More detailed Models of cohesion & Coupling
    
    **More detailed model of cohesion**
    
    –  Logical cohesion
    • Elementsofclassperformonekindofalogicalfunction
    
    – Temporal cohesion
    • Elementsofaclassareexecuted"together"
    
    **More detailed model of coupling**
    
    – Weigh kind of relationship (use, inheritance, containment,
    association)
    
- **Weighted Methods per Class**
    - Sum complexity for all methods (maybe use Cyclomatic Complexiy)
    
    → maybe Weighted based on length of method. 
    
    - Often just use constant 1 as complexity
    – Then equivalent to number of method
    - Large value:
    – Indicates application-specific class
    – Limited possibility of reuse
- **Depth of Inheritance Tree**
    
    Length of maximum path from root to this class
    – When using multiple inheritance take maximum of all possible paths
    
    Measure of how many ancestor classes affect this class
    
    - Large value:
    – Great number of inherited methods
    – Great effort to predict behavior
    – Many methods and classes taken into consideration
    – Potentially reuse more inherited methods
- **Number of Children**
    
    Vererbung nicht nur für Code-Wiederverwendung, sondern “ist-ein”-Beziehung richtig anwenden. 
    
    • Number of immediate successors (heirs) of this class
    • ... going to inherit methods of parent class
    
    Large value:
    
    – Requires more testing (more potential polymorphism)
    – Much (code) reuse
    – May mean a case of misuse of subclassing for code inheritance
    
    - High probability of improper abstraction of parent class
    - Design principle:
        
        – Do not inherit to reuse implementation
        
        – Only inherit to extend the type (is-a relationship)
        – Potentially big influence on design
        
- **Response level**
    
    ![Screen Shot 2022-02-22 at 2.17.21 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2022-02-22_at_2.17.21_PM.png)
    

- **Code Smells: Duplicate code** (3 ways to fix)
    
    ![Screen Shot 2022-02-22 at 3.00.43 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2022-02-22_at_3.00.43_PM.png)
    
- **Code Smells: Long parameter list** (why bad + 1 way to fix)
    - Method call statements are long
    • When calling method with same/similar arguments
    
    – Just **pass through** own arguments
    • Long parameter lists likely to change
    
    – **Complicates maintenance (example. when changing/adding parameter, likely have to change all instances method is called)** 
    • Refactoring:  Introduce parameter object
    
    - **Code Smells: Message chain / Feature envy**
        
        ![Screen Shot 2022-02-22 at 3.11.33 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2022-02-22_at_3.11.33_PM.png)
        

- Fragile Base Class
    
    the base class is the class you are inheriting from, and it is often called fragile because changes to this class can have unexpected results in the classes that inherit from it.
    
    → Änderung sieht in oberklasse lokal legal aus, aber in unterklasse entstehen probleme.
    
    The fragile base class problem is a fundamental architectural problem of object-oriented programming systems where base classes are considered "fragile" because seemingly safe modifications to a base class, when inherited by the derived classes, may cause the derived classes to malfunction.
    
- MVC Pattern
    
    Use **to segregate the views from the model and controllers**. It helps in separating the display and the data and allow modification in each data without affecting the others. It is mostly used for developing Graphical User Interface.
    
    View: GUI Bibliothek
    Model → View keine Abhängigkeit nur Kontrollfluss. 
    
    ![Screen Shot 2022-02-22 at 6.11.59 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2022-02-22_at_6.11.59_PM.png)
    
- LSP
    
    **→ wenn nicht eingehalten, schreiben wir evtl. Code der schwieriger zu verstehen ist. Problem tritt meist auf, wenn wir Vererben um Code wiederzuverwenden.**
    
    Liskov's notion of a behavioural subtype defines a notion of substitutability for objects; that is, if *S* is a subtype of *T* , then objects of type *T* in a program may be replaced with objects of type *S* without altering any of the desirable properties of that program (e.g. [correctnes](https://en.wikipedia.org/wiki/Correctness_(computer_science))).
    
    → Unterklasse darf etwas weniger machen oder etwas konkreteres. Aber sie darf nicht mehr machen. (könnte man evl. also umdrehen, Square vererbt nach Rectangle) 
    
    Example: 
    
    ![Screen Shot 2022-02-22 at 6.26.03 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2022-02-22_at_6.26.03_PM.png)
    
    ![Screen Shot 2022-02-22 at 6.30.43 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2022-02-22_at_6.30.43_PM.png)
    
- Was beduetet das LSP für Tests?
    
    Klassen/Methoden müssen so designt sein, dass: 
    
    Wenn ein Test korrekt ist bei verwendung der Superklasse, muss er auch korrekt sein wenn stattdessen ein Unterklassenobjekt verwendet wird. 
    
- Möglichkeit das Problem im bsp. oben zu lösen
    
    ![Screen Shot 2022-02-22 at 6.36.21 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2022-02-22_at_6.36.21_PM.png)
    
- Aspect Oriented Programming
    
    ![Screen Shot 2022-02-22 at 7.27.52 PM.png](Software%20Design%20c2ab5875c38941a3a1b6df1bcdc1e2a7/Screen_Shot_2022-02-22_at_7.27.52_PM.png)
    

~~TOD:~~ 

- ~~exam: pro/con considerations of design patterns (why use this not that similar pattern?) in actual project. Parallelen zwischen ähnlichen Patterns diskutieren können.~~
- ~~super keyword usage~~

- ~~Warum ist if else nicht .... ?~~
    
    Ist nicht objektorientiert sondern imperativ. If else von der Anwendbarkeit von Strategy Pattern.
    
    - UML
    
    ![https://upload.wikimedia.org/wikipedia/commons/thumb/9/93/Uml_classes_en.svg/300px-Uml_classes_en.svg.png](https://upload.wikimedia.org/wikipedia/commons/thumb/9/93/Uml_classes_en.svg/300px-Uml_classes_en.svg.png)
    
    - Durchgezogener Pfeil A→B  Assoziation (A kennt B; kann Operationen darauf ausführen) = "entspricht in der Implementierung einem **Feld**."
    - Gestrichelter Pfeil - - → Assoziation durch Erzeugung.
    - Aggregation vs Composition: Agg kann einzeln oder als Aggregat existieren: Composition kann nur als Teil des Ganzen existieren.
    - Aggregation vs. Associacion: **Aggregation describes a special type of an association which specifies a whole and part relationship.** **Association is a relationship between two classes where one class uses another**.
    
    [UML Association vs Aggregation vs Composition](https://www.visual-paradigm.com/guide/uml-unified-modeling-language/uml-aggregation-vs-composition/)
    
- **when to use dependency, aggregation and association**
    
    **Dependency** is the most abstract among all 
    relationships. Between 2 classes it only means that one is somehow 
    "aware" ot another. Example: An object of a class A receives a reference
     to an object of the class B (during some method execution) and do 
    something with it (like calling its method). 
    **Usage** is a special type of dependency and means that class A uses class B.
    
    **Association** is somehow stronger relationship than 
    dependency. Example: A class a has a member (attribute) of class B and 
    permanently holds this reference. The difference from the previous 
    example is that this link is long-term, versus short-term link expressed
     through dependency.
    
    **Agregation** and **compositions** are 
    also associations, but stronger ones. Their semantics depends on the 
    implementation language or context. 
    Agregation is a non-exclusive relationship of the type Group-Member 
    (several Members belog to the same group and can also belong to other 
    groups). When Group is destroyd - Members are just unasigned from it and
     not destroyd.
    Composition is exclusive and very strong relationship: Whole-part. Part 
    is under total control of Whole - is practically part of it. Without the
     Whole, the Part does not exist, so when the whole is destroyed, the 
    Part will die as well.
    
- Scrum
    
    Meeting → Sprint → Meeting
    
    development cycle: {
    
    planning, 
    
    requirements analysis, 
    
    design, 
    
    coding, 
    
    unit testing
    
    }
    
    → acceptance testing when a working product is demonstrated to stakeholders.
