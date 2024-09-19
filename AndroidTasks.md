# Google AndroidFundamental Workshop to Android: https://youtu.be/xNPkXGdVw7E

# Workspace: [Where is Everything](https://drive.google.com/drive/folders/1D7rHV4zzCX0xpIWjr7wAJzpV6Vic5toE)


# 1.Hello WorldApp



# 2.ToastCountAPP:
<img width="839" alt="one" src="https://github.com/user-attachments/assets/2db1b8af-e229-4678-be7c-d50e4c6f0c4b">

Xml:
```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
xmlns:android="http://schemas.android.com/apk/res/a
ndroid"
android:layout_width="match_parent"
android:layout_height="match_parent"
android:orientation="vertical"
android:background="#FFEB3B"**
>

< Button
android:id="@+id/toastBtn"
android:layout_width="match_parent"
android:layout_height="0dp"
android:layout_weight="1"
android:text="Toast"
android:onClick="showToast" />

< TextView
android:id="@+id/tv"
android:layout_width="match_parent"
android:layout_height="0dp"
android:layout_weight="8"
android:text="0"
android:textSize="200sp"
android:gravity="center"
/>

< Button
android:id="@+id/countBtn"
android:layout_width="match_parent"
android:layout_height="0dp"
android:layout_weight="1"
android:text="Count" />

</LinearLayout>

```

Java/Kotlin:


```
import android.os.Bundle
import android.view.View
import android.widget.Button
import android.widget.TextView
import android.widget.Toast
import androidx.appcompat.app.AppCompatActivity

class MainActivity : AppCompatActivity() {
    lateinit var toastBtn: Button
    lateinit var countText: TextView
    lateinit var countBtn: Button
    var counter = 0
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        toastBtn = findViewById(R.id.toast_button)
        countText = findViewById(R.id.countext)
        countBtn = findViewById(R.id.count_button)

        countBtn.setOnClickListener {
            counter = counter + 1
            countText.text = counter.toString()
        }

    }

    fun toastMe(view: View) {
        Toast.makeText(this,
            "Hello Toast!", Toast.LENGTH_SHORT)
            .show()
    }
}

```


# MultipleActivities & Intents:

**========================================**

## 3.Intents App:

<img width="344" alt="two" src="https://github.com/user-attachments/assets/239b749b-744b-4b2d-8f88-a6eff36202a2">

1.activity_main.xml:

```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:orientation="vertical"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

   <Button
       android:id="@+id/explicitIntent"
       android:layout_width="match_parent"
       android:layout_height="wrap_content"
       android:text="Explicit Intent"/>

    <Button
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Implicit Intent"
        android:onClick="implicitIntent"/>
</LinearLayout>
```

MainActivity.java:
==============

```
class MainActivity : AppCompatActivity() {
    lateinit var explicitIntent:Button
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
        explicitIntent = findViewById(R.id.explicitIntent)

        explicitIntent.setOnClickListener {
            val intent = Intent(this,
                SecondActivity::class.java)
            startActivity(intent)
        }
    }

    fun implicitIntent(view: View) {
        val uri = Uri.parse("https://www.google.com")
        val intent = Intent(Intent.ACTION_VIEW, uri)
        startActivity(intent)
    }
}

```

Activity_second.xml:
—-----------------------------------
```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:orientation="vertical"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".SecondActivity">

    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Welcome to Second Screen"
        android:textSize="16sp"/>

</LinearLayout>

```

SecondActivity.java:
=========

```
class SecondActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_second)

    }
}

```
## 4.ActivityLifeCycleAPP:

<img width="1013" alt="three" src="https://github.com/user-attachments/assets/51f0f950-95ee-48d7-b3d5-68166cba578a">


```
class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
        Toast.makeText(this, "onCreate", Toast.LENGTH_SHORT).show()
    }

    override fun onStart() {
        super.onStart()
        Toast.makeText(this, "onStart", Toast.LENGTH_SHORT).show()
    }

    override fun onResume() {
        super.onResume()
        Toast.makeText(this, "onResume", Toast.LENGTH_SHORT).show()
    }
    override fun onPause() {
        super.onPause()
        Toast.makeText(this, "onPause", Toast.LENGTH_SHORT).show()
    }
    override fun onStop() {
        super.onStop()
        Toast.makeText(this, "onStop", Toast.LENGTH_SHORT).show()
    }
    override fun onDestroy() {
        super.onDestroy()
        Toast.makeText(this, "onDestroy", Toast.LENGTH_SHORT).show()
    }
    override fun onRestart() {
        super.onRestart()
        Toast.makeText(this, "onRestart", Toast.LENGTH_SHORT).show()
    }
}

```

## 6.Menus:

<img width="1011" alt="four" src="https://github.com/user-attachments/assets/0cc253bd-a445-4e6f-bfda-cce30d7a8a1d">

<img width="864" alt="five" src="https://github.com/user-attachments/assets/14c6b0fe-c5f1-44d1-a13a-130d26bcceb2">

Menu.xml:
========
```
<?xml version="1.0" encoding="utf-8"?>
<menu xmlns:android="http://schemas.android.com/apk/res/android">
    <item android:title="About us"
        android:id="@+id/aboutusId"/>

    <item android:title="Settings"
        android:id="@+id/settingsId"/>

    <item android:title="Logout"
        android:id="@+id/logoutId"/>
</menu>

```

