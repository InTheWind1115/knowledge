1、如何在活动中使用Menu?    P49
    首先在res目录下面新建一个menu文件夹
    new->Menu resource->"main"
    在main.xml中添加一下代码：
    {
        <menu xmlns:android="http://schemas.android.com/apk/res/android">
        <item
        android:id="@+id/add_item"
        android:title="Add"/>
        <item
        android:id="@+id/remove_item"
        android:title="Remove"/>
        </menu>
    }
    重写活动中的onCreateMenu()方法:
    {
        public boolean onCreateOptionsMenu(Menu menu) {
            getMenuInflater().inflate(R.menu.main, menu);
            return true;
        }
    }
    定义菜单响应事件:
    {
        public boolean onOptionsItemSelected(MenuItem item) {
            switch (item.getItemId()) {
                case R.id.add_item:
                Toast.makeText(this, "You clicked Add", Toast.LENGTH_SHORT).show();
            break;
            case R.id.remove_item:
                Toast.makeText(this, "You clicked Remove", Toast.LENGTH_SHORT).show();
                break;
            default:
            }
            return true;
        }
    }


2、销毁一个活动：
    back键
    finish();


3、Intent

    作用:Intent是Android程序中各组件之间进行交互的一种重要方式，它不仅可以指明当前组件想要执行的动作，还可以在不同组件之间传递数据。Intent一般可被用于启动活动、启动服务以及发送广播等场景.

    在一个活动上面打开另一个活动：【显式Intent】
        {
            Intent intent = new Intent(FirstActivity.this, SecondActivity.class);
            startActivity(intent);
        }

    隐式Intent实例：
        {
            Intent intent = new Intent(Intent.ACTION_VIEW);
            intent.setData(Uri.parse("http://www.baidu.com"));
            startActivity(intent);
        }

    从first活动中通过Intent传递数据到second活动中：
    {
        String data = "Hello SecondActivity";
        Intent intent = new Intent(FirstActivity.this, SecondActivity.class);
        intent.putExtra("extra_data", data); //相当于键值对
        startActivity(intent);
    }
    从second活动取出first活动传递来的数据：
    {
        Intent intent = getIntent();
        //传递来的是String，所以用的是getStringExtra方法，还有getIntExtra()...
        String data = intent.getStringExtra("extra_data"); 
        Log.d("SecondActivity", data);
    }

    返回数据给上一个活动：从second返回first
    first中代码
    {
        button1.setOnClickListener(new View.OnClickListener() {
        @Override
        public void onClick(View v) {
            Intent intent = new Intent(FirstActivity.this, SecondActivity.class);
            //调用此方法来启动second活动，在second活动销毁之前会回调fisrt活动onActivityResult()
            startActivityForResult(intent, 1); 
        }
        });

        @Override
        protected void onActivityResult(int requestCode, int resultCode, Intent data) {
        switch (requestCode) {
            case 1:
                if (resultCode == RESULT_OK) {
                    String returnedData = data.getStringExtra("data_return");
                    Log.d("FirstActivity", returnedData);
                }
            break;
            default:
        }
        }
    }
    second中的代码
    {
        public class SecondActivity extends AppCompatActivity {
            @Override
            protected void onCreate(Bundle savedInstanceState) {
                super.onCreate(savedInstanceState);
                setContentView(R.layout.second_layout);
                Button button2 = (Button) findViewById(R.id.button_2);
                button2.setOnClickListener(new View.OnClickListener() {
                    @Override
                    public void onClick(View v) {
                        Intent intent = new Intent();
                        intent.putExtra("data_return", "Hello FirstActivity");
                        //setResult接受两个参数，第一个参数用于向上一个活动返回处理结果
                        //一般只是用RESULT_OK OR RESULT_CANCELED两个
                        //第二个参数则把带有数据的Intent传递回去
                        setResult(RESULT_OK, intent);
                        finish();
                    }   
                });
            }
        }
    }


4、活动状态
    运行状态：当一个活动位于返回栈的栈顶时，这时活动就处于运行状态。系统最不愿意回收的就是处于运行状态的活动，因为这会带来非常差的用户体验。

    暂停状态：当一个活动不再处于栈顶位置，但仍然可见时，这时活动就进入了暂停状态。你可能会觉得既然活动已经不在栈顶了，还怎么会可见呢？这是因为并不是每一个活动都会占满整个屏幕的，比如对话框形式的活动只会占用屏幕中间的部分区域，你很快就会在后面看到这种活动。处于暂停状态的活动仍然是完全存活着的，系统也不愿意去回收这种活动（因为它还是可见的，回收可见的东西都会在用户体验方面有不好的影响），只有在内存极低的情况下，系统才会去考虑回收这种活动。

    停止状态：当一个活动不再处于栈顶位置，并且完全不可见的时候，就进入了停止状态。系统仍然会为这活动保存相应的状态和成员变量，但是这并不是完全可靠的，当其他地方需要内存时，处于停止状态的活动有可能会被系统回收。

    销毁状态：当一个活动从返回栈中移除后就变成了销毁状态。系统会最倾向于回收处于这种状态的活动，从而保证手机的内存充足。

