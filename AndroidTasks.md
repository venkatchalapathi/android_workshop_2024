# Google AndroidFundamental Workshop to Android: https://youtu.be/xNPkXGdVw7E

# Workspace: [Where is Everything](https://drive.google.com/drive/folders/1D7rHV4zzCX0xpIWjr7wAJzpV6Vic5toE)


# 1.Hello WorldApp



# 2.ToastCountAPP:


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

## 3.ExplicitIntent App:


1.Activity_main.xml:
_<?_ **xml version="1.0" encoding="utf-8"** _?>_
< **LinearLayout**

**xmlns:android="http://schemas.android.com/apk/res/a
ndroid"**

**xmlns:app="http://schemas.android.com/apk/res-auto"
xmlns:tools="http://schemas.android.com/tools"**


```
android:layout_width="match_parent"
android:layout_height="match_parent"
tools:context=".MainActivity"
android:orientation="vertical"
android:layout_gravity="center_vertical"
android:gravity="center" >
```
```
< TextView
android:layout_width="match_parent"
android:layout_height="wrap_content"
android:text="Welcome to First Activity"
android:layout_gravity="center"
android:gravity="center"
android:textSize="40sp"
android:textColor="#000"
/>
```
```
< EditText
android:id="@+id/et"
android:layout_width="match_parent"
android:layout_height="wrap_content"
android:hint="Type a Message"
android:layout_marginTop="10dp"
/>
```
```
< Button
android:layout_width="wrap_content"
android:layout_height="wrap_content"
android:text="Next"
android:textColor="@color/white"
android:onClick="goNext"
/>
```
</ **LinearLayout** >


MainActivity.java:
==============

**package** com.example.explicitintent;

**import** androidx.appcompat.app.AppCompatActivity;

**import** android.content.Intent;
**import** android.os.Bundle;
**import** android.view.View;
**import** android.widget.EditText;