activity_main.xml
=================
```

<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Hello World!"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

</androidx.constraintlayout.widget.ConstraintLayout>

```

MainActivity.java
—-------------------
```
class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
    }

//Step 1
    override fun onCreateOptionsMenu(menu: Menu?): Boolean {
        menuInflater.inflate(R.menu.my_menu,menu)

        return super.onCreateOptionsMenu(menu)
    }

//Step 2
    override fun onOptionsItemSelected(item: MenuItem): Boolean {
        when(item.itemId){
            R.id.aboutusId ->
                Toast.makeText(this,"About us",Toast.LENGTH_SHORT).show()
            R.id.settingsId ->
                Toast.makeText(this,"Settings",Toast.LENGTH_SHORT).show()
            R.id.logoutId ->
                Toast.makeText(this,"Settings",Toast.LENGTH_SHORT).show()
        }
        return super.onOptionsItemSelected(item)

    }


}

```

themes.xml
=========
```
<resources xmlns:tools="http://schemas.android.com/tools">
    <!-- Base application theme. -->
    <style name="Base.Theme.MyApplication" parent="Theme.AppCompat">
        <!-- Customize your light theme here. -->
        <!-- <item name="colorPrimary">@color/my_light_primary</item> -->
    </style>

    <style name="Theme.MyApplication" parent="Theme.AppCompat" />
</resources>

```

# 7. Whats App
===============
<img width="356" alt="Screenshot 2024-09-19 at 8 05 26 AM" src="https://github.com/user-attachments/assets/8e2b1365-7f6f-4cd6-ac98-65bfd8ae3d6a">

Steps to implement What's app kind of app

1. Create new android studio project "WhatsApp"(project name)
2. Open activity_main.xml -> Change root layout to LinearLayout and add orientation as vertical
3. Take TabView and ViewPager inside activity_main.xml
    <img width="1021" alt="Screenshot 2024-09-19 at 7 35 53 AM" src="https://github.com/user-attachments/assets/5165827d-067f-4fa5-9ae5-06c10b09b418">
4. Configure tabview and viewpager to the MainActivity.kt
    <img width="1059" alt="Screenshot 2024-09-19 at 7 45 06 AM" src="https://github.com/user-attachments/assets/457552a3-f979-4f1f-ad32-66d7b63915a1">


MainActivity.kt
===============
```
class MainActivity : AppCompatActivity() {
    lateinit var tab:TabLayout
    lateinit var viewPager: ViewPager
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        tab = findViewById(R.id.tab)
        viewPager = findViewById(R.id.viewpager)

        viewPager.adapter = MyAdapter(supportFragmentManager)
        tab.setupWithViewPager(viewPager)

    }
}

class MyAdapter(fm: FragmentManager) : FragmentStatePagerAdapter(fm){

    override fun getCount(): Int {
        return 3
    }

    override fun getItem(position: Int): Fragment {
        when(position){
            0 -> return ChatsFragment()
            1 -> return CallsFragment()
            2 -> return StatusFragment()
            else -> return ChatsFragment()
        }
    }

    override fun getPageTitle(position: Int): CharSequence {
        when (position) {
            0 -> return "Chats"
            1 -> return "Calls"
            2 -> return "Status"
            else -> return "Chats"
        }
    }
}

```

actvity_main.xml
=======
```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:orientation="vertical"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

   <com.google.android.material.tabs.TabLayout
       android:id="@+id/tab"
       android:layout_width="match_parent"
       android:layout_height="wrap_content"
       android:background="#59CFE6"/>

    <androidx.viewpager.widget.ViewPager
        android:id="@+id/viewpager"
        android:layout_width="match_parent"
        android:layout_height="match_parent"/>
</LinearLayout>
```

ChatsFragment.kt
====

```
class ChatsFragment : Fragment() {

    override fun onCreateView(
        inflater: LayoutInflater, container: ViewGroup?,
        savedInstanceState: Bundle?
    ): View? {
        // Inflate the layout for this fragment
        return inflater.inflate(R.layout.fragment_chats, container, false)
    }

}

```
fragment_chats.xml
=====
```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="#AA9E9E">

    <TextView
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:text="Chats Fragment"
        android:gravity="center"/>

</LinearLayout>

```

CallsFragment.kt
====
```
class CallsFragment : Fragment() {

    override fun onCreateView(
        inflater: LayoutInflater, container: ViewGroup?,
        savedInstanceState: Bundle?
    ): View? {
        // Inflate the layout for this fragment
        return inflater.inflate(R.layout.fragment_calls, container, false)
    }

}

```
fragment_calls.xml
===
```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="#F1E8E8"
    tools:context=".CallsFragment">

    <TextView
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:text="Calls Fragment"
        android:gravity="center"/>

</LinearLayout>

```

StatusFragment.kt
=====
```
class StatusFragment : Fragment() {

    override fun onCreateView(
        inflater: LayoutInflater, container: ViewGroup?,
        savedInstanceState: Bundle?
    ): View? {
        // Inflate the layout for this fragment
        return inflater.inflate(R.layout.fragment_status, container, false)
    }

}

```

fragment_status.xml
=====
```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="#CEF1D4">

    <TextView
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:text="Status Fragment"
        android:gravity="center"/>

</LinearLayout>
```