5、活动的生命周期
    onCreate()。这个方法你已经看到过很多次了，每个活动中我们都重写了这个方法，它会在活动第一
    次被创建的时候调用。你应该在这个方法中完成活动的初始化操作，比如说加载布局、绑定事件等。

    onStart()。这个方法在活动由不可见变为可见的时候调用。

    onResume()。这个方法在活动准备好和用户进行交互的时候调用。此时的活动一定位于返回栈的栈
    顶，并且处于运行状态。

    onPause()。这个方法在系统准备去启动或者恢复另一个活动的时候调用。我们通常会在这个方法中
    将一些消耗CPU的资源释放掉，以及保存一些关键数据，但这个方法的执行速度一定要快，不然会影
    响到新的栈顶活动的使用。

    onStop()。这个方法在活动完全不可见的时候调用。它和onPause()方法的主要区别在于，如果启动
    的新活动是一个对话框式的活动，那么onPause()方法会得到执行，而onStop()方法并不会执行。

    onDestroy()。这个方法在活动被销毁之前调用，之后活动的状态将变为销毁状态。

    onRestart()。这个方法在活动由停止状态变为运行状态之前调用，也就是活动被重新启动了。

    上面onCreate() -> onDestroy()是完整生存期, onStart() -> onStop()是可见生存期, onResume -> onPause()是前台生存期

6、活动被回收怎么办?
    假设在一个活动启动了另外一个活动，然后此活动被系统回收了，那么要用到onSaveInstanceState()方法，此方法可以保证活动在被回收前调用。

    保存数据代码：
    {
        @Override
        protected void onSaveInstanceState(Bundle outState) {
            super.onSaveInstanceState(outState);
            String tempData = "Something you just typed";
            outState.putString("data_key", tempData);
        }
    }

    恢复数据代码：
    {
        @Override
        protected void onCreate(Bundle savedInstanceState) {
            super.onCreate(savedInstanceState);
            Log.d(TAG, "onCreate");
            setContentView(R.layout.activity_main);
            if (savedInstanceState != null) {
                String tempData = savedInstanceState.getString("data_key");
                Log.d(TAG, tempData);
            }
            ...
        }
    }


7、活动的启动模式
    启动模式一共有4种，分别是standard、singleTop、singleTask和singleInstance，可以在AndroidManifest.xml中通过给<activity>标签指定android:launchMode属性来选择启动模式。

    standard: 
    缺省默认为standard.
    从打印信息中我们就可以看出，每点击一次按钮就会创建出一个新的FirstActivity实例。此时返回栈中也会存在3个FirstActivity的实例，因此你需要连按3次Back键才能退出程序。

    singleTop:
    不管你点击多少次按钮都不会再有新的打印信息出现，因为目前FirstActivity已经处于返回栈的栈顶，每当想要再启动一个FirstActivity时都会直接使用栈顶的活动，因此FirstActivity也只会有一个实例，仅按一次Back键就可以退出程序。
    
    ###不过当FirstActivity并未处于栈顶位置时，这时再启动FirstActivity，还是会创建新的实例的。

    singleTask:
    改进singleTop中的###。
    当活动的启动模式指定为singleTask，每次启动该活动时系统首先会在返回栈中检查是否存在该活动的实例，如果发现已经存在则直接使用该实例，并把在这个活动之上的所有活动统统出栈，如果没有发现就会创建一个新的活动实例。

    singleInstance:
    前提知识：每个应用程序都会有自己的返回栈，同一个活动在不同的返回栈中入栈时必然是创建了新的实例。
    使用singleInstance模式就可以解决这个问题，在这种模式下会有一个单独的返回栈来管理这个活动，不管是哪个应用程序来访问这个活动，都共用的同一个返回栈，也就解决了共享活动实例的问题。
    

8、使用隐式Intent
    {
        <activity android:name=".SecondActivity" >
            <intent-filter>
                <action android:name="com.example.activitytest.ACTION_START" />
                <category android:name="android.intent.category.DEFAULT" />
                </intent-filter>
        </activity>
    }
    只有<action>和<category>中的内容同时能够匹配上Intent中指定的action和category时，这个活动才能响应该Intent。意思是当你在一个活动中通过隐式Intent调用另一个活动时，内容必须和那个活动的action和catetory相同才能启动那个活动，否则不能。
    例如：
    {
        Intent intent = new Intent("com.example.activitytest.ACTION_START");startActivity(intent);
    }


9、如何知道当前是在哪一个活动?
    {
        Log.d("BaseActivity", getClass().getSimpleName());
    }


