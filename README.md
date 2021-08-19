# 👩🏻‍💻 Navigation Component Projects

## [1-Navigation Component Project](https://github.com/yagmurerdogan/Navigation-Component/tree/master/NavigationComponent) 🪐

This project contains 2 fragments and 1 activity 👽

⭐️ [Watch YouTube Tutorial!](https://www.youtube.com/watch?v=DI0NIk-7cz8)

## Preview Video
<img src="https://user-images.githubusercontent.com/47380312/129910201-ac6081ca-a78c-4d4f-ac02-c200e9cc5f19.gif" width="250" height="500"/>

### Steps
- Firstly, we should create Navigation Resource File. We can create this directory with using **Resource Manager** on Android Studio. My navigation resource file name is **[my_nav.xml](https://github.com/yagmurerdogan/Navigation-Component/tree/master/NavigationComponent/app/src/main/res/navigation)**.

- After creating my_nav.xml file, add 2 fragment by selecting **"New Destination"** icon on my_nav.xml file. With this button we can create new destination easily.
<img width="416" alt="Screen Shot 2021-08-18 at 16 30 34" src="https://user-images.githubusercontent.com/47380312/129907107-d0271930-b09a-400a-a59f-1b2e101afdbd.png">

- **my_nav.xml**
<?xml version="1.0" encoding="utf-8"?>
<navigation xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/my_nav"
    app:startDestination="@id/firstFragment">

    <fragment
        android:id="@+id/firstFragment"
        android:name="com.hepsiburada.navigationcomponent.FirstFragment"
        android:label="fragment_first"
        tools:layout="@layout/fragment_first" >
        <action
            android:id="@+id/navigateToSecondFragment"
            app:destination="@id/secondFragment"
            app:enterAnim="@anim/nav_default_enter_anim"
            app:exitAnim="@anim/nav_default_exit_anim"
            app:popEnterAnim="@anim/nav_default_pop_enter_anim"
            app:popExitAnim="@anim/nav_default_pop_exit_anim" />
    </fragment>
    <fragment
        android:id="@+id/secondFragment"
        android:name="com.hepsiburada.navigationcomponent.SecondFragment"
        android:label="fragment_second"
        tools:layout="@layout/fragment_second" >
        <action
            android:id="@+id/navigateToFirstFragment"
            app:destination="@id/firstFragment"
            app:enterAnim="@anim/nav_default_enter_anim"
            app:exitAnim="@anim/nav_default_exit_anim"
            app:popEnterAnim="@anim/nav_default_pop_enter_anim"
            app:popExitAnim="@anim/nav_default_pop_exit_anim" />
    </fragment>
</navigation>

👇🏼 As you can see below, **First fragment has home icon.** This means that we will see the First fragment on screen when app is opened. If we want to make Second fragment as home page, we can do it easily with right click on it and select **"Set as Start Destination"** button.

<img width="669" alt="Screen Shot 2021-08-18 at 16 08 43" src="https://user-images.githubusercontent.com/47380312/129907783-7acf5114-0681-4b15-a568-5d56abdbf26d.png">

- **fragment_first.xml**
 ```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="@color/gray"
    app:layout_constraintEnd_toEndOf="parent"
    app:layout_constraintStart_toStartOf="parent"
    app:layout_constraintTop_toTopOf="parent"
    tools:context=".FirstFragment">

    <TextView
        android:id="@+id/tv_number"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="1"
        android:textColor="@color/white"
        android:textSize="100sp"
        android:textStyle="bold"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.5"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />
</androidx.constraintlayout.widget.ConstraintLayout>
 ```
- **fragment_second.xml**

```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="@color/black"
    app:layout_constraintEnd_toEndOf="parent"
    app:layout_constraintStart_toStartOf="parent"
    app:layout_constraintTop_toTopOf="parent"
    tools:context=".SecondFragment">

    <TextView
        android:id="@+id/tv_number2"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="2"
        android:textColor="@color/white"
        android:textSize="100sp"
        android:textStyle="bold"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.5"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />
</androidx.constraintlayout.widget.ConstraintLayout>
 ```
- **FirstFragment.kt**
 ```
 class FirstFragment : Fragment() {

    override fun onCreateView(
        inflater: LayoutInflater, container: ViewGroup?,
        savedInstanceState: Bundle?
    ): View? {
        // Inflate the layout for this fragment
        val view = inflater.inflate(R.layout.fragment_first, container, false)

        view.setOnClickListener {
            Navigation.findNavController(view).navigate(R.id.navigateToSecondFragment)
        }

        return view
    }
}
 ```

- **SecondFragment.kt**
 ```
 class FirstFragment : Fragment() {

    override fun onCreateView(
        inflater: LayoutInflater, container: ViewGroup?,
        savedInstanceState: Bundle?
    ): View? {
        // Inflate the layout for this fragment
        val view = inflater.inflate(R.layout.fragment_second, container, false)

        view.setOnClickListener {
            Navigation.findNavController(view).navigate(R.id.navigateToFirstFragment)
        }

        return view
    }
}
 ```