**public class** MainActivity **extends** AppCompatActivity
{

```
EditText et ;
```
@Override
**protected void** onCreate(Bundle
savedInstanceState) {
**super** .onCreate(savedInstanceState);
setContentView(R.layout. **_activity_main_** );

```
et = findViewById(R.id. et );
```
```
}
```
```
public void goNext(View view) {
String msg = et .getText().toString().trim();
```
Intent i = **new** Intent(MainActivity. **this** ,
SecondActivity. **class** );

```
//i.putExtra( "key" , "hi" );
i.putExtra( "key" , msg);
```
```
startActivity(i);
}
```

}

Activity_second.xml:
—-----------------------------------
**_<?_** **xml version="1.0" encoding="utf-8"** **_?>_**
**<LinearLayout**

**xmlns:android="http://schemas.android.com/apk/res/a
ndroid"**

**xmlns:app="http://schemas.android.com/apk/res-auto"
xmlns:tools="http://schemas.android.com/tools"
android:layout_width="match_parent"
android:layout_height="match_parent"
tools:context=".SecondActivity"
>**

```
<TextView
android:id="@+id/tv"
android:layout_width="match_parent"
android:layout_height="wrap_content"
android:text="Welcome to Second Activity"
android:layout_gravity="center"
android:gravity="center"
android:textSize="30sp"/>
```
**</LinearLayout>**

SecondActivity.java:

**—---------------**


**package com.example.explicitintent;**

**import androidx.appcompat.app.AppCompatActivity;**

**import android.os.Bundle;
import android.widget.TextView;**

**public class SecondActivity extends
AppCompatActivity {**

```
TextView tv;
```
**@Override
protected void onCreate(Bundle
savedInstanceState) {
super.onCreate(savedInstanceState);
setContentView(R.layout.** **_activity_second_** **);**

```
tv = findViewById(R.id. tv );
```
**String receivedValue =
getIntent().getStringExtra("key");**

```
tv.setText(receivedValue);
```
**}
}**


# Implicit Intents:

## 4.ActivityLifeCycleAPP:

**==============================**

**Task:
1.Activity Life Cycle**



**Ref: https://youtu.be/5b2r3Z5UcHU**

**2.What is Fragment?
3.Fragment Lifecycle**

**4.Multiple Activities & Intents:**

**Ref : https://youtu.be/3dsAuLkDTUc**


## 5.InputControls:


Xml:
====
_<?_ xml version="1.0" encoding="utf-8" _?>_
<ScrollView

xmlns:android="http://schemas.android.com/apk
/res/android"

xmlns:app="http://schemas.android.com/apk/res
-auto"

xmlns:tools="http://schemas.android.com/tools
"


```
android:layout_width="match_parent"
android:layout_height="match_parent"
tools:context=".MainActivity"
>
```
```
<LinearLayout
android:layout_width="match_parent"
android:layout_height="wrap_content"
android:orientation="vertical"
android:layout_margin="10dp">
```
```
<EditText
android:layout_width="match_parent"
android:layout_height="wrap_content"
```
android:hint="@string/enter_your_name"
android:layout_marginTop="10dp"/>

```
<EditText
android:layout_width="match_parent"
android:layout_height="wrap_content"
android:hint="Enter Phone Number"
android:inputType="phone"
android:layout_marginTop="10dp"
/>
<EditText
android:layout_width="match_parent"
android:layout_height="wrap_content"
android:hint="Enter your Email ID"
android:inputType="textEmailAddress"
android:layout_marginTop="10dp"
/>
```

```
<Spinner
android:layout_width="match_parent"
android:layout_height="wrap_content"
android:layout_marginTop="10dp"
android:entries="@array/branches"
/>
```
<androidx.appcompat.widget.AppCompatTextView
android:layout_width="match_parent"
android:layout_height="wrap_content"
android:text="Select Your Favourites
in Food"
android:layout_marginVertical="10dp"
/>

```
<LinearLayout
android:layout_width="match_parent"
android:layout_height="wrap_content"
>
```
```
<CheckBox
android:layout_width="0dp"
android:layout_weight="1"
```
android:layout_height="wrap_content"
android:text="Dosa"
/>
<CheckBox
android:layout_width="0dp"
android:layout_weight="1"


android:layout_height="wrap_content"
android:text="Biryani"
/>

```
</LinearLayout>
```
```
<LinearLayout
android:layout_width="match_parent"
android:layout_height="wrap_content"
>
<CheckBox
android:layout_width="0dp"
android:layout_weight="1"
```
android:layout_height="wrap_content"
android:text="Ice Cream"
/>
<CheckBox
android:layout_width="0dp"
android:layout_weight="1"

android:layout_height="wrap_content"
android:text="Fried Rice"
/>
</LinearLayout>

```
<RadioGroup
android:layout_width="match_parent"
android:layout_height="wrap_content"
android:orientation="horizontal"
>
```

```
<RadioButton
```
android:layout_width="wrap_content"

android:layout_height="wrap_content"
android:text="Male"
/>
<RadioButton

android:layout_width="wrap_content"

android:layout_height="wrap_content"
android:text="FeMale"

android:layout_marginHorizontal="30dp"
/>
<RadioButton

android:layout_width="wrap_content"

android:layout_height="wrap_content"
android:text="Others"

android:layout_marginHorizontal="30dp"
/>

```
</RadioGroup>
```
<com.google.android.material.button.MaterialB
utton


```
android:layout_width="match_parent"
android:layout_height="wrap_content"
android:text="SignUP"
android:layout_marginVertical="20dp"
android:onClick="signUp"
/>
```
```
</LinearLayout>
```
</ScrollView>

MainActivity.java:
=============
package com.example.inputcontrolstest;

import
androidx.appcompat.app.AppCompatActivity;

import android.os.Bundle;
import android.view.View;

public class MainActivity extends
AppCompatActivity {

@Override
protected void onCreate(Bundle
savedInstanceState) {
super.onCreate(savedInstanceState);

setContentView(R.layout.activity_main);


### }

public void signUp(View view) {
}
}

Strings.xml:
<resources>
<string name="app_name">Input Controls
Test</string>
<string name="enter_your_name">Enter your
Name</string>
<string-array name="branches">
<item>Select your Branch</item>
<item>CSE</item>
<item>ECE</item>
<item>MECH</item>
<item>IT</item>
<item>AI ML</item>
</string-array>
</resources>


## 6.Menus:

Steps:

**Menu.xml:**
========
_<?_ **xml version="1.0" encoding="utf-8"** _?>_


< **menu
xmlns:android="http://schemas.android.com/apk/res/a
ndroid"**

**xmlns:app="http://schemas.android.com/apk/res-auto"**
>

```
< item
android:id="@+id/menu_settings"
android:title="Settings"
/>
< item
android:id="@+id/menu_logout"
android:title="LogOut"
/>
< item
android:id="@+id/menu_search"
android:title="Search"
app:showAsAction="always"
```
**android:icon="@drawable/ic_baseline_search_24"**
/>
</ **menu** >

**activity_main.xml:**
=================

_<?_ **xml version="1.0" encoding="utf-8"** _?>_
< **androidx.constraintlayout.widget.ConstraintLayout
xmlns:android="http://schemas.android.com/apk/res/a
ndroid"**

**xmlns:app="http://schemas.android.com/apk/res-auto"**


```
xmlns:tools="http://schemas.android.com/tools"
android:layout_width="match_parent"
android:layout_height="match_parent"
tools:context=".MainActivity" >
```
```
< TextView
android:layout_width="wrap_content"
android:layout_height="wrap_content"
android:text="Hello World!"
```
**app:layout_constraintBottom_toBottomOf="parent"
app:layout_constraintLeft_toLeftOf="parent"**

**app:layout_constraintRight_toRightOf="parent"
app:layout_constraintTop_toTopOf="parent"** />

</ **androidx.constraintlayout.widget.ConstraintLayout**
>

**MainActivity.java**
—-------------------
**package** com.example.menus;

**import** androidx.appcompat.app.AppCompatActivity;

**import** android.os.Bundle;
**import** android.view.Menu;

**public class** MainActivity **extends** AppCompatActivity
{

@Override
**protected void** onCreate(Bundle
savedInstanceState) {
**super** .onCreate(savedInstanceState);
setContentView(R.layout. **_activity_main_** );


```
}
```
//Step-1

```
@Override
public boolean onCreateOptionsMenu(Menu menu) {
getMenuInflater().inflate(R.menu. menu , menu);
return super .onCreateOptionsMenu(menu);
}
```
//Step-2

@Override
**public boolean** onOptionsItemSelected(@NonNull
MenuItem item) {

**switch** (item.getItemId()){
**case** R.id. **_menu_logout_** :
Toast. _makeText_ ( **this** , **"You clicked "** +
item.getTitle(),
Toast. **_LENGTH_SHORT_** ).show();
**return true** ;
**case** R.id. **_menu_search_** :
Toast. _makeText_ ( **this** , **"You clicked "** +
item.getTitle(),
Toast. **_LENGTH_SHORT_** ).show();
**return true** ;
**case** R.id. **_menu_settings_** :
Toast. _makeText_ ( **this** , **"You clicked "** +
item.getTitle(),
Toast. **_LENGTH_SHORT_** ).show();

Intent i = **new**
Intent(MainActivity. **this** , SettingsActivity. **class** );
startActivity(i);


```
return true ;
```
```
}
```
**return super** .onOptionsItemSelected(item);
}
}

**activity_settings.xml:**
================

_<?_ **xml version="1.0" encoding="utf-8"** _?>_
< **androidx.constraintlayout.widget.ConstraintLayout
xmlns:android="http://schemas.android.com/apk/res/a
ndroid"**

**xmlns:app="http://schemas.android.com/apk/res-auto"
xmlns:tools="http://schemas.android.com/tools"
android:layout_width="match_parent"
android:layout_height="match_parent"
tools:context=".SettingsActivity"
android:background="#8BC34A"** >

</ **androidx.constraintlayout.widget.ConstraintLayout**
>

**SettingsActivity.java:**
=================
**package** com.example.menus;

**import** androidx.appcompat.app.AppCompatActivity;

**import** android.os.Bundle;


**public class** SettingsActivity **extends**
AppCompatActivity {

@Override
**protected void** onCreate(Bundle
savedInstanceState) {
**super** .onCreate(savedInstanceState);
setContentView(R.layout. **_activity_settings_** );
}
}

OutPut:


## FragmentLifecycle

## 7.WhatsApp:ByUsingTabLayout+ViewPager


**implementation
'com.google.android.material:material:1.6.0'**

activity_main.xml:
**=======================**
**_<?_** **xml version="1.0" encoding="utf-8"** **_?>_**
**<LinearLayout**

**xmlns:android="http://schemas.android.com/apk/res/a
ndroid"**

**xmlns:app="http://schemas.android.com/apk/res-auto"
xmlns:tools="http://schemas.android.com/tools"
android:layout_width="match_parent"
android:layout_height="match_parent"
tools:context=".MainActivity"
android:orientation="vertical">**

```
<com.google.android.material.tabs.TabLayout
```

```
android:id="@+id/tabLayout"
android:layout_width="match_parent"
android:layout_height="wrap_content"
```
**android:background="@color/design_default_color_pri
mary"
app:tabSelectedTextColor="@color/white"
app:tabTextColor="#FF5722"
/>**

```
<androidx.viewpager.widget.ViewPager
android:layout_width="match_parent"
android:layout_height="match_parent"
android:id="@+id/viewPager"
/>
```
**</LinearLayout>**

**MainActivity.java:
==============
package com.example.tablayoutviewpagertest;**

**import androidx.annotation.NonNull;
import androidx.annotation.Nullable;
import androidx.appcompat.app.AppCompatActivity;
import androidx.fragment.app.Fragment;
import androidx.fragment.app.FragmentManager;
import androidx.fragment.app.FragmentPagerAdapter;
import androidx.viewpager.widget.ViewPager;**

**import android.os.Bundle;**

**import com.google.android.material.tabs.TabLayout;**

**public class MainActivity extends AppCompatActivity
{**


```
TabLayout tabLayout;
```
```
ViewPager viewPager;
```
**@Override
protected void onCreate(Bundle
savedInstanceState) {
super.onCreate(savedInstanceState);
setContentView(R.layout.** **_activity_main_** **);**

```
tabLayout = findViewById(R.id. tabLayout );
```
```
viewPager = findViewById(R.id. viewPager );
```
**MyPagerAdapter adapter = new
MyPagerAdapter(getSupportFragmentManager());**

```
viewPager.setAdapter(adapter);
```
```
tabLayout.setupWithViewPager(viewPager);
```
```
}
```
**class MyPagerAdapter extends
FragmentPagerAdapter {**

**public MyPagerAdapter(@NonNull
FragmentManager fm) {
super(fm);
}**

```
@NonNull
@Override
public Fragment getItem(int position) {
switch (position){
case 0 :
```

```
return new ChatsFragment();
case 1 :
return new StatusFragment();
case 2 :
return new CallsFragment();
}
```
```
return null;
}
```
```
@Override
public int getCount() {
return 3 ;
}
```
**@Nullable
@Override
public CharSequence getPageTitle(int
position) {**

```
switch (position){
case 0 :
return "Chats";
case 1 :
return "Status";
case 2 :
return "Calls";
}
```
**return super.getPageTitle(position);
}
}
}**

**Note:Create 3 Fragmentswithindividualxmlbackgrounds.**

**Steps:**


**OutPut:
======**


# 8.MoviePosters App:

Example:MusicPlayerApp: **DifferentLayoutManager**




Steps:

1. Data
2. Recyclerviewinactivity_main.xml
3. layout.xml



activity_main.xml:

_<?_ xml version="1.0" encoding="utf-8" _?>_

<androidx.constraintlayout.widget.ConstraintL
ayout
xmlns:android="http://schemas.android.com/apk
/res/android"

xmlns:app="http://schemas.android.com/apk/res
-auto"

xmlns:tools="http://schemas.android.com/tools
"

```
android:layout_width="match_parent"
```
```
android:layout_height="match_parent"
```
```
tools:context=".MainActivity">
```
```
<androidx.recyclerview.widget.RecyclerView
```
```
android:id="@+id/rv"
```
```
android:layout_width="match_parent"
```
```
android:layout_height="match_parent"
```

```
tools:listitem="@layout/row"
```
app:layout_constraintBottom_toBottomOf="paren
t"

app:layout_constraintEnd_toEndOf="parent"

app:layout_constraintStart_toStartOf="parent"

app:layout_constraintTop_toTopOf="parent" />

</androidx.constraintlayout.widget.Constraint
Layout>

row.xml:

**_<?_** **xml version="1.0" encoding="utf-8"** **_?>_**
**<androidx.cardview.widget.CardView**

**xmlns:android="http://schemas.android.com/apk
/res/android"
android:layout_width="match_parent"
android:layout_height="wrap_content"**

**xmlns:app="http://schemas.android.com/apk/res
-auto"**


```
android:layout_margin="10dp"
app:cardCornerRadius="20dp"
android:elevation="2dp">
<LinearLayout
android:layout_width="match_parent"
android:layout_height="wrap_content"
android:orientation="vertical"
>
```
**<androidx.appcompat.widget.AppCompatImageView**

**android:layout_width="match_parent"
android:layout_height="300dp"
android:src="@drawable/f"
android:scaleType="fitXY"
/>
<TextView**

**android:layout_width="match_parent"**

**android:layout_height="wrap_content"
android:text="Title"
android:textSize="40sp"
android:textStyle="bold"
android:gravity="center"**

**android:layout_marginVertical="10dp"
/>**

```
</LinearLayout>
```

**</androidx.cardview.widget.CardView>**

**5.Adapter:**

```
● Createaclass
● ExtendsRecyclerview
```
```
●
```
MainActivity.java:
================
package com.example.musicplayer;

import
androidx.appcompat.app.AppCompatActivity;
import
androidx.recyclerview.widget.GridLayoutManage
r;
import
androidx.recyclerview.widget.RecyclerView;


import android.os.Bundle;

public class MainActivity extends
AppCompatActivity {
RecyclerView rv;

@Override
protected void onCreate(Bundle
savedInstanceState) {
super.onCreate(savedInstanceState);

setContentView(R.layout. _activity_main_ );

```
rv = findViewById(R.id. rv );
```
int images[] = {R.drawable. _a_ ,
R.drawable. _c_ ,
R.drawable. _d_ , R.drawable. _e_ ,
R.drawable. _f_ ,
R.drawable. _g_ , R.drawable. _h_ ,
R.drawable. _i_ , R.drawable. _j_ };

```
String titles[] = {"A", "B", "C", "D",
"e","f","g","h","i","j"};
```
rv.setLayoutManager(new
GridLayoutManager(this, 2 ));


### }

### }

**Adapter:**

Step1:


Step-2


Step-3

Step4:

Row.xml:Task-2MediaPlayer:

_<?_ xml version="1.0" encoding="utf-8" _?>_


<androidx.cardview.widget.CardView

xmlns:android="http://schemas.android.com/apk
/res/android"
android:layout_width="match_parent"
android:layout_height="wrap_content"

xmlns:app="http://schemas.android.com/apk/res
-auto"
android:layout_margin="20dp"
app:cardCornerRadius="20dp"
android:elevation="2dp">
<LinearLayout
android:layout_width="match_parent"
android:layout_height="wrap_content"
android:orientation="vertical"
>

<androidx.appcompat.widget.AppCompatImageView
android:id="@+id/img"

android:layout_width="match_parent"
android:layout_height="200dp"
android:src="@drawable/f"
android:scaleType="fitXY"
/>
<TextView
android:id="@+id/tv"

android:layout_width="match_parent"


android:layout_height="wrap_content"
android:text="Title"
android:textSize="40sp"
android:textStyle="bold"
android:gravity="center"

android:layout_marginVertical="5dp"
/>

```
<LinearLayout
```
android:layout_width="match_parent"

android:layout_height="wrap_content"

android:layout_gravity="center_vertical"
android:gravity="center"
>

<androidx.appcompat.widget.AppCompatImageView
android:id="@+id/play"
android:layout_width="100dp"
android:layout_height="100dp"

android:src="@drawable/ic_baseline_play_arrow
_24"
/>

<androidx.appcompat.widget.AppCompatImageView
android:id="@+id/pause"
android:layout_width="100dp"


```
android:layout_height="100dp"
```
android:src="@drawable/ic_baseline_pause_24"

android:layout_marginHorizontal="30dp"
/>
</LinearLayout>

```
</LinearLayout>
```
</androidx.cardview.widget.CardView>

outPut:


MainActivity.class
====================
package com.example.musicplayer;

import
androidx.appcompat.app.AppCompatActivity;
import
androidx.recyclerview.widget.GridLayoutManage
r;
import
androidx.recyclerview.widget.RecyclerView;

import android.os.Bundle;

public class MainActivity extends
AppCompatActivity {
RecyclerView rv;

@Override
protected void onCreate(Bundle
savedInstanceState) {
super.onCreate(savedInstanceState);

setContentView(R.layout. _activity_main_ );

```
rv = findViewById(R.id. rv );
```
int images[] = {R.drawable. _a_ ,
R.drawable. _b_ , R.drawable. _c_ ,
R.drawable. _d_ , R.drawable. _e_ ,
R.drawable. _f_ ,


R.drawable. _g_ , R.drawable. _h_ ,
R.drawable. _i_ , R.drawable. _j_ };

```
String titles[] = {"A", "B", "C", "D",
"e","f","g","h","i","j"};
```
```
int songs[] = {R.raw. rrr };
```
rv.setLayoutManager(new
GridLayoutManager(this, 2 ));

_//Step-1_
MusicPlayerAdapter adapter = new
MusicPlayerAdapter(images, titles, songs,
MainActivity.this);

```
//Step-3
rv.setAdapter(adapter);
```
### }

### }

MusicPlayerAdapterClass:

package com.example.musicplayer;

import android.content.Context;
import android.media.MediaPlayer;
import android.view.LayoutInflater;


import android.view.View;
import android.view.ViewGroup;
import android.widget.TextView;

import androidx.annotation.NonNull;
import
androidx.appcompat.widget.AppCompatImageView;
import
androidx.recyclerview.widget.RecyclerView;

public class MusicPlayerAdapter extends
RecyclerView.Adapter<MusicPlayerAdapter.Music
Info> {

```
int posters[];
String names[];
int songs[];
```
```
Context context;
```
```
MediaPlayer mp;
```
public MusicPlayerAdapter(int[] images,
String[] titles, int[] songs, Context ctx) {
posters = images;
names = titles;
this.songs = songs;
context = ctx;
}

```
@NonNull
@Override
```

public MusicInfo
onCreateViewHolder(@NonNull ViewGroup parent,
int viewType) {
_//Step-2_
View v =
LayoutInflater. _from_ (parent.getContext()).infl
ate(R.layout. _row_ , parent, false);
return new MusicInfo(v);
}

@Override
public void onBindViewHolder(@NonNull
MusicInfo holder, int position) {

```
holder.title.setText(names[position]);
```
holder.img.setImageResource(posters[position]
);

mp = MediaPlayer. _create_ (
context,songs[ 0 ]);

holder.play.setOnClickListener(new
View.OnClickListener() {
@Override
public void onClick(View v) {

```
if (mp.isPlaying()) {
mp.stop();
}
```

```
mp.start();
}
});
```
holder.pause.setOnClickListener(new
View.OnClickListener() {
@Override
public void onClick(View v) {
mp.stop();
}
});

### }

```
@Override
public int getItemCount() {
return posters.length;
}
```
public class MusicInfo extends
RecyclerView.ViewHolder {

```
AppCompatImageView img;
TextView title;
```
```
AppCompatImageView play, pause;
```
public MusicInfo(@NonNull View
itemView) {
super(itemView);


img =
itemView.findViewById(R.id. _img_ );
title =
itemView.findViewById(R.id. _tv_ );

play =
itemView.findViewById(R.id. _play_ );
pause =
itemView.findViewById(R.id. _pause_ );

### }

### }

### }

# 9.CinemaTalk:

Content_main.xml:
==========================
_<?_ xml version="1.0" encoding="utf-8" _?>_
<LinearLayout

xmlns:android="http://schemas.android.com/apk
/res/android"


xmlns:app="http://schemas.android.com/apk/res
-auto"
android:layout_width="match_parent"
android:layout_height="match_parent"

app:layout_behavior="@string/appbar_scrolling
_view_behavior">

```
<androidx.recyclerview.widget.RecyclerView
android:id="@+id/rv"
android:layout_width="match_parent"
android:layout_height="match_parent"
/>
```
</LinearLayout>

Activity_main.xml:

==============
_<?_ xml version="1.0" encoding="utf-8" _?>_
<androidx.coordinatorlayout.widget.Coordinato
rLayout

xmlns:android="http://schemas.android.com/apk
/res/android"

xmlns:app="http://schemas.android.com/apk/res
-auto"

xmlns:tools="http://schemas.android.com/tools
"
android:layout_width="match_parent"


```
android:layout_height="match_parent"
tools:context=".MainActivity">
```
<com.google.android.material.appbar.AppBarLay
out
android:layout_width="match_parent"
android:layout_height="wrap_content"

android:theme="@style/Theme.CinemaTalk.AppBar
Overlay">

```
<androidx.appcompat.widget.Toolbar
android:id="@+id/toolbar"
```
android:layout_width="match_parent"

android:layout_height="?attr/actionBarSize"

android:background="?attr/colorPrimary"

app:popupTheme="@style/Theme.CinemaTalk.Popup
Overlay" />

</com.google.android.material.appbar.AppBarLa
yout>

```
<include layout="@layout/content_main" />
```

<com.google.android.material.floatingactionbu
tton.FloatingActionButton
android:id="@+id/fab"
android:layout_width="wrap_content"
android:layout_height="wrap_content"
android:layout_gravity="bottom|end"

android:layout_marginEnd="@dimen/fab_margin"
android:layout_marginBottom="16dp"

app:srcCompat="@drawable/ic_baseline_favorite
_border_24" />

</androidx.coordinatorlayout.widget.Coordinat
orLayout>

MainActivity.java:

=================
package com.example.cinematalk;

import android.os.Bundle;

import
com.google.android.material.snackbar.Snackbar
;

import
androidx.appcompat.app.AppCompatActivity;

import android.view.View;


import androidx.navigation.NavController;
import androidx.navigation.Navigation;
import
androidx.navigation.ui.AppBarConfiguration;
import androidx.navigation.ui.NavigationUI;

import
com.example.cinematalk.databinding.ActivityMa
inBinding;

import android.view.Menu;
import android.view.MenuItem;

public class MainActivity extends
AppCompatActivity {

```
private ActivityMainBinding binding;
```
@Override
protected void onCreate(Bundle
savedInstanceState) {
super.onCreate(savedInstanceState);

binding =
ActivityMainBinding. _inflate_ (getLayoutInflater
());
setContentView(binding.getRoot());

```
setSupportActionBar(binding.toolbar);
```
binding.fab.setOnClickListener(new
View.OnClickListener() {


@Override
public void onClick(View view) {
Snackbar. _make_ (view, "Replace
with your own action", Snackbar. _LENGTH_LONG_ )
.setAction("Action",
null).show();
}
});
}

@Override
public boolean onCreateOptionsMenu(Menu
menu) {
_// Inflate the menu; this adds items
to the action bar if it is present._

getMenuInflater().inflate(R.menu. _menu_main_ ,
menu);
return true;
}

@Override
public boolean
onOptionsItemSelected(MenuItem item) {
_// Handle action bar item clicks here.
The action bar will
// automatically handle clicks on the
Home/Up button, so long
// as you specify a parent activity in
AndroidManifest.xml._
int id = item.getItemId();


```
//noinspection SimplifiableIfStatement
if (id == R.id. action_settings ) {
return true;
}
```
return
super.onOptionsItemSelected(item);
}

### }


# Databases: 3 Types

1. SharedPreference
2. SQLite
3. Files



