# ViewPagerSimpleDots
 https://medium.com/@adrian.kuta93/android-viewpager-with-dots-indicator-a34c91e59e3a

- `MainActivity.java`
```java
public class MainActivity extends AppCompatActivity {

    TabLayout dotsTab;
    ViewPager viewPager;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        dotsTab = findViewById(R.id.dots_tab);
        viewPager = findViewById(R.id.view_pager);

        ViewPagerAdapter viewPagerAdapter = new ViewPagerAdapter(getSupportFragmentManager(), FragmentPagerAdapter.BEHAVIOR_RESUME_ONLY_CURRENT_FRAGMENT);

        viewPagerAdapter.addFragment(FirstFragment.newInstance());
        viewPagerAdapter.addFragment(SecondFragment.newInstance());

        viewPager.setAdapter(viewPagerAdapter);
        dotsTab.setupWithViewPager(viewPager);
    }
}
```

- `activity_main.xml`
```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    tools:context=".MainActivity">

    <androidx.viewpager.widget.ViewPager
        android:id="@+id/view_pager"
        android:layout_width="match_parent"
        android:layout_height="0dp"
        android:layout_weight="1"
        app:layout_behavior="@string/appbar_scrolling_view_behavior" />

    <com.google.android.material.tabs.TabLayout
        android:id="@+id/dots_tab"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        app:tabBackground="@drawable/tab_selector"
        app:tabGravity="center"
        app:tabIndicatorColor="@color/colorAccent"
        app:tabIndicatorHeight="0dp"
        app:tabSelectedTextColor="@android:color/white"
        app:tabTextColor="@android:color/white" />

</LinearLayout>
```

- `ViewPagerAdapter.java`
```java
public class ViewPagerAdapter extends FragmentPagerAdapter {

    private ArrayList<Fragment> fragments;

    public ViewPagerAdapter(@NonNull FragmentManager fm, int behavior) {
        super(fm, behavior);
        this.fragments = new ArrayList<>();
    }

    @NonNull
    @Override
    public Fragment getItem(int position) {
        return fragments.get(position);
    }

    @Override
    public int getCount() {
        return fragments.size();
    }

    public void addFragment(Fragment fr){
        fragments.add(fr);
    }
}
```

- `fragment_first.xml`
```xml
<?xml version="1.0" encoding="utf-8"?>
<FrameLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".FirstFragment">

    <!-- TODO: Update blank fragment layout -->
    <TextView
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:text="@string/hello_blank_fragment" />

</FrameLayout>
```

- `FirstFragment.java`
```java
public class FirstFragment extends Fragment {

    public static FirstFragment instance(){
        return new FirstFragment();
    }

    public FirstFragment() {
        // Required empty public constructor
    }

    @Override
    public View onCreateView(LayoutInflater inflater, ViewGroup container,
                             Bundle savedInstanceState) {
        // Inflate the layout for this fragment
        return inflater.inflate(R.layout.fragment_first, container, false);
    }
}
```

---

```
Copyright 2020 M. Fadli Zein
```
