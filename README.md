# Androidtest4
这是实验四

一.基本要求

使用PrefereceFragment实现设置页面

二.代码

**Androidtest4.java:**

```

package com.example.lenovo.androidtest4;
import android.app.FragmentManager;
import android.app.FragmentTransaction;
import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;

public class Androidtest4 extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_androidtest4);
        FragmentManager fragmentManager=getFragmentManager();
        FragmentTransaction transaction=fragmentManager.beginTransaction();
        PreFragment preFragment=new PreFragment();
        transaction.add(android.R.id.content,preFragment);
        transaction.commit();
    }
}

```

**PreFragment.java:**

```

package com.example.lenovo.androidtest4;
import android.os.Bundle;
import android.preference.PreferenceFragment;
import android.support.annotation.Nullable;
public class PreFragment extends PreferenceFragment {
    @Override
    public void onCreate(@Nullable Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        addPreferencesFromResource(R.xml.preference);
    }
}

```

**preference.xml:**

```

<?xml version="1.0" encoding="utf-8"?>
<PreferenceScreen xmlns:android="http://schemas.android.com/apk/res/android">
    <PreferenceCategory android:title="In-line preferences">
        <CheckBoxPreference
            android:key="checkbox_preference"
            android:summary="This a checkbox"
            android:title="Checkbox_preference"/>
    </PreferenceCategory>
    <PreferenceCategory android:title="Dialog-based preferences">
        <EditTextPreference
            android:dialogTitle="Enter your favorite animal"
            android:title="EditTextPreference"
            android:key="edittext_preference"
            android:summary="An example that uses an edit text dialog"/>
        <ListPreference
            android:entries="@array/options"
            android:entryValues="@array/options"
            android:dialogTitle="Choose one"
            android:summary="An example that use a list dialog"
            android:title="List prefernce"
            android:key="list_preference"/>
    </PreferenceCategory>
    <PreferenceCategory android:title="Launch preferences">
        <PreferenceScreen
            android:key="screen_preference"
            android:summary="Shows another screen of preferences"
            android:title="Screen preference">
            <CheckBoxPreference
                android:key="next_scrren_checkbox_preference"
                android:summary="Preference that is on the next screen but same hierarchy"
                android:title="Toggle preference"/>
        </PreferenceScreen>
        <PreferenceScreen
            android:summary="Launches an Activity from an intent"
            android:title="Intent preference"/>
        <intent
            android:action="android.intent.action.VIEW"
            android:data="http://www.google.com"/>
    </PreferenceCategory>
    <PreferenceCategory android:title="Preference attributes">
        <CheckBoxPreference
            android:key="parent_checkbox_preference"
            android:summary="This is visually parent"
            android:title="Parent checkbox preference" />
        <CheckBoxPreference
            android:dependency="parent_checkbox_preference"
            android:key="child_checkbox_preference"
            android:summary="This is visually a child"
            android:title="Child checkbox preference" />
    </PreferenceCategory>
</PreferenceScreen>

```

**strings.xml:**

```

<resources>
    <string name="app_name">Preferece</string>
    <string-array name="options">
        　   <item>Alpha Option 01</item>
        <item>Beta Option 02</item>
        <item>Charlie Option 03</item>
    </string-array>
</resources>

```

三.结果截图

![image](https://github.com/TheEndofAbyss/PrefereceFragment/blob/master/image/4.1.png)

![image](https://github.com/TheEndofAbyss/PrefereceFragment/blob/master/image/4.2.png)

![image](https://github.com/TheEndofAbyss/PrefereceFragment/blob/master/image/4.3.png)

![image](https://github.com/TheEndofAbyss/PrefereceFragment/blob/master/image/4.4.png)

