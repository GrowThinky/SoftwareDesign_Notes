# ∆ndroid

[https://towardsdatascience.com/top-10-libraries-every-java-developer-should-know-37dd136dff54](https://towardsdatascience.com/top-10-libraries-every-java-developer-should-know-37dd136dff54)

- How to fix “nonsenical errors” Problem in IDE after import new Project?
    
    file > invalidate caches and restart
    
    - + rebuild project
- where to add launch configurations in intelliJ ?
    
    → these are options and arguments added to the main method’s args (as in main(string[] args)
    
    Go to: 
    
    run > Debug Configuration   
    
    → VM args need to be selected seperately
    
- where are the artifacts managed by maven stored?
    
    `.m2` folder is the default folder used by maven to store its:
    
    - `settings.xml` file which specifies properties, like the central repository to download your dependencies, the location of the so-called `localRepository`
    - by default, the `localRepository` in which maven stores all the dependencies your project might need to run.
- ***JUnit Jupiter***
    
    **Unit Jupiter**
     is the combination of the new [programming model](https://junit.org/junit5/docs/current/user-guide/#writing-tests)
     and [extension model](https://junit.org/junit5/docs/current/user-guide/#extensions)
     for writing tests and extensions in JUnit 5. The Jupiter sub-project provides a `TestEngine`
     for running Jupiter based tests on the platform.
    
- IRC
    
    > `Internet Relay Chat (IRC) is a protocol for live interactive Internet text messaging (chat) or synchronous conferencing. It is mainly designed for group communication in discussion forums, called channels, but also allows one-to-one communication via private message as well as chat and data transfer, including file sharing.`
    > 
    
    [Every Programmer should use IRC](https://www.fizerkhan.com/blog/posts/every-programmer-should-use-irc)
    
- PMD
    
    Simply put, PMD is **a source code analyzer to find common programming flaws like unused variables, empty catch blocks, unnecessary object creation, and so forth**. It supports Java, JavaScript, Salesforce.com Apex, PLSQL, Apache Velocity, XML, XSL.
    

- git - merge branch into master
    
    If you want to merge your branch to master on remote, follow the below steps:
    
    1. push your branch say 'br-1' to remote using `git push origin br-1`.
    2. switch to master branch on your local repository using `git checkout master`.
    3. update local master with remote master using `git pull origin master`.
    4. merge br-1 into local master using `git merge br-1`. This may give you conflicts which need to be resolved and changes committed before moving further.
    5. Once merge of br-1 to master on local is committed, push local master to remote master using `git push origin master`.
- git - add file to commit after git commit
    
    ```
    # edited file-that-i-remember.txt
    git add file-that-i-remember.txt
    git commit
    
    # realize you forgot a file
    git add file-that-i-forgot.txt
    git commit --amend --no-edit
    ```
    
- git push
- git - revert changes to last commit
    
    This will undo any changes you've made to tracked files and restore deleted files:
    
    `git reset HEAD --hard`   (head am Ende?)
    
- Taenzer Tipp - how to merge changes
    
    create new local branch
    merge remote master into new local - see if worked
    if so - merge that back into remote master
    

git clone (beim ersten Mal)

git checkout -b branchName //neuer lokaler branch 

// make changes 

git add —all 

git commit -m “message” 

git push origin branchName  

Android

- Check if App has been restored
    
    if(savedInstanceStace == null)  → nicht restored
    
    else → fields need to be reinitialized !!! 
    
    savedInstanceState.getDouble(ValueName)
    
- Save Data for restore
    
    onSaveInstanceState(Bundle outState) 
    
    ![Screen Shot 2022-04-02 at 9.55.50 PM.png](%E2%88%86ndroid%205b37d5be72d142308f63e2e1bf21d81f/Screen_Shot_2022-04-02_at_9.55.50_PM.png)
    
- R Class
    
    `R.java`
     is the dynamically generated class, created during build process to dynamically identify all assets (from strings to android widgets to layouts), for usage in java classes in Android app. Note this `R.java`
     is Android specific (though you may be able to duplicate it for other platforms, its very convenient), so it doesn't have much to do with Java language constructs. Take a look [here](http://knowledgefolders.com/akc/display?url=displaynoteimpurl&ownerUserId=satya&reportId=2883), for more details.
    
- Gradle (What is ?)
    
    ### Short Answer
    
    Gradle is a build system.
    
    ### Long Answer
    
    You can build your Android APK on the command line, but you have to learn what each tool ([dx](https://stackoverflow.com/tags/dx/info) and [AAPT](https://developer.android.com/studio/command-line/aapt2)) does in the SDK. Eclipse saved us all from these low-level, but important, fundamental details by giving us their own build system.
    
    Now, have you ever wondered why the `res` folder is in the same directory as your `src` folder?
    
    This is where the build system enters the picture. The build system automatically takes all the source files (`.java` or `.xml`), then applies the appropriate tool (e.g., takes `.java` class files and converts them to `.dex` files), and groups all of them into one compressed file - our beloved APK.
    
    This build system uses some conventions: an example of one is to specify the directory containing the source files (in Eclipse it is `\src` folder) or resources files (in Eclipse it is `\res` folder).
    
    Now, in order to automate all these tasks, there has to be a script; you can write your own build system using shell scripting in Linux or batch files syntax in Windows. Got it?
    
    Gradle is another **build system** that takes the best features from other build systems and combines them into one. It is improved based off of their shortcomings. It is a **JVM-based build system**. That means you can write your own script in Java, which Android Studio makes use of.
    
    One cool thing about Gradle is that it is a **plugin-based system**. This means if you have your own programming language and you want to automate the task of building some package (output like a [JAR](https://en.wikipedia.org/wiki/JAR_%28file_format%29) file for Java) from sources, then you can write a complete plugin in Java or [Groovy](https://en.wikipedia.org/wiki/Groovy_%28programming_language%29) (or [Kotlin](https://en.wikipedia.org/wiki/Kotlin_(programming_language)), see [here](https://blog.gradle.org/kotlin-meets-gradle)), and distribute it to the rest of the world.
    
    ### Why did Google use it?
    
    Google saw one of the most advanced build systems on the market and realized that you could write scripts of your own with little-to-no learning curve, and without learning Groovy or any other new language. So they wrote the Android plugin for Gradle.
    
    You must have seen `build.gradle` file(s) in your project. That is where you can write scripts to automate your tasks. The code you saw in these files is Groovy code. If you write `System.out.println("Hello Gradle!");` then it will print on your console.
    
    ### What can you do in a build script?
    
    A simple example is that you have to copy some files from one directory to another before the actual build process happens. A Gradle build script can do this.
    
- Features to use
    
    TODO pane  (//TODO:)
    

- Swipeable Views
    
    ViewPager: 
    Create multiple Fragments and swipe left/right. 
    ViewPager2
    ViewPagerAdapter extends FragmentStateAdapter
    ViewPager.setAdapter()
    number of Fragments
    SWITCH statement for changing between them. 
    
- getActivity()
    
    • `getActivity()` in a `Fragment` returns the `Activity` the `Fragment` is currently associated with. (see [http://developer.android.com/reference/android/app/Fragment.html#getActivity()](http://developer.android.com/reference/android/app/Fragment.html#getActivity%28%29)).
    
- onCreate() vs onCreateView() in Fragment
    
    **onCreate** is called on initial creation of the fragment. You do your non graphical initializations here. It finishes even before the layout is inflated and the fragment is visible.
    
    **onCreateView** is called to inflate the layout of the fragment i.e graphical initialization usually takes place here. It is always called some time after the **onCreate** method.
    
- ViewBinder
    
    Each binding class contains references to the root view and all views that have an ID.
    
    The name of the binding class is generated by converting the name of the XML file to camel case and adding the word "Binding" to the end.
    
- RootView
    
    RootView is the View in which all the other views are placed. It is like the root node in a tree structure which is the parent to all the children.
    
    For example, you have multiple Buttons in your layout which are placed inside a LinearLayout. Then LinearLayout is called the RootView as it would have the highest position in the structure and everything would have to be placed inside it.
    
- AndroidManifest.xml
    
    All activities must be represented by `<activity>`
    elements in the manifest file. Any that are not declared there will not be seen by the system and will never be run.
    
- Navigate Between Activities / Fragments
    
    add gradle dependecies 
    
    **Add a NavHostFragment via XML  (is a Fragment)**
    
    **Add source fragments/activities with nested actions with destinations to the navigation graph  
    →**  NavGraph <action>
    
- activity.xml  vs  content.xml
    
    According to new design pattern in android studio `activity_main.xml` will determine how the global UI of the Activity should be. And on the other hand `content_main.xml` will determine the contents (displayed to the user)  in the `activity_main.xml`.
    
    That is `content_main.xml` will contain the textview, edittext, button etc component. And it will be included by the `activity_main.xml`. 
    
    → like this: `<include layout="@layout/content_main" />`
    
- Set beginning Destination ?
    
    app:startDestination =       (in nav.graph.xml) 
    
- View Parameter in onClick(View v) ?
    
    OnClick method, the View parameter is in your case the Button instance that has fired the method - multiple Buttons can have the same OnClick handler, inside the method you can check which of the Buttons has fired (if there are more than one) and react accordingly.
    
- Connect layout (xml) to Activity
    
    in onCreate: 
    
    `setContentView(binding.getRoot());`  if ViewBinding is used. 
    
- Add Fragment to Activity
    
    Activitxie’s xml → <fragment>  
    
    (possibly as NavHostFragment to swich between multtiple Fragments) 
    
    with setContentView() in Activietie’s onCreate this layout is set 
    
- ActionBar vs Toolbar
    
    Action bar → present by default / contains Name / options menue 
    Toolbar can be set as Actionbar
    
    new Toolbar  ***is a generalization of the Action Bar pattern that gives you much more control and flexibility.***
    ***Toolbar is a view in your hierarchy just like any other, making it easier to interleave with the rest of your views***, animate it, and react to scroll events. You can also set it as your Activity’s action bar, meaning that your standard options menu actions will be display within it.
    
- Remove Default Action Bar  - add Toolbar
    
    Themes.xml <style>  .... .NoActionBar
    Remove all references in java (like onCreate) to action bar
    
    See Tutorial for Add Toolbar in Clipboard. 
    needs own xml file for toolbar 
    
    make Activity extend AppCompatActivity 
    setSupportActionBar()
    
- Default ActionBar
    
    shows Title → Label in Manifest 
    
    change name for each activity in manifest <activity> label=
    
- Visual ActionBar Icon
    
    in activitie’s onCreate: 
    
    ```
    getSupportActionBar().setDisplayShowHomeEnabled(true);
    getSupportActionBar().setIcon(R.drawable.ic_launcher_foreground);
    
    alt: 
    add:
    app:navigationIcon="@drawable/ic_action_navigation_menu">
    to the <android.support.v7.widget.Toolbar tag
    ```
    
- Clickable ActionBar Icon
    
    If you're looking for a clickable icon, you need to use `.setHomeAsUpIndicator`
     and handle it in your `onOptionsItemSelected`.
    
- AppCompat
    
    if used  use getSupportActionBar() vs get ActionBar 
    
- Add Menu to ActionBar / ToolBar
    
    r click on res > create xml file > choose type menu
    
    override onCreateOptionsMenue in Activity 
    
    getMenuInflater().inflate(xml file)
    
     onMenuItemClick() 
    
- **Add Action Button**
    
    action_button.xml with menu item in res > menu
    
    in Activity: onCreateOptionsMenu 
    
    `inflater.inflate(R.menu*action_button*, menu);`
    
- ActionBar Icon
    
    `actionbar.setIcon(R.drawable.*ic_launcher_foreground*);`
    
- Create new Icon
    
    res > new > vector asset  
    
- onCreate vs onCreateView
    
    Activity has no onCreateView ? !!!
    
- onCreateOptionsMenu
    
    You use onCreateOptionsMenu() to specify the options menu for an activity. In this method, you can inflate your menu resource (defined in XML) into the Menu provided in the callback.
    
- OptionsMenu
    
    The options menu is where you should include actions and other options that are relevant to the current activity context, such as "Search," "Compose email," and "Settings.” If you've developed your application for **Android 3.0 (API level 11) and higher**, items from the options menu are available in the app bar. By default, the system
    places all items in the action overflow, which the user can reveal with the action overflow icon on the right side of the app bar (or by pressing the device *Menu* button, if available). To enable quick access to important actions, you can promote a few items to appear in the app bar by adding`android:showAsAction="ifRoom"` to the corresponding `<item>`elements (see figure2).
    
- Context menu and contextual action mode
    
    A context menu is a [floating menu](https://developer.android.com/guide/topics/ui/menus#FloatingContextMenu) that appears when the
    user performs a long-click on an element. It provides actions that affect the selected content or context frame.
    
- set up SearchView in OptionsMenu
    
    ```
    public boolean onCreateOptionsMenu(Menumenu) {
    MenuInflaterinflater = getMenuInflater();
        inflater.inflate(R.menu.search_view, menu);
        finalMenuItemsearchItem = menu.findItem(R.id.app_bar_search);
        finalSearchViewsearchView=(SearchView) searchItem.getActionView();
        searchView.setOnQueryTextListener(this);
    		return super.onCreateOptionsMenu(menu);
    }
    ```
    
- set up the RecyclerView
    
    implement own Adapter class: 
    
    ```java
    public class **RecyclerViewAdapter** extends **RecyclerView**.**Adapter**<**RecyclerViewAdapter**.**ViewHolder**>
    
    In Activity: (below)
    ```
    
    ```java
    recyclerView = findViewById(R.id.re
    recyclerView.setLayoutManager(new L
    adapter = new RecyclerViewAdapter(t
    adapter.setClickListener(this);
    recyclerView.setAdapter(adapter);
    ```
    
- What does ViewHolder do ?
    
    in its constructor, the binding of View (like TextViet etc.) with Layout elements happens. 
    
    ```java
     onBindViewholder(ViewHolder holder, int position) 
    ```
    
    in Adapter is where pos of list Items and Bindings in holder are connected
    
- set up  RecyclerviewAdapter and ViewHolder
    
    in RecyclerViewAdapter: 
    → we set the content for TextView etc. in onBindViewHolder Method in Adapter !!!
    
    ```java
    // binds the data to the TextView in each row
    @Override
    public void onBindViewHolder(ViewHolder holder, int position) {
    Modul modul = mData.get(position);
        holder.nameTextView.setText(modul.name);
       ;
    }
    ```
    
    ```java
    // inflates the row layout from xml when needed
    @Override
    public ViewHolder onCreateViewHolder(ViewGroupparent, int viewType) {
    View view = mInflater.inflate(R.layout.recyclerview_row, parent, false);
    return new ViewHolder(view);
    }
    
    // stores and recycles views as they are scrolled off screen
        public class ViewHolder extends RecyclerView.ViewHolder implements View.OnClickListener {
            TextView nameTextView;
            TextView timeTextView;
    
            ViewHolder(View itemView) {
                super(itemView);
                nameTextView = itemView.findViewById(R.id.modul_name);
                timeTextView = itemView.findViewById(R.id.modul_time);
                itemView.setOnClickListener(this);
            }
    
            @Override
            public void onClick(View view) {
                if (mClickListener != null) mClickListener.onItemClick(view, getAdapterPosition());
            }
        }
    
        // convenience method for getting data at click position
        Modul getItem(int id) {
            return mData.get(id);
        }
    
        // allows clicks events to be caught
        void setClickListener(ItemClickListener itemClickListener) {
            this.mClickListener = itemClickListener;
        }
    
        // parent activity will implement this method to respond to click events
        public interface ItemClickListener {
            void onItemClick(View view, int position);
        }
    
        @Override
        public void onBindViewHolder(@NonNull ViewHolder holder, int position, @NonNull List<Object> payloads) {
            super.onBindViewHolder(holder, position, payloads);
    
        }
    ```
    
- ViewModel
    
    • The [ViewModel](https://developer.android.com/reference/android/arch/lifecycle/ViewModel.html) class is designed to hold and manage UI-related data in a life-cycle conscious way. This allows data to survive configuration changes such as screen rotations.
    
- Application for Data
    
    see stackoverflow article 
    
- Search Bar in Actionbar
    
    res > create new menu item xml
    add searchitem from palette
    actionViewClass: `androidx.appcompat.widget.SearchView`
    add lines to onCreateOptionsMenu (same as actionbutton)
    +
    
    ```
        final MenuItem searchItem = menu.findItem(R.id.<idOfMenuItem>);
        final SearchView searchView = (SearchView) searchItem.getActionView();
        searchView.setOnQueryTextListener(this);
    ```
    
    Activity implements OnQuerryTextListener
    
- Action View
    
    An *action view* is an action that provides rich functionality within the app bar. For example, a search action view allows the user to type their search text in the app bar, without having to change activities or fragments.
    
- Assets vs Storage
    
    Also, a quick reminder: assets are read-only at runtime. Use [internal storage](https://commonsware.com/blog/2014/04/07/storage-situation-internal-storage.html), [external storage](https://commonsware.com/blog/2014/04/08/storage-situation-external-storage.html), or [the Storage Access Framework](http://developer.android.com/guide/topics/providers/document-provider.html) for read/write content
    
- get file from Assets
    
    **`AssetManager** assetManager = getAssets();`
    
    `inputStream =  assetManager.open("data.xls");`
    
- Context
    
    As the name suggests, it's the context of the current state of the application/object. It lets newly-created objects understand what has been going on. Typically you call it to get information regarding another part of your program (activity and package/application).
    
    You can get the context by invoking `getApplicationContext()`, `getContext()`, `getBaseContext()` or `this` (when in a class that extends from `Context`, such as the Application, Activity, Service and IntentService classes).
    
- Read files
    - xls:
    
    `implementation "org.apache.poi:poi:3.17"`
    
    `Workbook workbook = new HSSFWorkbook(inputStream);`
    
    - Jsoup HTML Parser:
    
    **`Document** doc =` **`Jsoup.***parse*(inputStream, "UTF-8", "http://example.com/");`
    

ReadCode: 

ReadErrors: O

Knxwledge: O

- General Android Dev Concept
    
    add xml for Context and View Elements (Activity, Fragment, TextView etc. ) 
    
    inflate xml in relevant activity/fragment
    
    manipulate properties with java
    
- Gradle Dependency Basics
    
    [Managing Dependencies of JVM Projects](https://docs.gradle.org/current/userguide/dependency_management_for_java_projects.html)
    

- Key Shortcuts:
    
    
    | cmd + left/right | mov cursor  |
    | --- | --- |
    | cont + left/right | swipe screens |
    | shift + opt + down | highlight curr. line |
- Dates
    
    Woche 1 - 2 (Abgabe bis 29.4.)
    
    - *Installation + Einarbeitung in Android*
    
    Abnahme: nur in Übungen von Tutoren
    
    Donnerstag 5.5. Vorlesungszeit (12-14): Zusätzliche Sprechstunde zur App-Anforderungen (Hörsaal B)
    
    Woche 3 – 6 (Abgabe bis 22.5.)• *1. Ausbaustufe des Projekts (Milestone 1)*
    
    Abnahme: Donnerstag 2.6. mit Prof. Flek in der Vorlesungzeit (12-14, ggf. auch 14-16) oder in der Übungszeit in der Woche (außer Dienstag)
    
    Woche 7 – 9 (Abgabe bis 17.6.)• *2. Ausbaustufe (Milestone 2)*
    
    Abnahme: Donnerstag 23.6. mit Prof. Flek in der Vorlesungzeit (12-14, ggf. auch 14-16) oder in der Übungszeit in der Woche (außer Dienstag)
    
    Woche 10 – 12 (Abgabe bis 8.7.)• *3. Ausbaustufe (Milestone 3)*
    
    Abnahme: Donnerstag 21.7. mit Prof. Flek in der Vorlesungzeit (12-14 ggf. auch 14-16) oder in der Übungszeit in der Woche (außer Dienstag)
    
    Woche 13 – 15 (Abgabe bis 29.7.)
    
    - *Abrundung des Projekts*
    - Abschlusspräsentation der Ergebnisse und Rücksprachen
    
    Abnahme: Donnerstag 4.8. mit Prof. Flek in der Vorlesungzeit (12-14) oder in der Übungszeit in die Woche
    
- Info
    
    RecyclerView mit Adapter für die Darstellung mit SearchView zum Suchen
    
    Dafür spricht, dass suchergebnisse  bei RecyclerView super einfach mit recyclerView.swapAdapter() geupdatet werden können. ListView wäre auch eine option würde aber eher davon abraten, weil die Performance schlechter ist und allg. weniger  flexibel. 
    
    xls File mithilfe der Tags <Row> und <Cell> parsen. Der Tutor hat mir dafür JSoup empfohlen: 
    
    ```
    Document doc = null;
    try {
        doc =Jsoup.parse(inputStream, "UTF-8", "http://example.com/");
    } catch (IOExceptione) {
        e.printStackTrace();
    }
    
    Elements rows = doc.getElementsByTag("Row");
    → so kann man auf jede Zeile der Tabelle einzeln zugreifen. 
    ```
    
    Duplikate zusammenfassen (nach Superschlüssel z.B. Ver.nr ) 
    
    Datenklasse “Modul” mit allen (wichtigen?) Informationen zu den Modulen. 
    
    Einfache ArrayList zum Speichern aller Modul Instanzen. Es gäbe auch komplizierere Datenstrukturen z.B. im Guave Paket von Google, aber die einfache Lösung wird für diese Datenmenge auch schon ausreichen, glaube ich. 
    

android_∫:

- UML
    - RecyclerView UML (Analysemodell ? - check doc)
        - Shared Preferences for local user data
        - SQL for seperate storage (later on; we would need server)
    - obvious parts (like Activity etc.)
    - partial views UML - ok ?
    - Joda Time for von, bis Felder ?
- Patterns (see article: [https://www.raywenderlich.com/18409174-common-design-patterns-and-app-architectures-for-android](https://www.raywenderlich.com/18409174-common-design-patterns-and-app-architectures-for-android))
    - Builder
    - Singleton
    - Factory
    - Adapter (recylcerView)
    - MVC
    - Observer
    - Command
- persist user data (Application Object ? )
    - internal sql database
    - Shared Preferences
    
    FoPra Technologies: (find out what will be used to start learning soon!!!) 
    
    - Java GUI: SWT/JFace
    - ionic Framework
    
    - RecyclerView
        
        [Simple Android RecyclerView example](https://stackoverflow.com/questions/40584424/simple-android-recyclerview-example)
        
    - SearchView vs. RecyclerView
        
        SearchView provides Search Input Field 
        
        Recyclerview / ListView displays the results 
        
    
    - method stops execution after throw statement
    - Diff. Interface vs Abstract Class
        
        I**nterface:**
        
        Every single Method declared in an Interface will have to be implemented in the subclass. Only Events, Delegates, Properties (C#) and Methods can exist in a Interface. A class can implement multiple Interfaces.
        
        **Abstract Class:**
        
        Only Abstract methods have to be implemented by the subclass. An Abstract class can have normal methods with implementations. Abstract class can also have class variables beside Events, Delegates, Properties and Methods. A class can only implement one abstract class only due non-existence of Multi-inheritance in C#.
        
        Abstract Class abstrahiert konkrete Ausprägungen (Abstract:pilot, heliPilot,planePilot etc.). Ein Interface stellt eine Menge an abstrakten Methoden zur Verfügung, die von verschiedenartige Klassen implementiert werden können (Zusatzausbildung Safety Officer). 
        
        *I went to pilot training and became a USAF (US Air Force) pilot. At that point I wasn't qualified to fly anything, and had to attend aircraft type training. Once I qualified, I was a pilot (Abstract class) and a C-141 pilot (concrete class). At one of my assignments, I was given an additional duty: Safety Officer. Now I was still a pilot and a C-141 pilot, but I also performed Safety Officer duties (I implemented ISafetyOfficer, so to speak). A pilot wasn't required to be a safety officer, other people could have done it as well.*
        
    - == vs equals()  !!!
        
        `==` compares object references, it checks to see if the two operands point to the same object (not *equivalent* objects, the **same** object).
        
    - Diff. Methode überladen vs. Methode überschreiben