10、如何随时随地退出程序：
    写一个类作为活动管理器：
    {
        public class ActivityCollector {
            public static List<Activity> activities = new ArrayList<>();
            public static void addActivity(Activity activity) {
                activities.add(activity);
            }
            public static void removeActivity(Activity activity) {
                activities.remove(activity);
            }
            public static void finishAll() {
                for (Activity activity : activities) {
                    if (!activity.isFinishing()) {
                        activity.finish();
                    }
                }
            activities.clear();
            }
        }
    }

    实例：
    {
        public class BaseActivity extends AppCompatActivity {
            @Override
            protected void onCreate(Bundle savedInstanceState) {
                super.onCreate(savedInstanceState);
                Log.d("BaseActivity", getClass().getSimpleName());
                ActivityCollector.addActivity(this);
            }
            @Override
            protected void onDestroy() {
                super.onDestroy();
                ActivityCollector.removeActivity(this);
            }
        }
    }


11、启动活动的最佳写法
    当我在一个活动中想启动另一个活动的时候，但是另外的一个活动不是我写的，我不知道如何向他传递数据，这时候为了更好的开发，另外一个活动在编写的时候最好写上一个静态的方法，加上参数。如下：
    {
        public static void actionStart(Context context, String data1, String data2) {
            Intent intent = new Intent(context, SecondActivity.class);
            intent.putExtra("param1", data1);
            intent.putExtra("param2", data2);
            context.startActivity(intent);
        }
    }

    在我写的代码当中只需要如下的调用：
    {
        SecondActivity.actionStart(FirstActivity.this, "data1", "data2");
    }


12、如何重置标题栏：
    先写一个标题栏布局：
    {
        <LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:background="@drawable/title_bg">
            <Button
                android:id="@+id/title_back"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:layout_gravity="center"
                android:layout_margin="5dp"
                android:background="@drawable/back_bg"
                android:text="Back"
                android:textColor="#fff" />
            <TextView
                android:id="@+id/title_text"
                android:layout_width="0dp"
                android:layout_height="wrap_content"
                android:layout_gravity="center"
                android:layout_weight="1"
                android:gravity="center"
                android:text="Title Text"
                android:textColor="#fff"
                android:textSize="24sp" />
            <Button
                android:id="@+id/title_edit"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:layout_gravity="center"
                android:layout_margin="5dp"
                android:background="@drawable/edit_bg"
                android:text="Edit"
                android:textColor="#fff" />
        </LinearLayout>
    }

    修改需要更改标题栏的活动的布局代码
    {
        <LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
            android:layout_width="match_parent"
            android:layout_height="match_parent" >

            <include layout="@layout/title" />
        </LinearLayout>
    }

    修改需要更改标题栏的活动的java代码，将系统自带的标题栏隐藏掉
    {
        public class MainActivity extends AppCompatActivity {
            @Override
            protected void onCreate(Bundle savedInstanceState) {
                super.onCreate(savedInstanceState);
                setContentView(R.layout.activity_main);
                ActionBar actionbar = getSupportActionBar();
                if (actionbar != null) {
                    actionbar.hide();
                }
            }
        }
    }


13、如何创建自定义控件？
    首先自己定义一个类继承自LinearLayout
    {
        public class TitleLayout extends LinearLayout {
            public TitleLayout(Context context, AttributeSet attrs) {
                super(context, attrs);
                LayoutInflater.from(context).inflate(R.layout.title, this);
            }
        }
    }
    然后就可以把自己定义的类TitleLayout当作一个控件使用啦，例如
    {
        <LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
            android:layout_width="match_parent"
            android:layout_height="match_parent" >
            <com.example.uicustomviews.TitleLayout
                android:layout_width="match_parent"
                android:layout_height="wrap_content" />
        </LinearLayout>
    }


14、ListView
    作用：允许用户通过手指上下滑动的方式将屏幕外的数据滚动到屏幕内，同时屏幕上原有的数据则会滚动出屏幕。

    使用步骤：
        首先自己创建一个活动，并在相应的布局文件内添加一个ListView控件
        {
            <LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
                android:layout_width="match_parent"
                android:layout_height="match_parent">

                <ListView
                    android:id="@+id/list_view"
                    android:layout_width="match_parent"
                    android:layout_height="match_parent" />
            </LinearLayout>
        }

        然后修改活动内的代码
        {
            public class MainActivity extends AppCompatActivity {
                //提供ListView要显示的数据
                private String[] data = { "Apple", "Banana", "Orange", "Watermelon",
                "Pear", "Grape", "Pineapple", "Strawberry", "Cherry", "Mango",
                "Apple", "Banana", "Orange", "Watermelon", "Pear", "Grape",
                "Pineapple", "Strawberry", "Cherry", "Mango" };

                @Override
                protected void onCreate(Bundle savedInstanceState) {
                super.onCreate(savedInstanceState);
                setContentView(R.layout.activity_main);
                //数组中的数据无法直接传递给ListView，需要借用适配器来完成。
                //参数依次为当前上下文，ListView子项布局的id，适配的数据
                //android.R.layout.simple_list_item_1是内置的子项布局id，只有一个textview，可用于简单的显示一段文本
                ArrayAdapter<String> adapter = new ArrayAdapter<String>(
                    MainActivity.this, android.R.layout.simple_list_item_1, data);
                ListView listView = (ListView) findViewById(R.id.list_view);
                listView.setAdapter(adapter);
                }
            }
        }